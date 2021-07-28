# Schnorr Signatures

[![forthebadge](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNjEuNTgiIGhlaWdodD0iMzUiIHZpZXdCb3g9IjAgMCAxNjEuNTggMzUiPjxyZWN0IGNsYXNzPSJzdmdfX3JlY3QiIHg9IjAiIHk9IjAiIHdpZHRoPSI5Ny43MTAwMDAwMDAwMDAwMSIgaGVpZ2h0PSIzNSIgZmlsbD0iI0U0NkMxNyIvPjxyZWN0IGNsYXNzPSJzdmdfX3JlY3QiIHg9Ijk1LjcxMDAwMDAwMDAwMDAxIiB5PSIwIiB3aWR0aD0iNjUuODciIGhlaWdodD0iMzUiIGZpbGw9IiNEMzVCMDkiLz48cGF0aCBjbGFzcz0ic3ZnX190ZXh0IiBkPSJNMTcuMzMgMjJMMTQuMjIgMjJMMTQuMjIgMTMuNDdMMTcuMTQgMTMuNDdRMTguNTkgMTMuNDcgMTkuMzQgMTQuMDVRMjAuMTAgMTQuNjMgMjAuMTAgMTUuNzhMMjAuMTAgMTUuNzhRMjAuMTAgMTYuMzYgMTkuNzggMTYuODNRMTkuNDcgMTcuMzAgMTguODYgMTcuNTZMMTguODYgMTcuNTZRMTkuNTUgMTcuNzUgMTkuOTMgMTguMjZRMjAuMzEgMTguNzggMjAuMzEgMTkuNTFMMjAuMzEgMTkuNTFRMjAuMzEgMjAuNzEgMTkuNTMgMjEuMzZRMTguNzYgMjIgMTcuMzMgMjJMMTcuMzMgMjJaTTE1LjcwIDE4LjE1TDE1LjcwIDIwLjgyTDE3LjM1IDIwLjgyUTE4LjA0IDIwLjgyIDE4LjQ0IDIwLjQ3UTE4LjgzIDIwLjEzIDE4LjgzIDE5LjUxTDE4LjgzIDE5LjUxUTE4LjgzIDE4LjE4IDE3LjQ3IDE4LjE1TDE3LjQ3IDE4LjE1TDE1LjcwIDE4LjE1Wk0xNS43MCAxNC42NkwxNS43MCAxNy4wNkwxNy4xNSAxNy4wNlExNy44NCAxNy4wNiAxOC4yMyAxNi43NVExOC42MiAxNi40MyAxOC42MiAxNS44NkwxOC42MiAxNS44NlExOC42MiAxNS4yMyAxOC4yNiAxNC45NVExNy45MCAxNC42NiAxNy4xNCAxNC42NkwxNy4xNCAxNC42NkwxNS43MCAxNC42NlpNMjQuNjQgMTkuMTZMMjQuNjQgMTkuMTZMMjQuNjQgMTMuNDdMMjYuMTIgMTMuNDdMMjYuMTIgMTkuMThRMjYuMTIgMjAuMDMgMjYuNTUgMjAuNDhRMjYuOTggMjAuOTMgMjcuODMgMjAuOTNMMjcuODMgMjAuOTNRMjkuNTQgMjAuOTMgMjkuNTQgMTkuMTNMMjkuNTQgMTkuMTNMMjkuNTQgMTMuNDdMMzEuMDIgMTMuNDdMMzEuMDIgMTkuMTdRMzEuMDIgMjAuNTMgMzAuMTUgMjEuMzJRMjkuMjggMjIuMTIgMjcuODMgMjIuMTJMMjcuODMgMjIuMTJRMjYuMzYgMjIuMTIgMjUuNTAgMjEuMzNRMjQuNjQgMjAuNTUgMjQuNjQgMTkuMTZaTTM3LjE1IDIyTDM1LjY3IDIyTDM1LjY3IDEzLjQ3TDM3LjE1IDEzLjQ3TDM3LjE1IDIyWk00Ny4zMiAyMkw0MS45NiAyMkw0MS45NiAxMy40N0w0My40NCAxMy40N0w0My40NCAyMC44Mkw0Ny4zMiAyMC44Mkw0Ny4zMiAyMlpNNTMuMTIgMTQuNjZMNTAuNDkgMTQuNjZMNTAuNDkgMTMuNDdMNTcuMjUgMTMuNDdMNTcuMjUgMTQuNjZMNTQuNTkgMTQuNjZMNTQuNTkgMjJMNTMuMTIgMjJMNTMuMTIgMTQuNjZaTTcwLjEwIDIyTDY2Ljk5IDIyTDY2Ljk5IDEzLjQ3TDY5LjkxIDEzLjQ3UTcxLjM2IDEzLjQ3IDcyLjExIDE0LjA1UTcyLjg3IDE0LjYzIDcyLjg3IDE1Ljc4TDcyLjg3IDE1Ljc4UTcyLjg3IDE2LjM2IDcyLjU1IDE2LjgzUTcyLjI0IDE3LjMwIDcxLjYzIDE3LjU2TDcxLjYzIDE3LjU2UTcyLjMyIDE3Ljc1IDcyLjcwIDE4LjI2UTczLjA3IDE4Ljc4IDczLjA3IDE5LjUxTDczLjA3IDE5LjUxUTczLjA3IDIwLjcxIDcyLjMwIDIxLjM2UTcxLjUzIDIyIDcwLjEwIDIyTDcwLjEwIDIyWk02OC40NyAxOC4xNUw2OC40NyAyMC44Mkw3MC4xMiAyMC44MlE3MC44MSAyMC44MiA3MS4yMSAyMC40N1E3MS42MCAyMC4xMyA3MS42MCAxOS41MUw3MS42MCAxOS41MVE3MS42MCAxOC4xOCA3MC4yNCAxOC4xNUw3MC4yNCAxOC4xNUw2OC40NyAxOC4xNVpNNjguNDcgMTQuNjZMNjguNDcgMTcuMDZMNjkuOTIgMTcuMDZRNzAuNjEgMTcuMDYgNzEuMDAgMTYuNzVRNzEuMzkgMTYuNDMgNzEuMzkgMTUuODZMNzEuMzkgMTUuODZRNzEuMzkgMTUuMjMgNzEuMDMgMTQuOTVRNzAuNjcgMTQuNjYgNjkuOTEgMTQuNjZMNjkuOTEgMTQuNjZMNjguNDcgMTQuNjZaTTc5LjU4IDE4Ljg2TDc2LjcyIDEzLjQ3TDc4LjM3IDEzLjQ3TDgwLjMzIDE3LjUxTDgyLjI5IDEzLjQ3TDgzLjkzIDEzLjQ3TDgxLjA3IDE4Ljg2TDgxLjA3IDIyTDc5LjU4IDIyTDc5LjU4IDE4Ljg2WiIgZmlsbD0iI0ZGRkZGRiIvPjxwYXRoIGNsYXNzPSJzdmdfX3RleHQiIGQ9Ik0xMTIuMjggMjJMMTA5LjkwIDIyTDEwOS45MCAxMy42MEwxMTYuNDkgMTMuNjBMMTE2LjQ5IDE1LjQ0TDExMi4yOCAxNS40NEwxMTIuMjggMTcuMjhMMTE1Ljk5IDE3LjI4TDExNS45OSAxOS4xMkwxMTIuMjggMTkuMTJMMTEyLjI4IDIyWk0xMjIuNTAgMjJMMTIwLjA4IDIyTDEyMy43OCAxMy42MEwxMjYuMTMgMTMuNjBMMTI5Ljg0IDIyTDEyNy4zOCAyMkwxMjYuNzEgMjAuMzdMMTIzLjE2IDIwLjM3TDEyMi41MCAyMlpNMTI0Ljk0IDE1LjkzTDEyMy44NSAxOC42MUwxMjYuMDIgMTguNjFMMTI0Ljk0IDE1LjkzWk0xMzcuOTcgMjJMMTM0LjAwIDIyTDEzNC4wMCAxMy42MEwxMzcuOTcgMTMuNjBRMTM5LjM1IDEzLjYwIDE0MC40MiAxNC4xMlExNDEuNDkgMTQuNjMgMTQyLjA3IDE1LjU4UTE0Mi42NiAxNi41MyAxNDIuNjYgMTcuODBMMTQyLjY2IDE3LjgwUTE0Mi42NiAxOS4wNyAxNDIuMDcgMjAuMDJRMTQxLjQ5IDIwLjk3IDE0MC40MiAyMS40OFExMzkuMzUgMjIgMTM3Ljk3IDIyTDEzNy45NyAyMlpNMTM2LjM4IDE1LjUwTDEzNi4zOCAyMC4xMEwxMzcuODggMjAuMTBRMTM4Ljk1IDIwLjEwIDEzOS42MSAxOS40OVExNDAuMjYgMTguODggMTQwLjI2IDE3LjgwTDE0MC4yNiAxNy44MFExNDAuMjYgMTYuNzIgMTM5LjYxIDE2LjExUTEzOC45NSAxNS41MCAxMzcuODggMTUuNTBMMTM3Ljg4IDE1LjUwTDEzNi4zOCAxNS41MFpNMTQ5Ljc3IDIyTDE0Ny4zOSAyMkwxNDcuMzkgMTMuNjBMMTQ5Ljc3IDEzLjYwTDE0OS43NyAyMloiIGZpbGw9IiNGRkZGRkYiIHg9IjEwOC43MTAwMDAwMDAwMDAwMSIvPjwvc3ZnPg==)](https://forthebadge.com)

This is a **Schnorr signatures utility** for *educational purposes* only, developed by Fadi Barbara ([@disnocen](https://github.com/disnocen)) and published by BIT PoliTO.

## Scripts

There are four scripts:

- #### Key pair creator
`create_keypair.py` asks for a sentence (no newline characters), SHA256 hashes it and then creates a key pair which can be used to `schnorr_sign` and `schnorr_verify` a message.

- #### Schnorr signer
`schnorr_sign.py` returns the signature and the public key from a private key and a message. <br>
See `python schnorr_sign.py -h` for the syntax.

- #### Schnorr verifier
`schnorr_verify.py` returns `True` or `False` from a public key, a message and a signature. <br>
See `python schnorr_verify.py -h` for the syntax.

- #### Schnorr tester
`schnorr_test.py` is the BIP340 reference implementation minimally changed to perform a test from the `test-vector.csv`. <br>
See <https://github.com/bitcoin/bips/blob/master/bip-0340.mediawiki> and the reference implementation at <https://github.com/bitcoin/bips/tree/master/bip-0340>.

Both the scripts `schnorr_sign.py` and `schnorr_verify.py` are taken from the reference implementation. 

The script `create_keypair.py` should not be used in production environments because it is not secure enough.

The functions used in those scripts are collected in the library `schnorr_lib.py`.

## How to install and run code
### Installation

```console
# clone the repo
$ git clone https://github.com/BITPoliTO/schnorr-sig.git

# change the working directory to schnorr-sig
$ cd schnorr-sig

# install general requirements
$ pip install typing 
```

### Run
```console
$ python create_keypair.py
$ python schnorr_sign.py -s <secret_key> -m <message>
$ python schnorr_verify.py -s <signature> -p <public_key> -m <message>
```

#### Made to educate the BIT PoliTO team 🎓 by  
  
<a href="https://github.com/BITPoliTO/schnorr-sig/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=bitpolito/schnorr-sig" />
</a>
