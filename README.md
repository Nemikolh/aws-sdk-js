# AWS SDK for Node.js [![Build Status](https://travis-ci.org/aws/aws-sdk-js.png?branch=master)](https://travis-ci.org/aws/aws-sdk-js)

The official JavaScript implementation of the AWS SDK for Node.js.

## Installing

The preferred way to install the AWS SDK for Node.js is to use the
[npm](http://npmjs.org) package manager for Node.js. Simply type the following
into a terminal window:

```sh
npm install aws-sdk
```

**Please Note**: Installing the `aws-sdk` npm package on Windows may display errors while trying to install the optional dependency for `libxmljs`.  This error can be **safely ignored**.

## Usage

After you've installed the SDK, you can require the AWS package in your node
application using `require`:

```js
var AWS = require('aws-sdk');
```

Here is a quick example that makes some requests against Amazon S3 with the SDK:

```js
// Load the AWS SDK for Node.js
var AWS = require('aws-sdk');

/**
 * Don't hard-code your credentials!
 * Load them from disk or your environment instead.
 */
// AWS.config.update({accessKeyId: 'AKID', secretAccessKey: 'SECRET'});

// Instead, do this:
AWS.config.loadFromPath('./path/to/credentials.json');

// Set your region for future requests.
AWS.config.update({region: 'us-east-1'});

// Create a bucket and put something in it.
var s3 = new AWS.S3();
s3.client.createBucket({Bucket: 'myBucket'}, function() {
  var data = {Bucket: 'myBucket', Key: 'myKey', Body: 'Hello!'};
  s3.client.putObject(data, function(err, data) {
    if (err) {
      console.log("Error uploading data: ", err);
    } else {
      console.log("Successfully uploaded data to myBucket/myKey");
    }
  });
});
```

## Getting Started Guide

You can find a getting started guide at:

http://docs.amazonwebservices.com/nodejs/latest/dg/

## Supported Services

The SDK currently supports the following services:

<table width="100%">
  <thead>
    <th>Service Name</th>
    <th>Class Name</th>
  </thead>
  <tbody>
    <tr><td>Auto Scaling</td><td>AWS.AutoScaling</td></tr>
    <tr><td>Amazon CloudWatch</td><td>AWS.CloudWatch</td></tr>
    <tr><td>Amazon DynamoDB</td><td>AWS.DynamoDB</td></tr>
    <tr><td>Amazon EC2</td><td>AWS.EC2</td></tr>
    <tr><td>Amazon Elastic Transcoder</td><td>AWS.ElasticTranscoder</td></tr>
    <tr><td>Elastic Load Balancing</td><td>AWS.ELB</td></tr>
    <tr><td>Amazon Elastic MapReduce</td><td>AWS.EMR</td></tr>
    <tr><td>AWS Identity and Access Management</td><td>AWS.IAM</td></tr>
    <tr><td>Amazon S3</td><td>AWS.S3</td></tr>
    <tr><td>Amazon Simple Email Service</td><td>AWS.SES</td></tr>
    <tr><td>Amazon SimpleDB</td><td>AWS.SimpleDB</td></tr>
    <tr><td>Amazon Simple Notification Service</td><td>AWS.SNS</td></tr>
    <tr><td>Amazon Simple Queue Service</td><td>AWS.SQS</td></tr>
    <tr><td>AWS Security Token Service</td><td>AWS.STS</td></tr>
  </tbody>
</table>

## License

This SDK is distributed under the
[Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0).

```no-highlight
Copyright 2012. Amazon Web Services, Inc. All Rights Reserved.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
