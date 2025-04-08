# 🌦️ Weather API with Java (Spring Boot)

This project demonstrates how to build a **Weather API** in **Java** using **Spring Boot** by fetching data from a third-party weather service. Along the way, you'll learn how to make HTTP requests, cache data using Redis, handle environment variables, and build robust, well-structured APIs.

---

![UML diagram](./weather-api.png)

---

## 🚀 Project Objectives

- Integrate a 3rd-party weather API (like Visual Crossing)
- Cache responses using **Redis**
- Securely manage secrets with **environment variables**
- Handle errors and invalid inputs gracefully
- Optionally add **rate limiting** to prevent abuse

---

## 🔗 Suggested Weather API

Use any 3rd-party API of your choice. For example, [Visual Crossing Weather API](https://www.visualcrossing.com/) is **free and easy to use**.

---

## ⚙️ Tech Stack

- Java 21+
- Spring Boot (REST)
- Spring Data Redis
- [Lettuce or Jedis](https://spring.io/projects/spring-data-redis) (Redis client)
- Spring WebClient (for HTTP calls)
- dotenv or application.yml for environment configs

---

## 🧠 Caching with Redis

To avoid redundant API calls and speed up responses:

- Use the **city name/code** as a Redis key.
- Cache the API response as the value.
- Set a **TTL (Time to Live)** for each key (e.g., 12 hours).

```java
redisTemplate.opsForValue().set("weather:Nairobi", responseBody, 12, TimeUnit.HOURS);

