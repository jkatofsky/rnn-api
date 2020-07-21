# textgenrnn-api

## Description

A lightweight web service that allows clients to create RNNs trained on certain strings, and then query them. Uses the phenomenal [textgenrnn](https://github.com/minimaxir/textgenrnn) Python module for all of the text generation. The API creates no persistent data; rather, the trained models are deleted a given time after they are last interacted with. At the moment, `textgenrnn-api`'s purpose is to let web apps quickly get custom RNN output based on short-term data, not to facilitate long-term RNN model storage or management. Perhaps it can be expanded later. `textgenrnn-api` will not output anything worthy of a NLP paper, but it is pretty fun.

## Routes

At the moment, `textgenrnn-api` has two routes:

- `/train`:
  - supply a list of `training_strings`
  - get back `model_id`
- `/generate`:
  - supply a `model_id`, and optionally, an `options` object which can contain the `prompt`, `max_length`, and/or `temperature` fields
  - get back `output`

## Setup

You can run this API on your machine by cloning this repo,

```bash
git clone https://github.com/jkatofsky/textgenrnn-api.git
cd textgenrnn-api
```

creating a python `venv` (optional, but good practice),

```bash
python3 -m venv env
source env/bin/activate
```

installing the required modules,

```bash
pip3 install -r requirements.txt
```

and running `main.py`.

```bash
cd textgenrnn-api
python3 main.py
```

## Configuration & Deployment

To play with some settings for request handling/text generation, or to set an `IS_LOCAL` flag to enable debug logs and hot reload when running locally, you can modify the variables in `config.env`. They're used throughout the API's code.

I'm planning to run `textgenrnn-api` on Google Cloud's App Engine, which is the purpose of `app.yaml`. [Here](https://cloud.google.com/appengine/docs/standard/python3/building-app) is Google's guide for deploying a Python 3 app to App Engine.
