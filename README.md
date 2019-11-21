Please install docker and docker composer on your instance before run the docker-compose.yml

To install docker on Linux

sudo yum update -y
sudo yum install docker

sudo usermod -aG docker $USER
(grant permission to current user , then login again.)

sudo service docker start
(Verify Docker)
sudo docker run hello-world


and docker composer on AWS linux (minimum small instance is required) 



Pull both docker images to server

sudo docker pull docker.elastic.co/elasticsearch/elasticsearch:6.3.2
sudo docker pull docker.elastic.co/kibana/kibana:6.3.2


run single node elastic with docker 
docker run -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:6.3.2


sudo vi /etc/sysctl.conf
add below to the conf
vm.max_map_count=262144
sudo sysctl -p


Using docker-compose:


sudo curl -L "https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
(Verify Docker compose)
docker-compose --version


After installation, put docker-compose.yml and execute below in same directory

docker-compose up -d 




Elasticsearch is avaiable at http://localhost:9200/
Kibana UI is up at http://localhost:5601/

