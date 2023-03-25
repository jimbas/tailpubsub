# Tail a Google Pub/Sub topic

## Pre-build:
```
export GOPATH=${PWD} && export GOROOT=/path/to/your-goroot && export PATH=$PATH:$GOROOT/bin 
go get github.com/cihub/seelog
go get golang.org/x/net/context
go get golang.org/x/oauth2/google
go get google.golang.org/api/pubsub/v1
```

## Build:
```
go build -o bin/tailpubsub tailpubsub.go
```

## Google Service-account
In order to run, it requires the service-account.json file which can be obtained via the GCP console.
* Visit the GCP console then go to the 'API & Services' menu
* On the side menu, click 'Credentials'
* Click the email item in 'Service Accounts' and click the 'KEYS' tab then click 'ADD KEY'
* Download the service-account.json file and copy it to the active directory

## Usage:
```
$ ./tail-pubsub -h
Usage of ./tail-pubsub:
  -batchsize=1: How many messages to get at once
  -project="": Google project-id
  -topic="": PUB/SUB topic name to subscribe to
  -subscription="": PUB/SUB topic subscription name
```

## Run:
```
export GOOGLE_APPLICATION_CREDENTIALS='/path/to/your/service-account.json'
./bin/tailpubsub -batchsize=1 -project=GCP_PROJECT_ID -topic=YOUR_TOPIC -subscription=YOUR_TOPIC_SUB
```

## References

- [Original Source Code](https://github.com/chrusty/tail-pubsub)
