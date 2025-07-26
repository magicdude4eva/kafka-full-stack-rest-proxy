# Full-stack Docker compose with Kafka, Zookeeper, Schema-registry and UI's
Local full-stack docker-compose where you have Zookeeper, Kafka, Schema-registry (and UI) and Topics (UI). This solves the networking hurdles that comes with Docker/docker-compose and should work across all platforms

## Setup
Create the following directories:
```mkdir -p zookeeper/data zookeeper/datalog kafka/data```

## Run it
Via ```export DOCKER_HOST_IP=127.0.0.1; docker-compose up```

## Endpoints:
* Zookeeper: $DOCKER_HOST_IP:2181
* Kafka: $DOCKER_HOST_IP:9092
* Kafka Rest Proxy: $DOCKER_HOST_IP:8082

## UI's:
The following UI's are part of this:
* Schema registry UI: http://localhost:8001/
* Topics UI: http://localhost:8000/
* Zoonavigator: http://localhost:8004/ (connect via: zookeeper:2181)

## Example commands
Install OS X Kafka client and jq:
```brew install kafka jq```

### View subjects
$ curl --silent -X GET http://localhost:8081/subjects/ | jq .

### View subject
$ curl --silent -X GET http://localhost:8081/subjects/####/versions/latest | jq .

### View via schema-id
$ curl --silent -X GET http://localhost:8081/schemas/ids/1 | jq .

### Deletes all schema versions registered under the subject "Kafka-value"
$ curl -X DELETE http://localhost:8081/subjects/Kafka-value

### Deletes version 1 of the schema registered under subject "Kafka-value"
$ curl -X DELETE http://localhost:8081/subjects/Kafka-value/versions/1

### Deletes the most recently registered schema under subject "Kafka-value"
$ curl -X DELETE http://localhost:8081/subjects/Kafka-value/versions/latest

# Kafka - Create a topic
$ kafka-topics --zookeeper localhost:2181 --create --topic example-topic --partitions 1 --replication-factor 1
$ kafka-topics --zookeeper localhost:2181 --list

### Kafka - Create a consumer
$ kafka-console-consumer --topic example-topic --from-beginning --bootstrap-server localhost:9092

### Kafka - Produce message
$ kafka-console-producer --topic example-topic --broker-list localhost:9092
```
> {"event":"EXAMPLE", "data":{"id":"123", "name":"Piotr"}, "metadata":{"version":"001"}, "timestamp":"2017-11-05T00:00:00Z" }
```


## Donations are always welcome

[paypal]: https://paypal.me/GerdNaschenweng

🍻 **Support my work**  
All my software is free and built in my personal time. If it helps you or your business, please consider a small donation via [PayPal][paypal] — it keeps the coffee ☕ and ideas flowing!

💸 **Crypto Donations**  
You can also send crypto to one of the addresses below:

```
(CRO)   0xb83c3Fe378F5224fAdD7a0f8a7dD33a6C96C422C (Cronos)  
(USDC)  0xb83c3Fe378F5224fAdD7a0f8a7dD33a6C96C422C (ERC20)  
(ETH)   0xfc316ba7d8dc325250f1adfafafc320ad75d87c0  
(BNB)   0xfc316ba7d8dc325250f1adfafafc320ad75d87c0
(BTC)   bc1q24fuw84l6whm20umlr56nvqjn908sec8pavk3z  
Crypto.com PayString: magicdude$paystring.crypto.com
```

🧾 **Recommended Platforms**  
- 👉 [Curve.com](https://www.curve.com/join#DWPXKG6E): Add your Crypto.com card to Apple Pay  
- 🔐 [Crypto.com](https://crypto.com/app/ref6ayzqvp): Stake and get your free Crypto Visa card  
- 📈 [Binance](https://accounts.binance.com/register?ref=13896895): Trade altcoins easily