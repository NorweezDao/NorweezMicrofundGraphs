<h1 align="center">Norweez Microfund Graphs</h1>



### How to install Ceramic Cli and Launch the Daemon


Recommend use nvm

Node.js v14, and Npm v6.


In my case my the used env was MacOs Intel Because on Docker and arm64 have some strange issues
node -v v16.15.1
npm -v 8.19.2

npm install -g node-pre-gyp


npm install --global @ceramicnetwork/cli @glazed/cli


npm install -g @composedb/cli@^0.2.0

to run a local ceramic daemon please use

``` 
CERAMIC_ENABLE_EXPERIMENTAL_COMPOSE_DB=true ceramic daemon
```


CERAMIC_ENABLE_EXPERIMENTAL_COMPOSE_DB=true ceramic daemon --network testnet-clay

Also you can use if you doenst want to use a local node :

ceramic daemon --network testnet-clay
ceramic daemon --network=testnet-clay

Keep in mind compose conposite use Graph Scalar Definition Language

**GraphQL's Schema Definition Language,**

Some common errors can easily checking the env using 

cd $HOME/.ceramic/
vim daemon.config.json  

You can also ask for help in [Ceramic](https://forum.ceramic.network/)


If you want to create a composite you need to 

* Create a private key :
```
composedb did:generate-private-key
```

* Create Composite

```
composedb composite:create campaigns-schema.graphql --output=campaigns.json --did-private-key='<YOUR_KEY>' --ceramic-url=http://localhost:7007
```

* Deploy a Composite 
```
composedb composite:deploy campaigns.json --ceramic-url=http://localhost:7007
```

* Check the composite 
```
composedb composite:from-model campaigns.json 
```

* Import model form composite 
```
composedb composite:from-model <id> --ceramic-url=http://localhost:7007 --output=my-first-composite.json

```
to make sure your composite is deployed try to import the model using the id into the .json

Lets Build 

# Feedback to ceramic team 

## Composedb is awesome but if your are a newbie using ceramic there is so many dead ends in redundant errors from the cli 
