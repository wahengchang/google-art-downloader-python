# GAP decoder

This project aims at making it possible to download images from
[google art and culture](https://artsandculture.google.com/)
(formerly Google Art Project).

## How to use


First, install [python 3](https://www.python.org/) on your system,
and install the dependencies:

```bash
# python3 -m venv venv
pip3 install -r requirements.txt 
```

Then, run the code

```bash
python3 tile_fetch.py --zoom 5 "https://artsandculture.google.com/asset/the-water-carrier-la-aguadora/UwE2fGsMlWHuMg"
```

You can of course change the zoom level and the URL.
If you omit the zoom level, the script will display the list of available levels.

## Technical details

This project required reverse-engineering google's code to find 
the protection measures in place and circumvent them.
Here is what was found.

### Tile URLs

The tile URLs are signed using HMAC.
[See the details](./tile_fetch.py)

### Tile images

The tile images are encoded using AES 128 CBC.
[See the details](./decryption.py)