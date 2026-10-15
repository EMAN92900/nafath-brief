Version: NAFATH-V1
Track: Software 
## Overview
A national digital login service lets citizens access several government services through one account on a website or mobile app. Software standards manage the login process and allow services to request limited access without sharing passwords. Artificial intelligence can help detect unusual login patterns, but its decisions need testing and human oversight. Mobile permissions protect sensitive phone features and require clear requests when access is needed. Networking technologies can reduce exposure of DNS queries while data moves across the internet. Cybersecurity controls, especially phishing-resistant authentication, help stop attackers from stealing access. Data governance ensures that personal information is collected for clear purposes, stored securely, and handled according to Oman’s law. For the Software track, the central design question is the difference between OAuth 2.0 delegated authorization and OpenID Connect user authentication.

## Software
OAuth 2.0 is an authorization framework. It allows an application to obtain limited access to protected resources without receiving the user’s password. OpenID Connect (OIDC) adds an identity layer on top of OAuth 2.0 to authenticate users and provide an ID token containing identity claims. For the national service, OIDC should handle user sign-in, while OAuth 2.0 access tokens can authorize approved services to access permitted resources.

Resource: OpenID Connect Core 1.0 incorporating errata set 2 - https://openid.net/specs/openid-connect-core-1_0.html
## AI
Before deploying AI to flag suspicious logins, the authority should apply the NIST AI Risk Management Framework: Govern, Map, Measure, and Manage. It should evaluate false alarms that lock out legitimate users, missed attacks, biased results across groups, privacy risks from login data, and changes in model performance over time. Testing, documented accountability, human review of disputed decisions, and continuous monitoring are needed before and after launch.

Resource: AI RMF Core - https://airc.nist.gov/airmf-resources/airmf/5-sec-core/
## Mobile
Android restricts access to sensitive data and device features through runtime permissions. The login app cannot freely access features such as the camera, microphone, or location. It must check whether a dangerous permission is granted and request it before using the protected feature, preferably when the user starts the relevant action. Users may refuse or revoke permission. The app should explain the request and handle denial without unnecessary disruption.

Resource: Permissions on Android - https://developer.android.com/guide/topics/permissions/overview

## Networking

## Cybersecurity

## Data

## Misconception in My Track

## Open Question
