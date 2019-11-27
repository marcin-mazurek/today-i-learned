# Load test with Apache Bench

Installing Apache Bench on Debian/Ubuntu:
```
sudo apt-get -y install apache2-utils
```

The following command will make 100 concurrent connections and make 1000 requests in total:
```
ab -n 1000 -c 100 [URL TO LOAD TEST]
```
