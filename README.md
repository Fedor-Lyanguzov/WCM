# WireGuard config manager (WCM)

Manage WireGuard VPN peers (both server and clients)

## Usage

```bash
# networks
wcm network add test
wcm network add with-ip --address=10.0.0.2/24
wcm network delete with-ip
wcm network add no-preshared --no-preshared-key
wcm network show

# peers
wcm peer add temp
wcm peer add server --to-network test --pass-thru=0.0.0.0/0 --port=59
wcm peer add alice --to-network test --address=10.0.0.150
wcm peer add bob --with-pk=wireguardprivatekey=
wcm connect bob test
wcm disconnect bob all
wcm peer remove alice from network test
wcm peer delete alice
wcm peer show

# config
wcm config make test
wcm config make all
wcm config make test --output-dir=~/vpn-configs
wcm config load ~/vpn-configs/old

# Delete database
wcm database delete

# development crud
```

## Development

To start developing:

```bash
python -m venv .venv
source .venv/Scripts/activate
pip install -e .[test,lint]
# work related commands here
deactivate
```

Tools:

```bash
pytest
flake8 wcm
black wcm
```

Test runs:

```bash
# script declared in pyproject.toml
$ example
run
```
