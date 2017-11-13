# Learning Cassandra in a Docker

Trying to figure out how to get Cassandra inside a docker to talk to my other nodes. 

    docker run --name cassandra -i \
        -v /media/mcamp/HDD/Docker/CampgroundContainer1:/var/lib/cassandra \
        -e CASSANDRA_SEEDS="192.168.0.114, 192.168.0.101, 192.168.0.106" \
        -e CASSANDRA_CLUSTER_NAME=CampCluster \
        -e CASSANDRA_DC=campground-wireless \
        -e CASSANDRA_RACK=Docker1 \
        -e CASSANDRA_ENDPOINT_SNITCH=GossipingPropertyFileSnitch \
        -e CASSANDRA_START_RPC=true \
        -e CASSANDRA_LISTEN_ADDRESS=172.17.0.2 \
        -p 7000:7000 \
         cassandra:latest

sftp://mcamp@192.168.0.114/media/mcamp/HDD/Docker/Cassandra1