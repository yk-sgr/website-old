---
author: Yannick Seeger
title: "How I configure my Go Applications"
date: 2020-11-11T10:11:24+02:00
description: How to configure your Go Application
tags: ["programming", "golang", "go"]
summary: How to configure your Go Application.
cover:
    image: "https://miro.medium.com/max/1400/1*g4ECiJ5gMg9IuRZ4CY1CTA.png"
    alt: "Go Logo"
---

In this article I will show you what I think is the best way to configure your Go Application.

---

In the past I’ve been trying a lot of configuration formats like JSON, YAML, properties and much more. But in the recent past I see myself just using **environment variables**.

In the modern cloud age where we rely heavily on stateless services, environment variables are a good fit, especially when using Docker or Kubernetes.

To simplify my code for loading configurations, I make use of [godotenv](https://github.com/joho/godotenv) and [envconfig](https://github.com/kelseyhightower/envconfig).

- godotenv loads .env files if they exist, what they usually do in my local development environments.
- envconfig “loads” existing environment variables into a struct. It supports the use of struct tags to specify alternate, default, and required environment variables.

*config.go*
{{< highlight go "linenos=table" >}}
package main

import (
  "log"
  "github.com/joho/godotenv"
  "github.com/kelseyhightower/envconfig"
)

type Config struct {
  Debug       bool    `default:"false"`
  PostgresDSN string  `envconfig:"POSTGRES_DSN"`
  Port        string  `default:":3000"`
}

func LoadConfig() *Config {
  _ = godotenv.Load()
  var cfg Config
  err := envconfig.Process("SERVICE", &cfg)
  if err != nil {
    log.Fatalf("could not load config: %v", err)
  }
  return &cfg
}
{{< / highlight >}}

If you have sucessfully built your configuration struct you can initialize your config as following:

*main.go*
{{< highlight go "linenos=table" >}}
package main

import "fmt"

func main() {
  cfg := LoadConfig()
  fmt.Println(cfg.PostgresDSN)
}
{{< / highlight >}}

Your application now loads .env files if provided or existing environment variables.

*.env*
{{< highlight env "linenos=table" >}}
SERVICE_DEBUG=true
SERVICE_POSTGRES_DSN=postgresql://user@localhost
{{< / highlight >}}

---

I’m happy if I could help you get some inspiration or solve your problem.