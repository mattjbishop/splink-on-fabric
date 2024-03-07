# splink-on-fabric
An experiment to get the [MoJ Splink](https://github.com/moj-analytical-services/splink/) Spark demo(s) running on [Microsoft Fabric](https://learn.microsoft.com/en-us/fabric/).

Notebooks:
* [Spark Deduplicate example](deduplicate_1k_synthetic_on_fabric.ipynb)

## Running Splink on Fabric
The best way to get Splink running is to make use of the new [Environments](https://learn.microsoft.com/en-us/fabric/data-engineering/create-and-use-environment) feature in Fabric. 
> [!NOTE]
> Environments are a preview feature and may change before general release [as of 2024-03-05]

To use Splink in this demo, you need to:
1. Upload the [similarity UDF](https://github.com/moj-analytical-services/splink/blob/master/splink/files/spark_jars/scala-udf-similarity-0.1.1_spark3.x.jar) jar into the Lakehouse that you are using
<img width="490" alt="similarity_jar_file" src="https://github.com/mattjbishop/splink-on-fabric/assets/7355456/b3f4f1a0-e293-4bbb-8a12-82541b44329b">

2. In your environment, add a "spark.jars" Spark Property that points to the jar file. Use an ABFS path to point to the file e.g. `abfss://00000000-0000-0000-0000-000000000000@onelake.dfs.fabric.microsoft.com/00000000-0000-0000-0000-000000000000/Files/scala-udf-similarity-0.1.1_spark3.x.jar`
<img width="1038" alt="spark_jar_property" src="https://github.com/mattjbishop/splink-on-fabric/assets/7355456/d34041d6-7303-42aa-8b06-d6956cfd97e3">

3. In your environment, add Splink as a Public Library from PyPl
<img width="1037" alt="splink_public_library" src="https://github.com/mattjbishop/splink-on-fabric/assets/7355456/fdf237ed-8a36-4da4-b651-87b3faa155fa">
