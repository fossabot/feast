<p align="center">
    <a href="https://feast.dev/">
      <img src="docs/assets/feast_logo.png" width="550">
    </a>
</p>
<br />

[![Unit Tests](https://github.com/feast-dev/feast/workflows/unit%20tests/badge.svg?branch=master)](https://github.com/feast-dev/feast/actions?query=workflow%3A%22unit+tests%22+branch%3Amaster)
[![Code Standards](https://github.com/feast-dev/feast/workflows/code%20standards/badge.svg?branch=master)](https://github.com/feast-dev/feast/actions?query=workflow%3A%22code+standards%22+branch%3Amaster)
[![Docs Latest](https://img.shields.io/badge/docs-latest-blue.svg)](https://docs.feast.dev/)
[![GitHub Release](https://img.shields.io/github/v/release/feast-dev/feast.svg?style=flat&sort=semver&color=blue)](https://github.com/feast-dev/feast/releases)
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Ffeast-dev%2Ffeast.svg?type=shield)](https://app.fossa.com/projects/git%2Bgithub.com%2Ffeast-dev%2Ffeast?ref=badge_shield)

## Overview

Feast (Feature Store) is a tool for managing and serving machine learning features. Feast is the bridge between models and data.

Feast aims to:
* Provide a unified means of managing feature data from a single person to large enterprises.
* Provide scalable and performant access to feature data when training and serving models.
* Provide consistent and point-in-time correct access to feature data.
* Enable discovery, documentation, and insights into your features.

![](docs/.gitbook/assets/feast-docs-overview-diagram-2.svg)

Feast decouples feature engineering from feature usage, allowing independent development of features and consumption of features. Features that are added to Feast become available immediately for training and serving. Models can retrieve the same features used in training from a low latency online store in production.
This means that new ML projects start with a process of feature selection from a catalog instead of having to do feature engineering from scratch.

```
# Setting things up
fs = feast.Client('feast.example.com')
customer_features = ['CreditScore', 'Balance', 'Age', 'NumOfProducts', 'IsActive']

# Training your model (typically from a notebook or pipeline)
data = fs.get_historical_features(customer_features, customer_entities)
my_model = ml.fit(data)

# Serving predictions (when serving the model in production)
prediction = my_model.predict(fs.get_online_features(customer_features, customer_entities))
```

## Getting Started with Docker Compose

Clone the latest stable version of the [Feast repository](https://github.com/gojek/feast/) and navigate to the `infra/docker-compose` sub-directory:

```
git clone --depth 1 --branch v0.6.2 https://github.com/feast-dev/feast.git
cd feast/infra/docker-compose
cp .env.sample .env
```

The `.env` should be configured based on your environment. A GCP service account can be added if BigQuery will be used for historical serving (storing and retrieving training data).

Bring up Feast:
```
docker-compose up -d
```

The command above will bring up a complete Feast deployment with a [Jupyter Notebook](http://localhost:8888/tree/feast/examples) containing example notebooks.

## Important resources

Please refer to the official documentation at <https://docs.feast.dev>

 * [Why Feast?](https://docs.feast.dev/why-feast)
 * [Concepts](https://docs.feast.dev/user-guide/overview)
 * [Installation](https://docs.feast.dev/getting-started)
 * [Examples](https://github.com/feast-dev/feast/blob/master/examples/)
 * [Roadmap](https://docs.feast.dev/roadmap)
 * [Change Log](https://github.com/feast-dev/feast/blob/master/CHANGELOG.md)
 * [Slack (#Feast)](https://join.slack.com/t/kubeflow/shared_invite/zt-cpr020z4-PfcAue_2nw67~iIDy7maAQ)

## Notice

Feast is a community project and is still under active development. Your feedback and contributions are important to us. Please have a look at our [contributing guide](docs/contributing/contributing.md) for details.


## License
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Ffeast-dev%2Ffeast.svg?type=large)](https://app.fossa.com/projects/git%2Bgithub.com%2Ffeast-dev%2Ffeast?ref=badge_large)