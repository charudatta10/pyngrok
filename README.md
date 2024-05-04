<p align="center"><img alt="pyngrok - a Python wrapper for ngrok" src="https://pyngrok.readthedocs.io/en/latest/_images/logo.png" /></p>

[![Version](https://img.shields.io/pypi/v/pyngrok)](https://pypi.org/project/pyngrok)
[![Python Versions](https://img.shields.io/pypi/pyversions/pyngrok.svg)](https://pypi.org/project/pyngrok)
[![Coverage](https://img.shields.io/codecov/c/github/alexdlaird/pyngrok)](https://codecov.io/gh/alexdlaird/pyngrok)
[![Build](https://img.shields.io/github/actions/workflow/status/alexdlaird/pyngrok/build.yml)](https://github.com/alexdlaird/pyngrok/actions/workflows/build.yml)
[![Docs](https://img.shields.io/readthedocs/pyngrok)](https://pyngrok.readthedocs.io/en/latest)
[![GitHub License](https://img.shields.io/github/license/alexdlaird/pyngrok)](https://github.com/alexdlaird/pyngrok/blob/main/LICENSE)

`pyngrok` is a Python wrapper for `ngrok` that manages its own binary, making `ngrok` available via a convenient Python
API.

[`ngrok`](https://ngrok.com) is a reverse proxy tool that opens secure tunnels from public URLs to localhost, perfect
for exposing local web servers, building webhook integrations, enabling SSH access, testing chatbots, demoing from
your own machine, and more, and its made even more powerful with native Python integration through `pyngrok`.

## Installation

`pyngrok` is available on [PyPI](https://pypi.org/project/pyngrok/) and can be installed
using `pip`:

```sh
pip install pyngrok
```

or `conda`:

```sh
conda install -c conda-forge pyngrok
```

That's it! `pyngrok` is now available as a package to our Python projects, and `ngrok` is now available from
the command line.

## Basic Usage

To open a tunnel, use the [`connect`](https://pyngrok.readthedocs.io/en/latest/api.html#pyngrok.ngrok.connect) method,
which returns a `NgrokTunnel`, and this returned object has a reference to the public URL generated by `ngrok` in its
`public_url` attribute.

```python
from pyngrok import ngrok

# Open a HTTP tunnel on the default port 80
# <NgrokTunnel: "https://<public_sub>.ngrok.io" -> "http://localhost:80">
http_tunnel = ngrok.connect()

# Open a SSH tunnel
# <NgrokTunnel: "tcp://0.tcp.ngrok.io:12345" -> "localhost:22">
ssh_tunnel = ngrok.connect("22", "tcp")

# Open a named tunnel from the config file
named_tunnel = ngrok.connect(name="my_tunnel_name")
```

The [`connect`](https://pyngrok.readthedocs.io/en/latest/api.html#pyngrok.ngrok.connect) method takes `kwargs` as
well, which allows us to pass additional properties that
are [supported by `ngrok`](https://ngrok.com/docs/secure-tunnels/ngrok-agent/reference/config/#tunnel-definitions).

This package puts the default `ngrok` binary on our path, so all features of `ngrok` are
available on the command line.

```sh
ngrok http 80
```

For details on how to fully leverage `ngrok` from the command line,
see [`ngrok`'s official documentation](https://ngrok.com/docs).

## Documentation

For more advanced usage, `pyngrok`'s official documentation is available
at [http://pyngrok.readthedocs.io](http://pyngrok.readthedocs.io).

### `ngrok` Version Compatibility

`pyngrok` is compatible with `ngrok` v2 and v3, but by default it will install v3. To install v2 instead,
[set `ngrok_version` to "v2" in `PyngrokConfig`](https://pyngrok.readthedocs.io/en/latest/index.html#ngrok-version-compatibility).

## Contributing

If you would like to get involved, be sure to review
the [Contribution Guide](https://github.com/alexdlaird/pyngrok/blob/main/CONTRIBUTING.rst).

Want to contribute financially? If you've found `pyngrok` useful, [sponsorship](https://github.com/sponsors/alexdlaird)
would
also be greatly appreciated!
