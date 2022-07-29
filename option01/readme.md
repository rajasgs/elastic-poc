


```

docker network create elastic

docker run --name es01 --net elastic -p 9200:9200 -p 9300:9300 -it docker.elastic.co/elasticsearch/elasticsearch:8.3.2

docker cp es01:/usr/share/elasticsearch/config/certs/http_ca.crt .
```


Verify
```
curl --cacert http_ca.crt -u elastic:39a6sW-v_rX+isCACuKc https://localhost:9200



{
  "name" : "7382ea15cd43",
  "cluster_name" : "docker-cluster",
  "cluster_uuid" : "CpPJaiaCR22d2bQP09xPLA",
  "version" : {
    "number" : "8.3.2",
    "build_type" : "docker",
    "build_hash" : "8b0b1f23fbebecc3c88e4464319dea8989f374fd",
    "build_date" : "2022-07-06T15:15:15.901688194Z",
    "build_snapshot" : false,
    "lucene_version" : "9.2.0",
    "minimum_wire_compatibility_version" : "7.17.0",
    "minimum_index_compatibility_version" : "7.0.0"
  },
  "tagline" : "You Know, for Search"
}
```


Sample creds
```
-> Elasticsearch security features have been automatically configured!
-> Authentication is enabled and cluster connections are encrypted.

->  Password for the elastic user (reset with `bin/elasticsearch-reset-password -u elastic`):
  39a6sW-v_rX+isCACuKc

->  HTTP CA certificate SHA-256 fingerprint:
  6f0a81c7216533b943b6d0cf2cb6472059e01309add68dedd1670877a90a49ba

->  Configure Kibana to use this cluster:
* Run Kibana and click the configuration link in the terminal when Kibana starts.
* Copy the following enrollment token and paste it into Kibana in your browser (valid for the next 30 minutes):
  eyJ2ZXIiOiI4LjMuMiIsImFkciI6WyIxNzIuMjguMC4yOjkyMDAiXSwiZmdyIjoiNmYwYTgxYzcyMTY1MzNiOTQzYjZkMGNmMmNiNjQ3MjA1OWUwMTMwOWFkZDY4ZGVkZDE2NzA4NzdhOTBhNDliYSIsImtleSI6ImJZZ3hTSUlCbU5UVkEzeTlMLUowOkxlN2lIYmVUU2lLU29sQmlHRlRrSXcifQ==

-> Configure other nodes to join this cluster:
* Copy the following enrollment token and start new Elasticsearch nodes with `bin/elasticsearch --enrollment-token <token>` (valid for the next 30 minutes):
  eyJ2ZXIiOiI4LjMuMiIsImFkciI6WyIxNzIuMjguMC4yOjkyMDAiXSwiZmdyIjoiNmYwYTgxYzcyMTY1MzNiOTQzYjZkMGNmMmNiNjQ3MjA1OWUwMTMwOWFkZDY4ZGVkZDE2NzA4NzdhOTBhNDliYSIsImtleSI6ImI0Z3hTSUlCbU5UVkEzeTlMLUo2OmRMYThpcl9iUTl5LTBINDE0amEydncifQ==

  If you're running in Docker, copy the enrollment token and run:
  `docker run -e "ENROLLMENT_TOKEN=<token>" docker.elastic.co/elasticsearch/elasticsearch:8.3.2`
```