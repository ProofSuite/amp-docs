---
description: AMP exchange matching-engine setup documentation
---

# Matching Engine

## Requirements

* **golang** 1.10 or newer
* **mongoDB** version 4.0 or newer
* **rabbitmq** version 3.7.7 or newer
* **dep** latest



## Development Environment Setup

Before running the matching-engine you need to have **mongoDB** and **rabbitMQ** running locally. For a development environment, no specific passwords or parameters are required.

* Start MongoDB

```text
mongod
```

* Start the RabbitMQ server

```text
rabbitmq-server
```

### Installing Dependencies

Install the matching engine dependencies with the **dep** package manager.

```bash
dep ensure
```

Install the go hot reloading utility **fresh:**

```text
go get github.com/pilu/fresh
```

### Matching Engine Configuration

{% hint style="info" %}
You need a deployed version of the AMP smart-contracts. See the **Contracts** section for more information. 
{% endhint %}

Below is a list of environment variables with the description and recommend value for a local development environment setup.



<table>
  <thead>
    <tr>
      <th style="text-align:left">Environment Variable Name</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">AMP_RABBITMQ_URL</td>
      <td style="text-align:left">Recommend Value: <b>localhost</b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">AMP_MONGODB_URL</td>
      <td style="text-align:left">Recommend Value: <b>localhost</b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">AMP_MONGODB_DBNAME</td>
      <td style="text-align:left">
        <p>MongoDB Database name</p>
        <p>Recommended Value: <b>proofdex</b>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">AMP_EXCHANGE_CONTRACT</td>
      <td style="text-align:left">Your AMP exchange contract address. Currently interoperability is not
        supported so you need to deploy your own exchange contract or contact us
        for access to our <b>Rinkeby</b> exchange contract.</td>
    </tr>
    <tr>
      <td style="text-align:left">AMP_ETHEREUM_NODE_HTTP_URL</td>
      <td style="text-align:left">https://rinkeby.infura.io</td>
    </tr>
    <tr>
      <td style="text-align:left">AMP_ETHEREUM_NODE_WS_URL</td>
      <td style="text-align:left">wss://rinkeby.infura.io/ws</td>
    </tr>
    <tr>
      <td style="text-align:left">AMP_ENABLE_TLS</td>
      <td style="text-align:left">Recommended Value: <b>false</b>
      </td>
    </tr>
  </tbody>
</table>You can set these environment variables in the `start-local-rinkeby.sh file.` 

### Start the Matching Engine Server

```text
chmod +x ./start-local-rinkeby.sh
./start-local-rinkeby.sh
```



