# My CryptoHack Solutions

My solutions to the challenges on [CryptoHack](https://cryptohack.org/), a free platform for learning modern
cryptography by solving puzzles and breaking flawed implementations.

Each notebook covers one CryptoHack course. Every challenge comes with a short explanation of the
underlying concept or vulnerability, followed by a self-contained Python solution.

> **Spoiler warning:** these notebooks contain full solutions and flags. If you are working through CryptoHack
> yourself, try the challenges first. You will learn much more that way.

> **Work in progress:** I am still writing up my solutions, so not every CryptoHack course or challenge appears
> here. A missing notebook or challenge either means I have not covered it yet, or that I did not consider it
> worth including.

## Highlights

- [**Elliptic curve attacks**](notebooks/05_elliptic_curves.ipynb): Pohlig-Hellman on smooth-order curves,
  Smart's attack on anomalous curves, the MOV attack, singular curves, a lattice attack on ECDSA with biased nonces,
  and power analysis of double-and-add
- [**AES from scratch**](notebooks/03_symmetric_ciphers.ipynb), cross-checked against PyCryptodome, followed by
  attacks on block cipher modes: ECB byte-at-a-time, CBC bit flipping, IV reused as the key, keystream reuse
- [**Number theory**](notebooks/02_mathematics.ipynb): Tonelli-Shanks and Gaussian lattice reduction implemented by hand
- [**Diffie-Hellman man-in-the-middle**](notebooks/04_diffie_hellman.ipynb): parameter injection and a Logjam-style downgrade attack

## Contents

| Notebook | Course | Topics |
| --- | --- | --- |
| [01_general](notebooks/01_general.ipynb) | General | Encodings, XOR, GCD and Bézout coefficients, PEM/DER key formats |
| [02_mathematics](notebooks/02_mathematics.ipynb) | Mathematics | Quadratic residues, Legendre symbol, Tonelli-Shanks, CRT, Gram-Schmidt, Gaussian lattice reduction |
| [03_symmetric_ciphers](notebooks/03_symmetric_ciphers.ipynb) | Symmetric Ciphers | AES from scratch, dictionary attack, ECB byte-at-a-time, CBC bit flipping, IV = key, keystream reuse |
| [04_diffie_hellman](notebooks/04_diffie_hellman.ipynb) | Diffie-Hellman | Group generators, key derivation, parameter injection, downgrade attack |
| [05_elliptic_curves](notebooks/05_elliptic_curves.ipynb) | Elliptic Curves | Point arithmetic, Pohlig-Hellman, Smart's attack, MOV attack, singular curves, real curves and LLL, CurveBall, weak ECDSA nonces, side channels |

<details>
<summary>Full list of solved challenges</summary>

- **General**
  - *Encoding:* ASCII, Hex, Base64, Bytes and Big Integers, Encoding Challenge
  - *XOR:* XOR Starter, XOR Properties, Favourite byte, You either know, XOR you don't, Lemur XOR
  - *Mathematics:* Greatest Common Divisor, Extended GCD, Modular Arithmetic 1
  - *Data Formats:* Privacy-Enhanced Mail?, CERTainly not
- **Mathematics**
  - *Modular Math:* Quadratic Residues, Legendre Symbol, Modular Square Root, Chinese Remainder Theorem
  - *Lattices:* Gram Schmidt, What's a Lattice?, Gaussian Reduction
  - *Brainteasers Part 1:* Adrien's Signs, Modular Binomials
- **Symmetric Ciphers**
  - *How AES Works:* Structure of AES, Round Keys, Confusion through Substitution, Diffusion through Permutation, Bringing It All Together
  - *Symmetric Starter:* Modes of Operation Starter, Passwords as Keys
  - *Block Ciphers 1:* ECBCBCWTF, ECB Oracle, Flipping Cookie, Lazy CBC
  - *Stream Ciphers:* Symmetry, Bean Counter
- **Diffie-Hellman**
  - *Starter:* Working with Fields, Generators of Groups, Computing Public Values, Computing Shared Secrets, Deriving Symmetric Keys
  - *Man In The Middle:* Parameter Injection, Export-grade
- **Elliptic Curves**
  - *Starter:* Point Negation, Point Addition, Scalar Multiplication, Curves and Logs, Efficient Exchange
  - *Parameter Choice:* Smooth Criminal, Exceptional Curves, Micro Transmissions, Elliptic Nodes, Moving Problems
  - *Parameter Choice 2:* Real Curve Crypto
  - *Signatures:* Digestive, Curveball, ProSign 3, No Random, No Bias
  - *Edwards Curves:* Edwards Goes Degenerate
  - *Side Channels:* Montgomery's Ladder, Double and Broken

</details>

## Repository layout

```
.
├── notebooks/
│   ├── 01_general.ipynb ... 05_elliptic_curves.ipynb
│   ├── files/      # challenge files provided by CryptoHack (images, keys, certificates, outputs)
│   └── output/     # files generated when running the notebooks (git-ignored)
├── requirements.txt
└── README.md
```

## Running the notebooks

Requires Python 3.10 or newer.

```bash
git clone https://github.com/rmnbm/my-cryptohack-solutions.git
cd cryptohack
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook notebooks/
```

Run the notebooks from the `notebooks/` directory, since challenge files are loaded with relative paths.

Some solutions talk to live services, so they need an Internet connection:
`socket.cryptohack.org`, `aes.cryptohack.org` and `web.cryptohack.org` for the interactive challenges.

## Libraries used

- [PyCryptodome](https://www.pycryptodome.org/): AES, RSA key parsing, integer/byte conversions
- [PARI/GP](https://pari.math.u-bordeaux.fr/) via [cypari2](https://github.com/sagemath/cypari2): elliptic curve point counting, extension fields, pairings, LLL
- [pwntools](https://docs.pwntools.com/): socket connections and XOR helpers
- [SymPy](https://www.sympy.org/): modular square roots, prime factors, discrete logarithms
- [NumPy](https://numpy.org/) and [Pillow](https://python-pillow.org/): linear algebra and image manipulation
- [Requests](https://requests.readthedocs.io/): HTTP challenge APIs

## Acknowledgements

All challenges are created and hosted by the [CryptoHack](https://cryptohack.org/) team.
The helper functions marked as "provided by the challenge" in the notebooks come from the challenge source files.
