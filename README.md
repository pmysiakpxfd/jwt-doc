# JWT Framework

This framework provides an implementation of:

* JW**S** [JSON Web Signature (RFC 7515)](https://tools.ietf.org/html/rfc7515),
* JW**T** [JSON Web Token (RFC 7519)](https://tools.ietf.org/html/rfc7519),
* JW**E** [JSON Web Encryption (RFC 7516)](http://tools.ietf.org/html/rfc7516),
* JW**A** [JSON Web Algorithms (RFC 7518)](http://tools.ietf.org/html/rfc7518).
* JW**K** [JSON Web Key (RFC 7517)](http://tools.ietf.org/html/rfc7517).
* JSON Web Key Thumbprint ([RFC 7638](https://tools.ietf.org/html/rfc7638)).
* Unencoded Payload Option [RFC7797](https://tools.ietf.org/html/rfc7797).

This framework is not just a library, it contains Symfony bundles for an easy integration into your application.
It also provides a standalone console command that will help you to manager your keys and key sets. 

# Provided Features

## Supported Input Types:

JWS or JWE objects support every input that can be encoded into JSON:

* [x] `string`, `array`, `integer`, `float`...
* [x] Objects that implement the `\JsonSerializable` interface such as `JWK` or `JWKSet`

The [detached](https://tools.ietf.org/html/rfc7515#appendix-F) and unencoded payloads are supported.
This means you can sign and verify payload without base64 encoding operation.

## Supported Serialization Modes

* [x] Compact JSON Serialization Syntax for JWS andJWE
* [x] Flattened JSON Serialization Syntax for JWS andJWE
* [x] General JSON Serialization Syntax for JWS andJWE

## Supported Compression Methods

| Compression Method | Supported | Comment                                                         |
| ------------------ |:---------:| --------------------------------------------------------------- |
| Deflate (`DEF`)    | YES       |                                                                 |
| GZip (`GZ`)        | YES       | *This compression method is not described in the specification* |
| ZLib (`ZLIB`)      | YES       | *This compression method is not described in the specification* |

## Supported Key Types (JWK)

| Key Type | Supported | Comment                                      |
| -------- |:---------:| -------------------------------------------- |
| `oct`    | YES       | Symmetric keys                               |
| `RSA`    | YES       | RSA based asymmetric keys                    |
| `EC`     | YES       | Elliptic Curves based asymmetric keys        |
| `OKP`    | YES       | Octet Key Pair based asymmetric keys         |

JWK objects support JSON Web Key Thumbprint ([RFC 7638](https://tools.ietf.org/html/rfc7638)).

*Note: we use a `none` key type for the `none` algorithm only.*

## Key Sets (JWKSet)

JWKSet is fully supported.

## Supported Signature Algorithms

| Signature Algorithm            | Supported | Comment                                                                                            |
| ------------------------------ |:---------:| -------------------------------------------------------------------------------------------------- |
| `HS256`, `HS384` and `HS512`   | YES       |                                                                                                    |
| `HS256`, `ES384` and `ES512`   | YES       |                                                                                                    |
| `RS256`, `RS384` and `RS512`   | YES       |                                                                                                    |
| `PS256`, `PS384` and `PS512`   | YES       |                                                                                                    |
| `none`                         | YES       | **Please note that this is not a secured algorithm. USE IT WITH CAUTION!**                         |
| *`EdDSA` with `Ed25519` curve* | YES       | [For PHP 7.1, third party extension highly recommended](https://github.com/jedisct1/libsodium-php) |
| *`EdDSA` with `Ed448` curve*   | NO        |                                                                                                    |

## Supported Key Encryption Algorithms

| Key Encryption Algorithm                                            | Supported | Comment                                                                                            |
| ------------------------------------------------------------------- |:---------:| -------------------------------------------------------------------------------------------------- |
| `dir`                                                               | YES       |                                                                                                    |
| `RSA1_5`, `RSA-OAEP` and `RSA-OAEP-256`                             | YES       |                                                                                                    |
| `ECDH-ES`, `ECDH-ES+A128KW`, `ECDH-ES+A192KW` and `ECDH-ES+A256KW`  | YES       |                                                                                                    |
| `A128KW`, `A128KW` and `A128KW`                                     | YES       |                                                                                                    |
| `PBES2-HS256+A128KW`, `PBES2-HS384+A192KW` and `PBES2-HS512+A256KW` | YES       |                                                                                                    |
| `A128GCMKW`, `A192GCMKW` and `A256GCMKW`                            | YES       |                                                                                                    |
| `EdDSA` with `X25519` curve                                         | YES       | [For PHP 7.1, third party extension highly recommended](https://github.com/jedisct1/libsodium-php) |
| `EdDSA` with `X448` curve                                           | NO        |                                                                                                    |

## Supported Content Encryption Algorithms

| Content Encryption Algorithm                         | Supported | Comment |
| ---------------------------------------------------- |:---------:| ------- |
| `A128CBC-HS256`, `A192CBC-HS384` and `A256CBC-HS512` | YES       |         |
| `A128GCM`, `A192GCM` and `A256GCM`                   | YES       |         |

# Prerequisites

This framework needs at least:
* ![PHP 7.1+](https://img.shields.io/badge/PHP-7.1%2B-ff69b4.svg),
* OpenSSL extension.
* GMP extension.
* MBString extension.

Please consider the following optional requirements:
* If you intent to use `EdDSA` or `ECDH-ES` algorithm with `Ed25519`/`X25519` curves on PHP 7.1, please install this [third party extension](https://github.com/jedisct1/libsodium-php)

# Continuous Integration

It has been successfully tested using `PHP 7.1` with all algorithms.

Tests vectors from the [RFC 7520](http://tools.ietf.org/html/rfc7520) are fully implemented and all tests pass.

We also track bugs and code quality using [Scrutinizer-CI](https://scrutinizer-ci.com/g/web-token/jwt-framework) and [Sensio Insight](https://insight.sensiolabs.com/projects/b7efa68f-8962-41cf-a2e3-4444426bc95a).

Coding Standards are verified by [StyleCI](https://styleci.io/repos/105997386).

Code coverage is analyzed by [Coveralls.io](https://coveralls.io/github/web-token/jwt-framework).

# How to use

* [The components](component/index.md)
* [The bundles](bundle/index.md)
* [The console commands](console/index.md)

# Performances

Please read the [performance page](benchmarks/index.md) to know how to test the algorithms of the framework.

You can also see the [last benchmarks](benchmarks/results.md) made with our development environment.

# Contributing

Requests for new features, bug fixed and all other ideas to make this framework useful are welcome.
If you feel comfortable writing code, you could try to fix [opened issues where help is wanted](https://github.com/web-token/jwt-framework/labels/help+wanted) or [those that are easy to fix](https://github.com/web-token/jwt-framework/labels/easy-pick).

Do not forget to [follow these best practices](https://github.com/web-token/jwt-framework/.github/CONTRIBUTING.md).

**If you think you have found a security issue, DO NOT open an issue**. You should submit your issue here. 

# Licence

This project is release under [MIT licence](LICENSE.md).
