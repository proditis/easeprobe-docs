# Native Clients

**Client**. Currently, support the following native client. Support the mTLS. ( refer to: Native Client Probe Configuration )

* **MySQL**. Connect to the MySQL server and run the `SHOW STATUS` SQL.
* **Redis**. Connect to the Redis server and run the `PING` command.
* **Memcache**. Connect to a Memcache server and run the `version` command or check based on key/value checks.
* **MongoDB**. Connect to MongoDB server and just ping server.
* **Kafka**. Connect to Kafka server and list all topics.
* **PostgreSQL**. Connect to PostgreSQL server and run `SELECT 1` SQL.
* **Zookeeper**. Connect to Zookeeper server and run `get /` command.
* **MySQL**. Connect to the MySQL server and run the `SHOW STATUS` SQL.
* **Redis**. Connect to the Redis server and run the `PING` command.
* **Memcache**. Connect to a Memcache server and run the `version` command or check based on key/value checks.
* **MongoDB**. Connect to MongoDB server and just ping server.
* **Kafka**. Connect to Kafka server and list all topics.
* **PostgreSQL**. Connect to PostgreSQL server and run `SELECT 1` SQL.
* **Zookeeper**. Connect to Zookeeper server and run `get /` command.

Most of the clients support the additional validity check of data pulled from the service (such as checking a redis or memcache key for specific values). Check the documentation of the corresponding client for details on how to enable.

### Native Client Probe Configuration

Native Client probe uses the native GO SDK to communicate with the remote endpoints. Additionally to simple connectivity checks, you can also define key and data validity checks for EaseProbe, it will query for the given keys and verify the data stored on each service.

```
# Native Client Probe
client:
  - name: Redis Native Client (local)
    driver: "redis"  # driver is redis
    host: "localhost:6379"  # server and port
    password: "abc123" # password
    data:         # Optional
      key: val    # Check that `key` exists and its value is `val`
    # mTLS - Optional
    ca: /path/to/file.ca
    cert: /path/to/file.crt
    key: /path/to/file.key

  - name: MySQL Native Client (local)
    driver: "mysql"
    host: "localhost:3306"
    username: "root"
    password: "pass"
    data: # Optional, check the specific column value in the table
      #  Usage: "database:table:column:primary_key:value" : "expected_value"
      #         transfer to : "SELECT column FROM database.table WHERE primary_key = value"
      #         the `value` for `primary_key` must be int
      "test:product:name:id:1" : "EaseProbe" # select name from test.product where id = 1
      "test:employee:age:id:2" : 45          # select age from test.employee where id = 2
    # mTLS - Optional
    ca: /path/to/file.ca
    cert: /path/to/file.crt
    key: /path/to/file.key

  - name: MongoDB Native Client (local)
    driver: "mongo"
    host: "localhost:27017"
    username: "admin"
    password: "abc123"
    timeout: 5s
    data: # Optional, find the specific value in the table
      #  Usage: "database:collection" : "{JSON}"
      "test:employee" : '{"name":"Hao Chen"}' # find the employee with name "Hao Chen"
      "test:product" : '{"name":"EaseProbe"}' # find the product with name "EaseProbe"

  - name: Memcache Native Client (local)
    driver: "memcache"
    host: "localhost:11211"
    timeout: 5s
    data:         # Optional
      key: val    # Check that key exists and its value is val
      "namespace:key": val # Namespaced keys enclosed in "

  - name: Kafka Native Client (local)
    driver: "kafka"
    host: "localhost:9093"
    # mTLS - Optional
    ca: /path/to/file.ca
    cert: /path/to/file.crt
    key: /path/to/file.key

  - name: PostgreSQL Native Client (local)
    driver: "postgres"
    host: "localhost:5432"
    username: "postgres"
    password: "pass"
    data: # Optional, check the specific column value in the table
      #  Usage: "database:table:column:primary_key:value" : "expected_value"
      #         transfer to : "SELECT column FROM table WHERE primary_key = value"
      #         the `value` for `primary_key` must be int
      "test:product:name:id:1" : "EaseProbe" # select name from product where id = 1
      "test:employee:age:id:2" : 45          # select age from employee where id = 2
    # mTLS - Optional
    ca: /path/to/file.ca
    cert: /path/to/file.crt
    key: /path/to/file.key

  - name: Zookeeper Native Client (local)
    driver: "zookeeper"
    host: "localhost:2181"
    timeout: 5s
    data: # Optional, check the specific value in the path
      "/path/to/key": "value" # Check that the value of the `/path/to/key` is "value"
    # mTLS - Optional
    ca: /path/to/file.ca
    cert: /path/to/file.crt
    key: /path/to/file.key
```
