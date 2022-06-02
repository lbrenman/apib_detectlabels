# API Builder Project Readme

An Image Processing API example based on API Builder. Project can be found [here](https://github.com/lbrenman/apib_detectlabels) on Github. The API leverages [AWS Rekognition](https://docs.aws.amazon.com/rekognition/index.html).

The API is an example of an API First API designed in Stoplight and Built in API Builder as described in the following blog post:

* [An “API First” Image Label Detection API using API Builder](https://gist.github.com/lbrenman/f64e8a06bb50e8fa3150be8e02cd9cd2)

The API is shown below:

`POST /detectlabels`

with the following body:

```
{
  "image": <Base64 encoded image>
}
```

which results in the following sample response:

```
{
    "Labels": [
        {
            "Name": "Car",
            "Confidence": 98.41893005371094,
            "Instances": [
                {
                    "BoundingBox": {
                        "Width": 0.9095886945724487,
                        "Height": 0.4260041415691376,
                        "Left": 0.044332683086395264,
                        "Top": 0.37117668986320496
                    },
                    "Confidence": 98.41893005371094
                }
            ],
            "Parents": [
                {
                    "Name": "Vehicle"
                },
                {
                    "Name": "Transportation"
                }
            ]
        },
        {
            "Name": "Automobile",
            "Confidence": 98.41893005371094,
            "Instances": [],
            "Parents": [
                {
                    "Name": "Vehicle"
                },
                {
                    "Name": "Transportation"
                }
            ]
        },
        .
        .
        .
        {
            "Name": "Jaguar Car",
            "Confidence": 57.534969329833984,
            "Instances": [],
            "Parents": [
                {
                    "Name": "Car"
                },
                {
                    "Name": "Vehicle"
                },
                {
                    "Name": "Transportation"
                }
            ]
        }
    ],
    "LabelModelVersion": "2.0"
}
```

For the example above, I use this [**Base64 encoded data**](https://gist.github.com/lbrenman/86bfd4ac91b8ccdaf7c5cf45b2e317fc) for the car image shown below:

![](https://i.imgur.com/8XiS1DF.jpg)

The API uses API Key authentication that is passed in a header with key apikey.

The container requires three env vars:

* API_KEY - a randomly selected API Key that you can provide that is used to authenticate API calls in a header with key apikey
* AWS_ACCESS_KEY_ID - AWS Access Key
* AWS_SECRET_ACCESS_KEY - AWS Secret Key

You can read about AWS credentials [here](https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/loading-node-credentials-environment.html).

A docker image can be accessed [here](https://hub.docker.com/r/lbrenman/apib_detectsentiment)
