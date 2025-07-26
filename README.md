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
:beer: **Please support me**: If the above helped you in any way, then [follow me on Twitter](https://twitter.com/gerdnaschenweng) or send me some coins: 
```
(CRO)    cro1w2kvwrzp23aq54n3amwav4yy4a9ahq2kz2wtmj (Memo: 644996249) or 0xb83c3Fe378F5224fAdD7a0f8a7dD33a6C96C422C (Cronos)
(USDC)   0xb83c3Fe378F5224fAdD7a0f8a7dD33a6C96C422C
(BTC)    3628nqihXvw2RXsKtTR36dN6WvYzaHyr52
(ETH)    0xb83c3Fe378F5224fAdD7a0f8a7dD33a6C96C422C
(BAT)    0xb83c3Fe378F5224fAdD7a0f8a7dD33a6C96C422C
(LTC)    MQxRAfhVU84KDVUqnZ5eV9MGyyaBEcQeDf
(Ripple) rKV8HEL3vLc6q9waTiJcewdRdSFyx67QFb (Tag: 1172047832)
(XLM)    GB67TJFJO3GUA432EJ4JTODHFYSBTM44P4XQCDOFTXJNNPV2UKUJYVBF (Memo ID: 1406
```

Go to [Curve.com to add your Crypto.com card to ApplePay](https://www.curve.com/join#DWPXKG6E) and signup to [Crypto.com for a staking and free Crypto debit card](https://crypto.com/app/ref6ayzqvp).

Use [Binance Exchange](https://www.binance.com/?ref=13896895) to trade #altcoins. Sign up with [Coinbase](https://www.coinbase.com/join/nasche_x) and **instantly get $10 in BTC**. I also accept old-school **[PayPal](https://paypal.me/GerdNaschenweng)**.

If you have no crypto, follow me at least on [Twitter](https://twitter.com/gerdnaschenweng).
