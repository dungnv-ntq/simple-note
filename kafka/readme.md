1. start kafka
docker-compose up -d

2. create topic test
docker exec kafka kafka-topics --bootstrap-server kafka:9092 --create --topic test

3. write message to topic
docker exec --interactive --tty kafka kafka-console-producer --bootstrap-server kafka:9092 --topic test

+ type some message then press ctr-D to return terminal

4. read message from topic
docker exec --interactive --tty kafka kafka-console-consumer --bootstrap-server kafka:9092 --topic test --from-beginning
