# **docker-impala**
___

### Description
___

This image runs [*Cloudera Impala*](https://www.cloudera.com/products/open-source/apache-hadoop/impala.html) distribution on HDFS.

You can pull it with:

    docker pull parrotstream/impala


You can also find other images based on different Apache Impala releases, using a different tag in the following form:

    docker pull parrotstream/impala:[impala-release]-[cdh-release]


Stop with Docker Compose:

    docker-compose -p parrot

Setting the project name to *parrot* with the **-p** option is useful to share the network created with the containers coming from other Parrot docker-compose.yml configurations.

Once started you'll be able to access to the following UIs:

| **Impala Web UIs**           |**URL**                    |
|:----------------------------|:--------------------------|
| *Impala State Store Server* | http://localhost:25010    |
| *Impala Catalog Server*     | http://localhost:25020    |
| *Impala Server Daemon*      | http://localhost:25000    |

### Available tags:

- Apache Impala 3.0.0-cdh6.0.0 ([latest](https://github.com/parrot-stream/docker-impala/blob/latest/Dockerfile), [3.0.0-cdh6.0.0](https://github.com/parrot-stream/docker-impala/blob/3.0.0-cdh6.0.0/Dockerfile))
- Apache Impala 2.8.0-cdh5.15.1 ([2.12.0-cdh5.15.1](https://github.com/parrot-stream/docker-impala/blob/2.12.0-cdh5.15.1/Dockerfile))
- Apache Impala 2.8.0-cdh5.11.1 ([2.8.0-cdh5.11.1](https://github.com/parrot-stream/docker-impala/blob/2.8.0-cdh5.11.1/Dockerfile))





## 启动AND使用


1. 启动方式
```shell
docker-compose up 
```
2. 观察日志, 看Hadoop是否启动

   ![，image-20200801134310044](./imgs/image-20200801134310044.png)

   访问浏览器看服务是否正常启动

   ![image-20200801134536185](./imgs/image-20200801134536185.png)

3. 脚本启动后，通过命令查看五个服务都是UP状态的

   ![image-20200801135029346](./imgs/image-20200801135029346.png)

   但是我们通过命令测试的发现是impala启动会异常

   ![image-20200801135205540](./imgs/image-20200801135205540.png)

   **分析之后发现是impala没有启动，执行手动启动命令**

   ```
   docker-compose exec impala /bin/bash /start-impala.sh
   ```

   

   ![image-20200801135453585](./imgs/image-20200801135453585.png)

​      ![image-20200801140118390](./imgs/image-20200801140118390.png)

​      上图看出启动和测试是成功的


4. impala使用

   ```shell
   docker-compose exec impala impala-shell
   ```

   ![image-20200801140403881](./imgs/image-20200801140403881.png)

5. 
