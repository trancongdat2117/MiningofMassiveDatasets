# MiningofMassiveDatasets
This is all materials of MMD subject at Ton Duc Thang University.

References: 
- [SparkByEX](https://sparkbyexamples.com/)
- [SparkDocs](https://spark.apache.org/docs/latest/api/python/index.html)
# 1. Tìm hiểu về Spark ?
## 1.1 Giới thiệu: 
- Là một framework để xử lý dữ liệu
- Cung cấp các APIs cho Scala, Java, Python.
- Được xây dựng bằng ngôn ngữ Scala.
- Tốc độ nhanh hơn Mapreduce từ 10 ~ 100 lần

<img src="https://static.javatpoint.com/tutorial/pyspark/images/pyspark-rdd2.png">
## 1.2 Đặc trưng:
- Fast processing: xử lí nhanh
- In-memory computation: tính toán trên RAM
- Fault Tolerance: khả năng chống chịu lỗi
- Near Real time stream processing: xử lí dữ liệu gần như thời gian thực
- Lazy evaluation.
- Support Multiple Languages.
- Cost Efficent.
## 1.3 Spark components
- Spark core: cung cấp nền tảng cho các sprak Applications
- Spark SQL: xử lí dữ liệu semi-structured/structured data bằng SQL/HQL
- Spark Streaming: xử lí dữ liệu streaming
- Spark ML cung cấp công cụ cho việc phân tích dữ liệu bằng các model ML
- Spark Graph X: xử lí dữ liệu đồ thị
- Spark R: dùng cho việc phân tích dữ liệu trên R

# 2. Tìm hiểu về Mapreduce ?
## 2.1 Giới thiệu:
- là một mô hình lập trình, thực hiện quá tình xử lý tập dữ liệu lớn song song và phân tán trên 1 cụm máy tính
- gồm 2 phần: map và reduce
  + Hàm Map : Các xử lý một cặp (key, value) để sinh ra một cặp (keyI, valueI) - key và value trung gian. Dữ liệu này input vào hàm Reduce
  + Hàm Reduce : Tiếp nhận các (keyI, valueI) và trộn các cặp (keyI, valueI) trung gian , lấy ra các valueI có cùng keyI
  + Ngoài ra, Hàm Group by key: Sort and shuffle - Hệ thống sắp xếp tất cả các cặp khóa-giá trị theo khóa và xuất ra các cặp khóa(danh sách các giá trị)
  <img src="https://images.viblo.asia/371995ad-cac3-4060-b7c3-c93c596a569d.jpg">
## 2.2 Đặc trưng:
- MapReduce có khả năng xử lý dễ dàng mọi bài toán có lượng dữ liệu lớn nhờ khả năng tác vụ phân tích và tính toán phức tạp
- Mapreduce có khả năng chạy song song trên các máy có sự phân tán  khác nhau. Với khả năng hoạt động độc lập kết hợp  phân tán, xử lý các lỗi kỹ thuật để mang lại nhiều hiệu quả cho toàn hệ thống. 
- MapRedue có khả năng thực hiện trên nhiều nguồn ngôn ngữ lập trình khác nhau 
## 2.3 Mapreduce Jobs:
- Thống kê số từ khóa xuất hiện trong các documents,số documents có chứa từ khóa.
- Thống kê số câu match với pattern trong các documents.
- Thống kê số URLs xuất hiện trong các web pages.
- Thống kê số lượt truy cập các URLs, ...

Link code Ex: [CountingWord](https://colab.research.google.com/drive/15JAJkXYaqvzOjLugInsMIdsR8NNQX6fU?usp=sharing)
