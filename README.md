minikube start --nodes 4

kubectl create configmap scylla-config --from-file=scylla.yaml

kubectl apply -f ScyllaDB.yaml

kubectl logs -f scylla-0

kubectl exec -ti scylla-0 -- nodetool status

kubectl exec -ti scylla-0 -- bash

kubectl exec -ti scylla-0 -- cqlsh

CREATE KEYSPACE my_keyspace WITH replication = {
  'class': 'SimpleStrategy',
  'replication_factor': 3
};

USE my_keyspace;

CREATE TABLE users (id UUID PRIMARY KEY, name TEXT, email TEXT);

INSERT INTO users (id, name, email) VALUES (uuid(), 'John Doe', 'john@example.com');

SELECT * FROM users;

exit

