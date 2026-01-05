---
layout: default
title: About my Dissertation
---

# About my Dissertation

## Background

In late 2016 a series of high-profile DDoS attacks, carried out by infected IoT devices (the mirai botnet), highlighted the need for improved security mechanisms in the internet of things. The most notable of these was the attack on the DNS provider Dyn which caused significant outages across the US and Europe.

The investigative journalist Brian Krebs reported on the attacks only to have his blog (KrebsOnSecurity) hit by a 620 Gbps DDos. Nine years later, the mirai-style botnet continues to be a significant threat; and brian krebs continues to report on it [read here](https://krebsonsecurity.com/2025/10/ddos-botnet-aisuru-blankets-us-isps-in-record-ddos/).

There are, of course, many more attacks to be concerned about. Intrusion detection systems (IDSs) are a necessary technology for detecting and preventing these attacks. Traditional NIDSs (Network IDSs) send network traffic data to a central server for analysis: which, for large streams of IoT data, can strain the network and further expose private information.

Federated learning offers a promising alternative. It was introduced by google researchers in a paper entitled "communication-efficient learning of deep networks from decentralised data" and it works by first: initialising model weights and distributing them to clients, second: clients train the models on local data, and then finally the server aggregates the local weights according to some strategy.

This reduces the strain on the network: "communication efficient" and, at first glance, seems to ensure no private data is sent to a central server.

## Motivation

My dissertation aims to simulate an FL-based NIDS and explore the effect of privacy preserving techniques on it's usability. 

In the advent of 6G, we can expect another boom in the internet of things and with it IoT-based attacks. We can also expect more computation at the edge and more machine learning; further demonstrating the relevance of this topic.  

Additionally there is a lot of concern over the sheer amount of resources large AI models are currently using. Researchers from Cambridge, UCL and Avignon Universite collaborated to show that FL provides a less wasteful alternative. 

Moving the computation to the edge gives clients more control over their own data and less reliance on central servers.

This dissertation gives me the oppurtunity to explore many interesting and relevant areas of computer science. It focuses on federated learning, differential privacy and intrusion detection but also exposes me to distributed algorithms. Since I'm not proposing a novel aggregation scheme I won't be looking into distributed algorithms too much. However, reading papers that do propose and analyse their own aggregation schemes has definitely sparked an interest.

## Proposed Experiment



## Proposed Model

## The Theoretical Side

## Where I'm At

