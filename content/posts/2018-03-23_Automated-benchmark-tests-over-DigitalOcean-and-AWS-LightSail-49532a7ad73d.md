---
author:
  name: "Ayush Verma"
date: 2019-10-14
linktitle: Automated benchmark tests over DigitalOcean and AWS LightSail
type:
- post
- posts
title: Automated benchmark tests over DigitalOcean and AWS LightSail
weight: 10
series:
- Cloud
---

A comparison between DigitalOcean and AWS LightSail for Data Centers located in London.

A comparison between DigitalOcean and AWS LightSail for Data Centers located in London.

### VPS benchmarks

I did ran some standard benchmark tests over [DO](https://www.digitalocean.com/) and [AWS](https://lightsail.aws.amazon.com/ls/webapp/home) with bench.sh

So , here’s the Available stacks for deploying preconfigured stacks

AWS Lightsail is typically a EC2 Instance with Easier and less complicated GUI . They offer standalone plans and stacks mentioned below -

![LightSail](https://cdn-images-1.medium.com/max/800/1*L3OzYouFxlJWrinsUbuXPA.png)
LightSail

Digital Ocean has very good community and set of Articles to get you Onboard the Server. They provide a few cool amazing stacks including Machine Leaning.

![](https://cdn-images-1.medium.com/max/800/1*HOz2wxx-9_kY4y6IqZhGrg.png)

Now comes the pricing , AWS Starts with 5$ Plan that provides 512MB RAM and 512GM Transfer but at the same Price , Digital Ocean provides 1 GB of RAM and 1TB Transfer. Decision is yours 💸

![](https://cdn-images-1.medium.com/max/800/1*YYSiBEk-zqt5NDKaOKQ9DQ.png)
![](https://cdn-images-1.medium.com/max/800/1*Tk3-llqxtMh268xgtlvxDg.png)

Digital Ocean :

Here’s results of benchmarks ran over 1 GB Ubuntu server at London Data Centre.

**Keep an eye , The I/O Operations speed is 241MB/S and Average goes to 445MB/S.**

![](https://cdn-images-1.medium.com/max/800/1*MXDOfpgVFWv8acRQPepOhQ.png)

AWS LightSail

LightSail got an I/O Speed of 67.8MB/S which is definitely slower and would cause issues in Memory Intensive Applications.

![](https://cdn-images-1.medium.com/max/800/1*1QTjBnIL7jbwWkdNwx7jPg.png)

Here’s an Image of both Screen splitted horizontally ,

![](https://cdn-images-1.medium.com/max/800/1*jP8kRRYObxiNSBQw0yKyjw.png)

### Inference

So , At 10$ , If you are looking for heavy memory intensive applications and good alert system then Digital Ocean is definitely a better choice in market

But If you are complete newbie and looking for just easy workaround like download .pem and get started then LightSail is a good option for you .

Hope , That helped . 💚

By [Ayush Verma](https://medium.com/@Ayushverma8) on [March 23, 2018](https://medium.com/p/49532a7ad73d).

[Canonical link](https://medium.com/@Ayushverma8/digitalocean-and-lightsail-49532a7ad73d)

Exported from [Medium](https://medium.com) on July 6, 2019.