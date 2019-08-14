## Parcel cert generator for Firefox

Parcel bundler's self-signed certificates include some configuration which is appears incompatible with Firefox, which throws the certificate error with code `MOZILLA_PKIX_ERROR_CA_CERT_USED_AS_END_ENTITY`.

The error is explained at the bottom of [this page](https://wiki.mozilla.org/SecurityEngineering/x509Certs).

Parcel includes [this feature](https://github.com/parcel-bundler/parcel/blob/2c1499596680be6daf158334f4146b80592ed4be/packages/core/parcel-bundler/src/utils/generateCertificate.js#L66) in certificate generation, which causes the error.

This repo is a copy of the parcel generation script, with that feature omitted, to enable working certificate generation for Firefox.

### Usage

```
$ git clone git@github.com:shanehandley/parcel-cert-gen-firefox.git

$ cd parcel-cert-gen-firefox

$ npm install

$ node ./index.js
```

The certificate files will be dumped in the CWD. You can then:

- Install and trust it locally
- Copy the cert your parcel project `.cache` directory
- Restart your parcal server, if required
- Visit https://127.0.0.1:1234 to test. You may need to restart Firefox.