# Mint via WebAuthn

You can mint a PKP by presenting a valid WebAuthn credential generated by your browser to the Lit Relay server. 

We have a frontend that helps with this process at https://lit-pkp-auth-demo.vercel.app/.

We currently support both username-based and username-less WebAuthn registration, and usernames are purely used for your convenience / reference on the client-side.

## Technical Details

### Contract Specifics

- The `authMethodId` is derived from the credential's [rawId](https://www.w3.org/TR/webauthn-2/#dom-publickeycredential-rawid) parameter.
- The `authMethodPubkey` is the [COSE credential public key](https://datatracker.ietf.org/doc/html/rfc8812). **We currently only support Elliptic Curve COSE Key Type IDs**.

### Relying Parties and Supported Origins

In order to allow for various frontends to integrate with our platform, we plan to support any domain to act as a [Relying Party](https://www.w3.org/TR/webauthn-2/#webauthn-relying-party) in the long run. However, we are in the process of slowly rolling out this authentication method currently maintain an allowlist of origins / domains that can integrate with the Lit network.

### Challenge-Free Registration

We do not currently use challenges as part of our PKP minting / WebAuthn registration process and only use it for the PKP / WebAuthn authentication step.