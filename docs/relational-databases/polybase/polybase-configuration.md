---
title: Настройка PolyBase | Документация Майкрософт
ms.custom: ''
ms.date: 02/15/2018
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: polybase
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 848ac4ee465ad0c7461734fbcd7478eaff6af531
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37173547"
---
# <a name="polybase-configuration"></a>Конфигурация PolyBase
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  В этом разделе приведены процедуры для настройки PolyBase.  
  
## <a name="external-data-source-configuration"></a>Конфигурация внешнего источника данных  
 Обеспечьте подключение к внешнему источнику данных с помощью SQL Server. Тип подключения ощутимо влияет на производительность запросов. Например, в рамках 10-гигабитного соединения Ethernet ответ на запрос PolyBase приходит быстрее, чем в рамках 1-гигабитного соединения Ethernet.  
  
 Необходимо настроить SQL Server для подключения к вашей версии Hadoop или хранилищу BLOB-объектов Azure с помощью **sp_configure**. В PolyBase поддерживается два типа распределений: Hortonworks Data Platform (HDP) и Cloudera Distributed Hadoop (CDH).  Полный список поддерживаемых внешних источников данных см. в статье [Конфигурация PolyBase (Transact-SQL)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md).  

Обратите внимание на то, что PolyBase поддерживает зоны шифрования Hadoop начиная с SQL Server 2016 с пакетом обновления 1 (SP1) и накопительным пакетом обновления 7 и SQL Server 2017.

  
### <a name="run-spconfigure"></a>Выполнение процедуры sp_configure  
  
1.  Запустите хранимую процедуру sp_configure 'hadoop connectivity' и задайте соответствующее значение.  Значение см. в статье [Конфигурация подключения к PolyBase (Transact-SQL)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md).  
  
    ```sql  
    -- Values map to various external data sources.  
    -- Example: value 7 stands for Azure blob storage and Hortonworks HDP 2.3 on Linux.  
    sp_configure @configname = 'hadoop connectivity', @configvalue = 7;   
    GO   
  
    RECONFIGURE   
    GO   
    ```  
  
2.  Перезапустите SQL Server с помощью **services.msc**. При перезапуске SQL Server следующие службы также будут перезапущены:  
  
    -   Служба перемещения данных SQL Server PolyBase  
  
    -   Компонент SQL Server PolyBase Engine  
  
## <a name="pushdown-configuration"></a>Конфигурация Pushdown  
 Чтобы повысить производительность запросов, активируйте вычисление pushdown для кластера Hadoop, необходимо будет указать некоторые параметры конфигурации, относящиеся к используемой среде Hadoop SQL Server:  
  
1.  Найдите файл **yarn-site.xml** в каталоге установки SQL Server. Как правило, путь выглядит следующим образом:  
  
    ```  
    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\Polybase\Hadoop\conf  
    ```  
  
2.  Найдите аналогичный файл на компьютере с Hadoop в каталоге конфигурации. Открыв его, найдите и скопируйте значение ключа конфигурации yarn.application.classpath.  
  
3.  На компьютере SQL Server в файле **yarn.site.xml** найдите свойство **yarn.application.classpath** . Вставьте значение, скопированное на компьютере с Hadoop, в качестве значения элемента.  

4. Для всех версий CDH 5.X необходимо добавить параметры конфигурации **mapreduce.application.classpath** либо в конец **файла yarn.site.xml**, либо в **файл mapred-site.xml**. HortonWorks содержит эти настройки в конфигурациях **yarn.application.classpath**.

## <a name="connecting-to-hadoop-cluster-with-hadooprpcprotection-setting"></a>Подключение к кластеру Hadoop с параметром Hadoop.RPC.Protection
Типичный способ защиты взаимодействия в кластере Hadoop — изменение конфигурации hadoop.rpc.protection на Privacy (Конфиденциальность) или Integrity (Целостность). По умолчанию PolyBase предполагает, что задана конфигурация Authenticate (Проверка подлинности). Чтобы переопределить эту настройку по умолчанию, добавьте в файл core-site.xml указанное ниже свойство. Изменение конфигурации позволит осуществлять безопасную передачу данных между узлами Hadoop и использовать SSL-подключение к SQL Server.

```
<!-- RPC Encryption information, PLEASE FILL THESE IN ACCORDING TO HADOOP CLUSTER CONFIG -->
  <property>
    <name>hadoop.rpc.protection</name>
    <value></value>
  </property> 
```




