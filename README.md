# Satya_Stripe_payment

Written By

Satyanarayan Behera

# Introduction

It's no lie that "everything is going digital". A lot of products never reach the shelves, but rather get sold online.

With the arising number of entrepreneurs, startups, and online sales, a very high percentage of websites nowadays have a payment system, whether it's a subscription to a service or a one-time payment for a product.

Handling finances is a delicate subject, and coming up with your own logic to handle payments can sound off-putting for a lot of developers, especially if they don't have much prior experience with such systems.

To our aid come services like PayPal and Stripe. Both services are great and each have their pros and cons. While PayPal has certainly been the more popular one, Stripe offers more payment methods and simpler fees, though it does take a day more to withdraw funds - although for many, this isn't really important.

# What is Stripe?

Stripe is a payment processor for small-to-medium size businesses which offers several products within their network - business data, fraud detection with machine learning, issuing cards, etc.

As it does with a lot of useful services, Spring offers support for integrating the Stripe API and implementing the payment functionality into your Spring applications.

# Integrating Stripe with a Spring Boot Application
Stripe Account-

First and foremost, to deal with the Stripe API, we need to open an account on Stripe.

Opening an account is very simple, and the only thing you need to do is verify your email address and phone number. Although this will only provide you with a test account while your application is approved by Stripe, which can take anywhere from a few minutes to a few days.


Add in application.properties file:
![image](https://user-images.githubusercontent.com/43759116/126889370-f7ebbd4e-7ffc-46d3-8bb8-d11b745d08df.png)


For starting using a stripe first you need to add stripe’s official library into your project. This library allows you to access all Stripe API.

Server-side:
For spring boot project add the following dependency into your pom.xml file

<dependency>
<groupId>com.stripe</groupId>
<artifactId>stripe-java</artifactId>
<version>{VERSION}</version>
</dependency>
 

Client side:
Stripe provide Stripe.js library which you can add to your project by using script tag like,

<script src="https://js.stripe.com/v3/"></script>

Since the stripe-java dependency isn't in the Spring Initializr list, we'll add it directly to our pom.xml file:

<dependency>
    <groupId>com.stripe</groupId>
    <artifactId>stripe-java</artifactId>
    <version>10.12.1</version>
</dependency>

Our application will offer two options for potential buyers:

1.One-time Purchase: They can purchase a StackAbuse course for a one-time payment
2.Subscription: They can sign up for a place in our email list, where we send out weekly mini-courses (coming soon in an upcoming article)
Additionally, we'll be sending email receipts to our customers.


The general flow of Stripe requests looks a little something like this:

1.Front-end: The front-end is used to send form-encoded credit card data to Stripe
2.Stripe: Stripe responds by sending back a token within the response
3.Front-end: The front-end communicates with our back-end by providing the token and amount required to pay
4.Back-end: Uses the private (secret) Stripe key, along with the token, amount and currency to process the payment


# Stripe Java client library

[![Maven Central](https://img.shields.io/maven-central/v/com.stripe/stripe-java)](https://mvnrepository.com/artifact/com.stripe/stripe-java)
[![JavaDoc](http://img.shields.io/badge/javadoc-reference-blue.svg)](https://stripe.dev/stripe-java)

The official [Stripe][stripe] Java client library.

## Installation

### Requirements

- Java 1.8 or later

### Gradle users

Add this dependency to your project's build file:

```groovy
implementation "com.stripe:stripe-java:20.66.0"
```

### Maven users

Add this dependency to your project's POM:

```xml
<dependency>
  <groupId>com.stripe</groupId>
  <artifactId>stripe-java</artifactId>
  <version>20.66.0</version>
</dependency>
```

### Others

You'll need to manually install the following JARs:

- The Stripe JAR from <https://github.com/stripe/stripe-java/releases/latest>
- [Google Gson][gson] from <https://repo1.maven.org/maven2/com/google/code/gson/gson/2.8.5/gson-2.8.5.jar>.


## Documentation

Please see the [Java API docs][api-docs] for the most
up-to-date documentation.

See [video demonstrations][youtube-playlist] covering how to use the library.


