<head>
    <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
    <script type="text/x-mathjax-config">
        MathJax.Hub.Config({
            tex2jax: {
            skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
            inlineMath: [['$','$']]
            }
        });
    </script>
    <style type="text/css">
        .container3 {
            width: 400px;
            height: 400px;
        }
        .row3 {
            display: flex;
            height: 50%;
        }
        .column3 {
            flex: 1;
            background: brown;
            margin-left: 10px;
            margin-top: 10px;
        }
    </style>
</head>

> 2022/7/26

## What is **Portex**?

**Portex** is a novel accountable decryption system. We extend such a research direction: *using a trusted
hardware-based log to make decryption accountable*, but we consider the risk of the compromised trusted hardware and
introduce a tracing mechanism. In our scheme, the decryption key is sealed in the trusted hardware (e.g., Trusted
Execution Environment), and each decryption will trigger an automatic update of the transparent log. Then, a tracer can
check the log to show evidence of users' misbehaviours of decryption. Meanwhile, the tracing mechanism ensures TEE's
action of the key generation or key distribution accountable.

## Contributions

- We propose a practical accountable cryptosystems, in which the users are accountable for their decryption. Each
  decryption will be faithfully recorded by the log maintainer, whose actions are publicly verifiable.

- Our proposed scheme relies on TEE, but we further take consider the mainstream vulnerability of TEE that may leak the
  users' private keys and destroy accountability. We accordingly design a tracing mechanism to make trusted hardware,
  additionally, accountable for the private key generation and distribution.
- We formalize the syntax and security definitions of **Portex**. The formal security analyses indicate that our system
  is provably secure, which satisfies the properties of *key privacy*, *fairness*, *completeness*, and *TEE
  traceability*.

- We provide a full-functional implementation for **Portex** and evaluate performance in terms of *theoretical
  complexity*, *running time*, and *log size* for major functionalities. The experimental results demonstrate the
  feasibility and efficiency of our system.

## Designs

In **Portex**, four types of entities are involved: *private key generator* $\mathsf{PKG}$, a *log manager*
$\mathsf{LM}$, and user clients $\mathsf{CLIENTS}$ and tracers $\mathsf{TRACERS}$. The $\mathsf{PKG}$ is required to run
inside TEEs. The log manager and users' platforms do not necessarily to support TEEs. Similar to the standard IBE
system, the $\mathsf{PKG}$ is responsible for generating the public parameters and extracting and distributing the
user's private key. User clients $\mathsf{CLIENTS}$ are used to perform the decryption of ciphertext. The $\mathsf{LM}$
updates and stores the logs when $\mathsf{PKG}$ distributes a private key. $\mathsf{TRACERS}$ that any roles can serve
are responsible for detecting the wrongdoing of $\mathsf{CLIENTS}$ and the TEE-based $\mathsf{PKG}$ and users. The main
idea behind **Portex** is to run $\mathsf{PKG}$ inside a TEE and force the action of key generation to render a public
auditable log.

<img src="assets/image-20220726180341133.png" alt="image-20220726180341133" style="zoom: 40%;" />

## Implementation

The implementation is published in [Portex-tee/Portex (github.com)](https://github.com/Portex-tee/Portex)

Here we present the functions:


<div class="container3">
    <div class="row3">
        <div class="column3"><p></p></div>
        <div class="column3"><p></p></div>
    </div>
    <div class="row3">
        <div class="column3"><p></p></div>
        <div class="column3"><p></p></div>
    </div>
</div>

<div class="container3">
    <div class="row3">
        <div class="column3"><p></p></div>
            <video width="450" height="300" src="media/keyreq.mkv"  type="video/mp4"><p></p></video>
        <div class="column3"><p></p></div>
        <div class="column3"><p></p></div>
            <video width="450" height="300" src="media/keygen.mkv" type="video/mp4"><p></p></video>
        <div class="column3"><p></p></div>
    </div>
    <div class="row3">
        <div class="column3"><p></p></div>
            <video width="450" height="300" src="media/encrypt.mkv" type="video/mp4"><p></p></video>
        <div class="column3"><p></p></div>
        <div class="column3"><p></p></div>
            <video width="450" height="300" src="media/decrypt.mkv" type="video/mp4"><p></p></video>
        <div class="column3"><p></p></div>
    </div>
</div>

### Key Request

<video width="900" height="600" src="media/keyreq.mkv"  type="video/mp4"></video>

### Key Generation

<video width="900" height="600" src="media/keygen.mkv" type="video/mp4"></video>

### Encryption

<video width="900" height="600" src="media/encrypt.mkv" type="video/mp4"></video>

### Decryption