## <a name="example-yarn-sitexml-and-mapred-sitexml-files-for-cdh-5x-cluster"></a>Пример yarn-site.xml mapred-site.xml файлов и CDH 5.X кластера.



Yarn-site.xml yarn.application.classpath и mapreduce.application.classpath конфигурации.
```
<?xml version="1.0" encoding="utf-8"?>
<?xml-stylesheet type="text/xsl" href="configuration.xsl"?>
<!-- Put site-specific property overrides in this file. -->
 <configuration>
  <property>
     <name>yarn.resourcemanager.connect.max-wait.ms</name>
     <value>40000</value>
  </property>
  <property>
     <name>yarn.resourcemanager.connect.retry-interval.ms</name>
     <value>30000</value>
  </property>
<!-- Applications' Configuration-->
  <property>
    <description>CLASSPATH for YARN applications. A comma-separated list of CLASSPATH entries</description>
     <!-- Please set this value to the correct yarn.application.classpath that matches your server side configuration -->
     <!-- For example: $HADOOP_CONF_DIR,$HADOOP_COMMON_HOME/share/hadoop/common/*,$HADOOP_COMMON_HOME/share/hadoop/common/lib/*,$HADOOP_HDFS_HOME/share/hadoop/hdfs/*,$HADOOP_HDFS_HOME/share/hadoop/hdfs/lib/*,$HADOOP_YARN_HOME/share/hadoop/yarn/*,$HADOOP_YARN_HOME/share/hadoop/yarn/lib/* -->
     <name>yarn.application.classpath</name>
     <value>$HADOOP_CLIENT_CONF_DIR,$HADOOP_CONF_DIR,$HADOOP_COMMON_HOME/*,$HADOOP_COMMON_HOME/lib/*,$HADOOP_HDFS_HOME/*,$HADOOP_HDFS_HOME/lib/*,$HADOOP_YARN_HOME/*,$HADOOP_YARN_HOME/lib/,$HADOOP_MAPRED_HOME/*,$HADOOP_MAPRED_HOME/lib/*,$MR2_CLASSPATH*</value>
  </property>

<!-- kerberos security information, PLEASE FILL THESE IN ACCORDING TO HADOOP CLUSTER CONFIG
  <property>
     <name>yarn.resourcemanager.principal</name>
     <value></value>
  </property>
-->
</configuration>

```
Если 2 параметра конфигурации необходимо разбить на mapred-site.xml и yarn-site.xml, то файлы будут выглядеть следующим образом:

**yarn-site.xml**
```
<?xml version="1.0" encoding="utf-8"?>
<?xml-stylesheet type="text/xsl" href="configuration.xsl"?>
<!-- Put site-specific property overrides in this file. -->
 <configuration>
  <property>
     <name>yarn.resourcemanager.connect.max-wait.ms</name>
     <value>40000</value>
  </property>
  <property>
     <name>yarn.resourcemanager.connect.retry-interval.ms</name>
     <value>30000</value>
  </property>
<!-- Applications' Configuration-->
  <property>
    <description>CLASSPATH for YARN applications. A comma-separated list of CLASSPATH entries</description>
     <!-- Please set this value to the correct yarn.application.classpath that matches your server side configuration -->
     <!-- For example: $HADOOP_CONF_DIR,$HADOOP_COMMON_HOME/share/hadoop/common/*,$HADOOP_COMMON_HOME/share/hadoop/common/lib/*,$HADOOP_HDFS_HOME/share/hadoop/hdfs/*,$HADOOP_HDFS_HOME/share/hadoop/hdfs/lib/*,$HADOOP_YARN_HOME/share/hadoop/yarn/*,$HADOOP_YARN_HOME/share/hadoop/yarn/lib/* -->
     <name>yarn.application.classpath</name>
     <value>$HADOOP_CLIENT_CONF_DIR,$HADOOP_CONF_DIR,$HADOOP_COMMON_HOME/*,$HADOOP_COMMON_HOME/lib/*,$HADOOP_HDFS_HOME/*,$HADOOP_HDFS_HOME/lib/*,$HADOOP_YARN_HOME/*,$HADOOP_YARN_HOME/lib/*</value>
  </property>

<!-- kerberos security information, PLEASE FILL THESE IN ACCORDING TO HADOOP CLUSTER CONFIG
  <property>
     <name>yarn.resourcemanager.principal</name>
     <value></value>
  </property>
-->
</configuration>
```

