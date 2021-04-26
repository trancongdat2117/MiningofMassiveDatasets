# MiningofMassiveDatasets
This is all materials of MMD subject at Ton Duc Thang University.

References: 
- [SparkByEX](https://sparkbyexamples.com/)
- [SparkDocs](https://spark.apache.org/docs/latest/api/python/index.html)
- [SparkApache](https://spark.apache.org/)
- [Tutorialspoint](https://www.tutorialspoint.com/apache_spark/apache_spark_rdd.htm)
- [github](https://github.com/spark-examples/pyspark-examples/)
- [towardsdatascience](https://towardsdatascience.com/machine-learning-with-pyspark-and-mllib-solving-a-binary-classification-problem-96396065d2aa)
# 1. Tìm hiểu về Spark ?
## 1.1 Giới thiệu: 
- Là một framework để xử lý dữ liệu
- Cung cấp các APIs cho Scala, Java, Python.
- Được xây dựng bằng ngôn ngữ Scala.
- Tốc độ nhanh hơn Mapreduce từ 10 ~ 100 lần
<p align="center">
<img src="https://static.javatpoint.com/tutorial/pyspark/images/pyspark-rdd2.png" width="460" height="300">
 </p>
 
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
  <p align="center">
  <img src="https://images.viblo.asia/371995ad-cac3-4060-b7c3-c93c596a569d.jpg" width="460" height="300">
  </p>
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


# 3. Tìm hiểu về Spark (tiếp theo...):
## 3.1 Spark properties (tính chất của Spark)
- Spark cung cấp 3 thành phần để cấu hình hệ thống:
  + Spark properties: control hầu hết các thông số (paramenters) bằng SparkConf Object
or Java system properties
  + Environment variables: được sử dụng để set-up cho từng máy ví dụ như địa chỉ IP,
hoặc thông qua lệnh conf/spark-env.sh
  + Logging: có thể cấu hình thông qua lệnh - log4j.properties
- Với Spark properties ta có thể set một cách trực tiếp trên SparkConf được passed qua
SparkContext. Với SparkConf cho phép bạn cấu hình một vài thuộc tính phổ biến (URL ,
application name), các cặp khóa thông qua phương thức set():


`val conf = new SparkConf()`

`.setMaster("local[2]")`

`.setAppName("CountingSheep")`

`val sc = new SparkContext(conf)`
- Dynamically Loading Spark Properties : trong một vài trường hợp đặc biệt muốn tránh hard-coding trong SparkConf. Ví dụ bạn muốn chạy ứng dụng với các bản khác nhau hoặc khác memory thì bạn chỉ cần tạo 1 conf rỗng. 

`val sc = new SparkContext(new SparkConf())`

- Viewving Spark Properties : là một nơi để kiểm tra đảm bảo rằng các thuộc tính của bạn đã được set chính xác, chỉ các giá trị chỉ định thông qua spark-defaults.conf, SparkConf hoặc commanđ lne mới xuất hiện. Đối với Web, thì các thuộc tính Spark được hiển thị trong tag Enviroment.
- Application Properties:
  + Spark.app.name: tên của ứng dụng sẽ xuất hiện trên UI và trong log data.
  + Spark.driver.cores: chỉ có trong cluster mode, là số lượng core được dùng trong quá trình xử lí driver
  + Spark.driver.memory: số lượng memory được dùng trong quá trình xử lí.
  + Spark.executor.memory: dung lượng memory được dùng trong quá trình xử lí
## 3.2 Spark RDD (Resilient Distributed Datasets):
- Là một cấu trúc dữ liệu cơ bản của Spark, là một tập hợp các đối tượng được phân bố một cách cố định. Mỗi tập dữ liệu trong RDD có thể chứa bất kỳ kiểu đối tượng nào của Scala, Python, Java or user-defined classes.
- Lặp đi lặp lại trên Mapreduce : Việc sử dụng lại các kết quả nhiều lần tính toán trong các giai đoạn tính toán đã phát sinh chi phí đáng kể cho việc sao chép dữ liệu Disk I/O, và làm chậm hệ thống.
<p align="center"> <img src="https://www.tutorialspoint.com/apache_spark/images/iterative_operations_on_mapreduce.jpg" > </p>
- Hoạt động lặp trên Spark RDD: Việc lặp trên RDD sẽ lưu kết quả trung gian trong bộ nhớ phân tán thay vì IO Disk do vậy hệ thống sẽ nhanh hơn hẳn. Khi RAM hết bộ nhớ thì Data sẽ được lưu trên Disk
<p align="center"> <img src="https://www.tutorialspoint.com/apache_spark/images/iterative_operations_on_spark_rdd.jpg" > </p>
- Hoạt động tương tác trên Spark RDD: Các truy vấn khác nhau được chạy trên cùng 1 tập dữ liệu, dữ liệu được lưu trên memory nên có thời gian thực thi tốt hơn. 
<p align="center"> <img src="https://www.tutorialspoint.com/apache_spark/images/interactive_operations_on_spark_rdd.jpg" > </p>
- Parallelized Collections : được tạo bằng paralleelize method của SparkContext trên 1 collection. Các thành phần trong collection có thể so chép để tạo thành một tập dư liệu phân tán và có thể hoạt động song song . Example :

`data = [1, 2, 3, 4, 5]`

`distData = sc.parallelize(data)`

- External Datasets : PySpark cps thể tạo bộ dữ liệu phân tán bất kỳ từ các nguồn mà Hadoop hỗ trợ. Các RDD của tệp văn bản có thể được tạo bằng cách sử dụng phương thức textFile của SparkContext. Example: 
`distFile = sc.textFile("data.txt")`
- Làm việc với Key-Value Pairs: 

`lines = sc.textFile("data.txt")`

`pairs = lines.map(lambda s: (s, 1))`

`counts = pairs.reduceByKey(lambda a, b: a + b)`
## 3.3 Spark DataFrames:
- Là một tập dữ liệu đươc tổ chức thành cột, về cơ bản thì nó khá giống với cơ sở dữ liệu quan hệ mà chúng ta từng được học nhưng có điểm được tối ưu và phong phú hơn.DataFrames
được xây dựng từ nhiều nguồn như structured data files, tables in Hive, external databases. API DataFrames được tích hợp sẳn trong Scala, Java, Python và R.
- Tạo DataFrames:
`df = spark.read.json("examples/src/main/resources/people.json")` `df.show()`
- Thao tác với dữ liệu không kiểu:

`df.printSchema()` : Print the schema in a tree format

`df.select("name").show()` : Select only the "name" column

`df.select(df['name'], df['age'] + 1).show()` : Select everybody, but increment the age by 1

`df.filter(df['age'] > 21).show()` : Select people older than 21

`df.groupBy("age").count().show()`: Count people by age

# 4. Machine leaning models on PySpark:
## 4.1 Kmean
- K-means là một thuật toán phân cụm đơn giản thuộc loại học không giám sát(tức là dữ liệu không có nhãn) và được sử dụng để giải quyết bài toán phân cụm. 
- Ý tưởng của thuật toán phân cụm k-means là phân chia 1 bộ dữ liệu thành các cụm khác nhau. Trong đó số lượng cụm được cho trước là k. Công việc phân cụm được xác lập dựa trên nguyên lý: Các điểm dữ liệu trong cùng 1 cụm thì phải có cùng 1 số tính chất nhất định. Tức là giữa các điểm trong cùng 1 cụm phải có sự liên quan lẫn nhau. Đối với máy tính thì các điểm trong 1 cụm đó sẽ là các điểm dữ liệu gần nhau
- input: Cho n điểm. Mỗi điểm có dạng (x, y), k: số nhóm. k <= n
- output: Danh sách k nhóm và các điểm của mỗi nhóm

[Code](https://drive.google.com/file/d/1e92M1d_bLhxW20QotcVhg1IFPka8ssop/view?usp=sharing)
## 4.2 Linear Regression
- "Hồi quy tuyến tính" là một phương pháp thống kê để hồi quy dữ liệu với biến phụ thuộc có giá trị liên tục trong khi các biến độc lập có thể có một trong hai giá trị liên tục hoặc là giá trị phân loại. Nói cách khác "Hồi quy tuyến tính" là một phương pháp để dự đoán biến phụ thuộc (Y) dựa trên giá trị của biến độc lập (X). Nó có thể được sử dụng cho các trường hợp chúng ta muốn dự đoán một số lượng liên tục. Ví dụ, dự đoán giao thông ở một cửa hàng bán lẻ, dự đoán thời gian người dùng dừng lại một trang nào đó hoặc số trang đã truy cập vào một website nào đó v.v..

[Code](https://drive.google.com/file/d/1bYMaV3Hl7NkgHQKzha7sUvolKB5oJNiS/view?usp=sharing)
## 4.3 Random_Forests
- Random Forests là thuật toán học có giám sát (supervised learning). Nó có thể được sử dụng cho cả phân lớp và hồi quy. Nó cũng là thuật toán linh hoạt và dễ sử dụng nhất. Một khu rừng bao gồm cây cối. Người ta nói rằng càng có nhiều cây thì rừng càng mạnh. 
- Random forests tạo ra cây quyết định trên các mẫu dữ liệu được chọn ngẫu nhiên, được dự đoán từ mỗi cây và chọn giải pháp tốt nhất bằng cách bỏ phiếu. Nó cũng cung cấp một chỉ báo khá tốt về tầm quan trọng của tính năng. Random forests có nhiều ứng dụng, chẳng hạn như công cụ đề xuất, phân loại hình ảnh và lựa chọn tính năng.
- Nó có thể được sử dụng để phân loại các ứng viên cho vay trung thành, xác định hoạt động gian lận và dự đoán các bệnh. Nó nằm ở cơ sở của thuật toán Boruta, chọn các tính năng quan trọng trong tập dữ liệu
- Cách hoạt động:
+ Chọn các mẫu ngẫu nhiên từ tập dữ liệu đã cho.
+ Thiết lập cây quyết định cho từng mẫu và nhận kết quả dự đoán từ mỗi quyết định cây.
+ Hãy bỏ phiếu cho mỗi kết quả dự đoán.
+ Chọn kết quả được dự đoán nhiều nhất là dự đoán cuối cùng.

[Code](https://drive.google.com/file/d/1lAGjz3GCENhQs8WQDAUAYEXHt7Cn95dY/view?usp=sharing)

# 5. PySpark DataFrame:
## 5.1 Create DataFrame:
- Bạn có thể dùng toDF() hoặc createDataFrame(): cả hai hàm này đều lấy các signatures khác nhau để tạo DataFrame từ RDD, danh sách và DataFrame hiện có.
- Bạn cũng có thể tạo PySpark DataFrame từ các nguồn dữ liệu như TXT, CSV, JSON, ORV, Avro, Parquet, định dạng XML bằng cách đọc từ HDFS, S3...
- Ngoài ra, PySpark DataFrame cũng có thể được tạo bằng cách đọc dữ liệu từ Cơ sở dữ liệu RDBMS và Cơ sở dữ liệu NoSQL.

`Ví dụ`:
- Tạo 1 Spark RDD:
`spark = SparkSession.builder.appName('SparkByExamples.com').getOrCreate()`

`rdd = spark.sparkContext.parallelize(data)`

- Dùng toDF():
`dfFromRDD1 = rdd.toDF()`
`dfFromRDD1.printSchema()`

- Ví dụ với file TXT:
`df2 = spark.read.text("/src/resources/file.txt")`

## 5.2 Convert PySpark RDD to DataFrame:
- Trong PySpark, hàm toDF () của RDD được sử dụng để chuyển RDD thành DataFrame. Chúng ta sẽ cần chuyển đổi RDD sang DataFrame vì DataFrame cung cấp nhiều lợi thế hơn RDD. 
Ví dụ: DataFrame là một tập hợp dữ liệu phân tán được tổ chức thành các cột được đặt tên tương tự như bảng Cơ sở dữ liệu và cung cấp các cải tiến về hiệu suất và tối ưu hóa

### Ví dụ:
#### Tạo Spark RDD
`from pyspark.sql import SparkSession`
`spark = SparkSession.builder.appName('SparkByExamples.com').getOrCreate()`
`dept = [("Finance",10),("Marketing",20),("Sales",30),("IT",40)]`
`rdd = spark.sparkContext.parallelize(dept`
#### Convert PySpark RDD to DataFrame
- Dùng rdd.toDF()
`df = rdd.toDF()`
`df.printSchema()`
`df.show(truncate=False`

- Spark Session cung cấp hàm createDataFrame() 
`deptDF = spark.createDataFrame(rdd, schema = deptColumns)`
`deptDF.printSchema()`
`deptDF.show(truncate=False)`

Link code Ex: [Code ví dụ minh họa](https://colab.research.google.com/drive/1l-mjC5V9Zr_8VH-N5LdNU9tRJ1nd9g2-?usp=sharing)
#### Convert PySpark DataFrame to Pandas
- PySpark DataFrame có thể được chuyển đổi thành Python Pandas DataFrame bằng cách sử dụng hàm toPandas()
+ Chuẩn bị DataFrame 
+ Convert PySpark Dataframe to Pandas DataFrame

Link code ex: [Ví dụ minh họa](https://colab.research.google.com/drive/1SEtpj5IMui9KAZwfQJOMPPb_fMkaT2-8?usp=sharing)

Ngoài ra còn rất nhiều methods để có thể tương tác DataFame, bạn có thể tham khảo [tại đây](https://github.com/spark-examples/pyspark-examples/blob/master/README.md)
