Version: NAFATH-V1
Track: Software 
## Overview
A national digital login service lets citizens access several government services through one account on a website or mobile app. Software standards manage the login process and allow services to request limited access without sharing passwords. Artificial intelligence can help detect unusual login patterns, but its decisions need testing and human oversight. Mobile permissions protect sensitive phone features and require clear requests when access is needed. Networking technologies can reduce exposure of DNS queries while data moves across the internet. Cybersecurity controls, especially phishing-resistant authentication, help stop attackers from stealing access. Data governance ensures that personal information is collected for clear purposes, stored securely, and handled according to Oman’s law. In the Software track, the key issue is how OAuth 2.0 delegated authorization differs from OpenID Connect user authentication.

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
DNS over HTTPS (DoH) sends DNS queries and responses through encrypted HTTPS connections to a DNS resolver. It reduces the ability of observers on local networks to read or alter the domain lookups made for the login service. However, the resolver can still see those queries, while network observers may identify destination IP addresses or other metadata. DoH does not hide all browsing activity or encrypt the login service’s other traffic; HTTPS remains necessary.

Resource: RFC 8484 - DNS Queries over HTTPS (DoH) - https://www.rfc-editor.org/rfc/rfc8484

## Cybersecurity
Phishing-resistant authentication cryptographically binds the login response to the legitimate service or its protected connection, preventing a fake website from reusing it. Multi-factor FIDO2/WebAuthn passkeys with user verification and PIN-protected smart cards using client-authenticated TLS can qualify. Passwords combined with SMS codes, email codes, authenticator-app one-time passwords, or ordinary push approvals do not provide phishing resistance. Attackers may trick users into entering or approving those credentials on fraudulent sites.

Resource: NIST SP 800-63B - Authenticators - https://pages.nist.gov/800-63-4/sp800-63b/authenticators/
## Data
Oman’s Personal Data Protection Law exempts processing by state administrative units when performing their legally assigned duties. The government Personal Data Protection Policy under Circular 6/2024 still governs such processing. Where the law applies, the authority must provide clear processing information, respect personal data rights, maintain processing records, protect information, and report qualifying breaches. Consent or an applicable exception must be assessed, alongside rules for sensitive data and overseas transfers. The authority should confirm which legal requirements apply.

Resource: Governance - Personal Data Protection - https://www.mtcit.gov.om/sectors/governance/personal

## Misconception in My Track
A common misconception in software development is that OAuth 2.0 alone proves who a user is. In reality, OAuth 2.0 mainly delegates access to resources; an access token is not automatically proof of a user’s identity. OpenID Connect adds a standardized authentication layer and an ID token that a client can validate. The OpenID Connect Core specification states under its Abstract: “OpenID Connect 1.0 is a simple identity layer on top of the OAuth 2.0 protocol.” For this project, confusing access tokens with ID tokens could lead to an insecure login design.

## Open Question
How will the authority verify that every participating government service validates OpenID Connect ID tokens correctly and grants only the access permissions each service needs?
