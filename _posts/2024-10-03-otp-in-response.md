---
layout: post
title: "OTP in Response: A Major Client-Side Security Flaw"
date: 2024-10-03 12:00:00 +0000
author: "D Naveen Kumar"
categories: security otp
tags: otp client-side vulnerabilities
---

## Introduction

In an application I tested, a significant security vulnerability was discovered involving the generation and validation of One-Time Passwords (OTPs). The OTP was sent directly in the response to the browser, and the application relied solely on client-side validation to verify its authenticity. This approach not only exposes the application to various attack vectors but also undermines the effectiveness of the OTP as a security measure.

## The Vulnerability

A screenshot of the application’s sign-in page:

![Sign-in Page Screenshot](assets/images/sign-in-page.png)

The application's design flaw lies in its reliance on client-side validation for OTP verification. When a user attempts to log in, the OTP is generated and sent to the browser as part of the server's response. This means that once the OTP reaches the client, it is the client that must validate it.

## OTP Generation

A screenshot showing the OTP being generated:

![OTP Generated Screenshot](assets/images/otp-generated.png)

This architecture introduces critical security risks. If a malicious actor can intercept the server response, they can gain access to the OTP and potentially bypass the authentication process.

## Server Response with OTP

A redacted screenshot of the response showing the OTP being sent to the browser:

![Response OTP Screenshot](assets/images/otp-response.png)

## Proof of Client-Side Validation

To illustrate the vulnerability further, I captured a screenshot that confirms the application is performing validation on the client side. This validation can be manipulated, allowing an attacker to exploit this weakness easily.

![Proof of Client-Side Validation](assets/images/client-side-validation.png)

## Conclusion

Attackers have the ability to manipulate client-side scripts, which can enable them to completely bypass validation checks that are intended to secure the application. This manipulation may occur through various methods, such as altering the script directly in the browser's developer tools or using automated tools to modify the client-side behavior, rendering the validation process ineffective and leaving the application vulnerable to exploitation.
