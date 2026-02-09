# Editing “Authenticating with SSL/TLS” from Worldpay’s Developer Documentation

## Overview section

**My version**

Transport Layer Security (TLS), previously known as Secure Sockets Layer (SSL), is a security protocol that provides confidentiality and integrity for messages exchanged between a client and server and, most often, authentication of the server by the client.

Mutual TLS authentication (mTLS), also known as Client Certificate Authentication (CCA), authenticates the server using X509 certificates during the TLS handshake. Then, it authenticates the client to ensure it is authorized to make the request, similar to how it would for our HTTP-based authentication mechanism.

To use mTLS, you must:
1. Securely send us one or more issuer certificates that we can associate with your account. 
2. Configure your client with a client certificate to send and its corresponding private key. 
Note: The certificate must be signed by one of the issuer certificates that you've sent to us. You can additionally use an intermediate certificate signed by the issuer certificate.

During the TLS handshake, our service requests that you provide a certificate. Your client sends us the certificate along with proof of possession of the private key. You may optionally include one intermediate certificate in the handshake. We then authenticate you based on five criteria:
1. The time on our servers must be within the validity period of the client, optional intermediate, and issuer certificates.
2. The signature of each certificate must be valid and the trust chain terminates with one of the issuer certificates that you previously provided to us.
3. The proof of possession of the corresponding private key for the client certificate must be valid.
4. We do not have a revocation notice for any certificate in the chain.
5. If you provided any RDNs for the client certificate's Distinguished Name, they must match the client certificate. 

**Original version**

Transport Layer Security (TLS), also known by its historical name of Secure Sockets Layer (SSL), is a security protocol that provides confidentiality and integrity for messages exchanged between a client and server and, in its most typical use-case, authentication of the server by the client.

Mutual TLS authentication (mTLS), also known as Client Certificate Authentication (CCA), adds authentication of the client during the TLS handshake. This is done in a very similar way to which the client authenticates the server, using X509 certificates that are exchanged during the handshake. Once the handshake is completed your authenticated identity is checked to ensure it is authorized to make the request, the same as it would be for using our HTTP-based authentication mechanism.

In order to use mTLS, you must first securely send us one or more issuer certificates that we associate with your account. You then configure your client, with a client certificate to send, and its corresponding private key. The certificate must be signed by one of the issuer certificates that you've sent to us (or you may use an intermediate certificate signed by the issuer certificate as well, if you wish).

During the TLS handshake, our service requests that you provide a certificate. Your client sends us the certificate along with proof of possession of the private key. You may optionally include one intermediate certificate in the handshake. We then authenticate you based on five criteria:
1. The time on our servers must be within the validity period of the client, optional intermediate and issuer certificate.
2. The signature of each certificate must be valid and the trust chain terminates with one of the issuer certificates that you have previously provided us.
3. The proof of possession of the corresponding private key for the client certificate must be valid.
4. We do not have a revocation notice for any certificate in the chain.
5. If you have provided any RDNs for the client certificate's Distinguished Name, these much match.

## From Step 1 of the Integration Guide section
**My version**

Your local configuration must override the IP addresses for `try.access.worldpay.com` and `access.worldpay.com`. This points your traffic through the mTLS-secured access point to our services. When you don’t change IPs, you can’t provide identity or authentication data, resulting in a successful TLS handshake but a failed request.

Each host environment has two IP addresses to provide a fault-isolation design that increases the availability of Access Worldpay using mTLS. The two IPs are hosted on and managed by two different sets of physical infrastructure. If one IP is unavailable, the other IP is available.

**Original version**

Your local configuration must override the IP addresses for try.access.worldpay.com and access.worldpay.com. This is to point your traffic through the mTLS-secured access point to our services. Without changing IPs, the TLS handshake succeeds, but as you are providing no identity or authentication data, your request fails.

Each environment has two IP addresses to provide a fault-isolating design that increases the availability of Access Worldpay via mTLS. The two IPs are hosted on and managed by two different sets of physical infrastructure. If one IP is unavailable then the other will be available.
