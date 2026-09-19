# Sublist3r Python 3

A Python 3-compatible modernization of the legacy Sublist3r v1.0
subdomain-enumeration script.

## Requirements

- Python 3.8 or newer
- The packages listed in `requirements.txt`

Install the runtime dependency with:

```bash
python3 -m venv .venv
. .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

## Usage

Display the available options:

```bash
python3 sublist3r.py --help
```

Enumerate subdomains for a domain:

```bash
python3 sublist3r.py --domain example.com
```

Save results to a file and suppress terminal colors:

```bash
python3 sublist3r.py --domain example.com --output results.txt --no-color
```

Choose specific passive sources:

```bash
python3 sublist3r.py --domain example.com \
  --engines google,bing,ssl,passivedns
```

Enable verbose output:

```bash
python3 sublist3r.py --domain example.com --verbose
```

Scan selected TCP ports on discovered subdomains:

```bash
python3 sublist3r.py --domain example.com --ports 80,443
```

## Brute-force mode

The `--bruteforce` option requires the original `subbrute` package and its
`subbrute/names.txt` and `subbrute/resolvers.txt` data files to be present
beside `sublist3r.py`. It is intentionally optional and is not needed for
passive enumeration.

```bash
python3 sublist3r.py --domain example.com --bruteforce --threads 30
```

## Notes

- Search-engine HTML layouts and third-party endpoints can change over time,
  so individual sources may stop returning results even though the script
  itself runs correctly.
- Run enumeration and port scanning only against domains and systems you own
  or are explicitly authorized to assess.