**mapred-site.xml**

Обратите внимание, что было добавлено свойство mapreduce.application.classpath. В CDH 5.X значения конфигурации имеют тот же формат именования, что и в Ambari.

```
<?xml version="1.0"?>
<?xml-stylesheet type="text/xsl" href="configuration.xsl"?>
<!-- Put site-specific property overrides in this file. -->
<configuration xmlns:xi="http://www.w3.org/2001/XInclude">
  <property>
    <name>mapred.min.split.size</name>
      <value>1073741824</value>
  </property>
  <property>
    <name>mapreduce.app-submission.cross-platform</name>
    <value>true</value>
  </property>
<property>
    <name>mapreduce.application.classpath</name>
    <value>$HADOOP_MAPRED_HOME/*,$HADOOP_MAPRED_HOME/lib/*,$MR2_CLASSPATH</value>
  </property>


<!--kerberos security information, PLEASE FILL THESE IN ACCORDING TO HADOOP CLUSTER CONFIG
  <property>
    <name>mapreduce.jobhistory.principal</name>
    <value></value>
  </property>
  <property>
    <name>mapreduce.jobhistory.address</name>
    <value></value>
  </property>
-->
</configuration>
  
```
  
## <a name="kerberos-configuration"></a>Конфигурация Kerberos  
Когда PolyBase выполняет проверку подлинности в защищенном кластере Kerberos, параметр hadoop.rpc.protection должен по умолчанию иметь значение Authenticate. При этом обмен данными между узлами Hadoop остается в незашифрованном виде. Чтобы использовать значение Privacy или Integrity для параметра hadoop.rpc.protection, обновите файл core-site.xml на сервере PolyBase. Дополнительные сведения см. в предыдущем разделе [Подключение к кластеру Hadoop с параметром Hadoop.rpc.protection](#connecting-to-hadoop-cluster-with-hadooprpcprotection-setting).

 Чтобы подключиться к защищенному с помощью Kerberos кластеру Hadoop [с помощью MIT KDC], сделайте следующее.
   
  
1.  Найдите каталог конфигурации Hadoop в каталоге установки SQL Server. Как правило, путь выглядит следующим образом:  
  
    ```  
    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\Polybase\Hadoop\conf  
    ```  
  
2.  Найдите значение конфигурации для ключей конфигурации, перечисленных в таблице, на компьютере с Hadoop. (Найдите файлы в каталоге конфигурации Hadoop на этом же компьютере.)  
  
3.  Скопируйте значения конфигурации в свойство value соответствующих файлов на компьютере с SQL Server.  
  
    |**#**|**Файл конфигурации**|**Ключ конфигурации**|**Действие**|  
    |------------|----------------|---------------------|----------|   
    |1|core-site.xml|polybase.kerberos.kdchost|Укажите имя узла KDC. Например, kerberos.your-realm.com|  
    |2|core-site.xml|polybase.kerberos.realm|Укажите область Kerberos. Например, YOUR-REALM.COM|  
    |3|core-site.xml|hadoop.security.authentication|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Например, KERBEROS<br></br>**Примечание о безопасности:** слово KERBEROS должно быть написано прописными буквами. При использовании строчных букв функция может не включиться.|   
    |4|hdfs-site.xml|dfs.namenode.kerberos.principal|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Например: hdfs/_HOST@YOUR-REALM.COM.|  
    |5|mapred-site.xml|mapreduce.jobhistory.principal|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Например: mapred/_HOST@YOUR-REALM.COM.|  
    |6|mapred-site.xml|mapreduce.jobhistory.address|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Например, 10.193.26.174:10020|  
    |7|yarn-site.xml yarn|yarn.resourcemanager.principal|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Например: yarn/_HOST@YOUR-REALM.COM.|  
  
4.  Создайте объект учетных данных для базы данных, чтобы указать аутентификационные сведения для каждого пользователя Hadoop. См. статью [Объекты T-SQL PolyBase](../../relational-databases/polybase/polybase-t-sql-objects.md).  
  
## <a name="next-steps"></a>Следующие шаги  
 [Объекты PolyBase T-SQL](../../relational-databases/polybase/polybase-t-sql-objects.md)  
  
 [Приступая к работе с PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)  
  
## <a name="see-also"></a>См. также:  
 [Конфигурация PolyBase (Transact-SQL)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md)   
 [Руководство по PolyBase](../../relational-databases/polybase/polybase-guide.md)  
  
  
