> Authors

## What is Protex?

**Portex** is a novel accountable decryption system. We extend such a research direction: *using a trusted hardware-based log to make decryption accountable*, but we consider the risk of the compromised trusted hardware and introduce a tracing mechanism. In our scheme, the decryption key is sealed in the trusted hardware (e.g., Trusted Execution Environment), and each decryption will trigger an automatic update of the transparent log. Then, a tracer can check the log to show evidence of users' misbehaviours of decryption. Meanwhile, the tracing mechanism ensures TEE's action of the key generation or key distribution accountable. Our systems have several immediate applications, covering:
