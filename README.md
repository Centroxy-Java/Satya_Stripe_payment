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

# Server-side:
For spring boot project add the following dependency into your pom.xml file

<dependency>
<groupId>com.stripe</groupId>
<artifactId>stripe-java</artifactId>
<version>{VERSION}</version>
</dependency>
 

# Client side:
Stripe provide Stripe.js library which you can add to your project by using script tag like,

<script src="https://js.stripe.com/v3/"></script>

Since the stripe-java dependency isn't in the Spring Initializr list, we'll add it directly to our pom.xml file:

<dependency>
    <groupId>com.stripe</groupId>
    <artifactId>stripe-java</artifactId>
    <version>10.12.1</version>
</dependency>

# Our application will offer two options for potential buyers:

1.One-time Purchase: They can purchase a StackAbuse course for a one-time payment

2.Subscription: They can sign up for a place in our email list, where we send out weekly mini-courses (coming soon in an upcoming article)
Additionally, we'll be sending email receipts to our customers.


# The general flow of Stripe requests looks a little something like this:

1.Front-end: The front-end is used to send form-encoded credit card data to Stripe
2.Stripe: Stripe responds by sending back a token within the response
3.Front-end: The front-end communicates with our back-end by providing the token and amount required to pay
4.Back-end: Uses the private (secret) Stripe key, along with the token, amount and currency to process the payment

# Front-end

Stripe will automatically add the preferred Stripe Element into your HTML, where you mark it. For an example, to add the Card Element:

![image](https://user-images.githubusercontent.com/43759116/126889526-84b1b869-0f70-484c-88e0-3b4b768c64e6.png)

# Back-end

Controller
With the front-end, out of the way, let's focus a bit on the back-end side. Clicking "Submit" on the checkout window will send the information to Stripe, which will return a token that we need for authentication. Let's define a simple PaymentController:

![image](https://user-images.githubusercontent.com/43759116/126889560-da32505a-565e-4222-8177-c0d61402c2f5.png)

What we do here is very simple. We assign the STRIPE_PUBLIC_KEY value to a string for later use and add it to the model so that we can use it in the front-end. In our form above, we're using the amount and stripePublicKey to send a request to Stripe, which generates a stripeToken for us in response.

Let's make an endpoint for the returned response:

![image](https://user-images.githubusercontent.com/43759116/126889579-93653fb0-1278-47f9-bfdc-4edbbe9f64d7.png)

From the response, we simply extract the stripeToken and the amount parameters and pass them onto our service, which actually handles the communication with Stripe and the payment processing.

# Service

The service layer introduces us with a few new classes:

![image](https://user-images.githubusercontent.com/43759116/126889598-3f33b4f7-03b1-4d30-a432-83e32b5361d6.png)

# Running the Application

![image](https://user-images.githubusercontent.com/43759116/126889789-9c8831e2-36cb-4044-9aff-38424a36733b.png)

# Conclusion

With the rise of online dependency and payment, it's most probable that at some point your web application will have to handle/process some payments. Since it's a touchy subject, it's easiest and safest to let a third-party processor such as Stripe or PayPal handle the actual transaction and act as a trusted middleman.


# Stripe Java client library

[![Maven Central](https://img.shields.io/maven-central/v/com.stripe/stripe-java)](https://mvnrepository.com/artifact/com.stripe/stripe-java)
[![JavaDoc](http://img.shields.io/badge/javadoc-reference-blue.svg)](https://stripe.dev/stripe-java)


### Others

You'll need to manually install the following JARs:

- The Stripe JAR from <https://github.com/stripe/stripe-java/releases/latest>
- [Google Gson][gson] from <https://repo1.maven.org/maven2/com/google/code/gson/gson/2.8.5/gson-2.8.5.jar>.


## Documentation

Please see the [Java API docs][api-docs] for the most
up-to-date documentation.

See [video demonstrations][youtube-playlist] covering how to use the library.

# Stripe features

Authorization
Dispute Handling
Financial Reporting
Clean Canvas
Invoice
Open-Source Plugin
Payment Options
Mobile Customer Interface
Embeddable Checkout
Multicurrency Payouts
Roles and Permissions
Accounting Integrations
Unified Payout
Payout Timing
Consolidated Reports
Custom UI Toolkit
Collaboration Notes

# Stripe Benefits

Stripe offers a highly scalable and robust payment transaction and processing solution for any online-based business. Its user interface toolkit has the necessary elements for analytics, design, and a front-end for creating and customizing payment forms. Users can quickly embed checkout on their site by simply utilizing a Javascript line.

Invoices are made for sending out and requesting payment from customers who are aligned to the branding. The platform can be utilized quickly on-the-go via an iOS or Android app thanks to its mobile-friendly checkout option.

Stripe can offer payment gateway support options to customers. Users can cater payment to a majority of credit and debit cards in almost every country in the world. Digital wallets like Apple Play, Amex Express Checkout, and Alipay are intended for customers who want to pay conveniently without having to share personal card details. Local payment methods, local Stripe accounts, and preferred currencies are also supported by the platform.

In terms of optimizing revenue, Stripe can optimize routing paths with popular card networks which include American Express, MasterCard, and Visa. This pre-processing layer minimizes latency during transaction and dramatically enhances success rates.

Handling of disputes are now automated to effectively present any evidence in case of conflicts. Automated accounting support, collated reports, and financial reporting helps streamline and hasten reconciliation of transaction issues. This provides users information regarding refunds, transfers, fees, and other charges in real-time via the platform’s API and Dashboard.

Whenever a transaction is resolved, users can simplify and expedite how they can be paid from consolidated payouts. They can also have a bird’s eye view of charges made across payment types, countries, and currencies via information exportability and reporting in real-time.

