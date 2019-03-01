# kafka 

```docker-compose-single-brocker``` 는 zookeeper, kafka 두 가지 서비스를 모두 설정한 파일이다.

## INSTALLATION


## 1. Install kafka server With docker 

```
$ git clone https://github.com/wurstmeister/kafka-docker

$ cd kafka-docker

$ docker-compose -f docker-compose-single-broker.yml up

```


## 2. Download kafka archive

kafka producer, consumer 를 만들어보기 위한 kafka archive를 다운로드 받고, 압축을 해제한다.

```
$ ./download.sh

```

## 3. Make kafka topic

testone 이라는 topic 을 생성한다.


```
$ bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic testone

```

## 4. Producer(생성자) 시작

만들어진 토픽인 testone에서 데이터의 Producer(생성자)를 시작한다. 

```
$ bin/kafka-console-producer.sh --broker-list localhost:9092 --topic testone

```


## 5. Consumer(소비자) 시작

만들어진 토픽인 testone에서 데이터의 Consumer(소비자)를 * 새로운 터미널에서 * 시작한다. 

```
$ bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic testone --from-beginning

```


생성자 터미널 콘솔에서 text 를 입력하면, 소비자 콘솔으로 바로 전달되는것을 알 수 있다. 
