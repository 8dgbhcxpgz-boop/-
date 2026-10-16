# V3 minimal reproducible trial
Primary upstream: https://github.com/fashn-AI/fashn-vton-1.5

## Setup (NVIDIA GPU recommended)
git clone https://github.com/fashn-AI/fashn-vton-1.5.git
cd fashn-vton-1.5
python -m venv .venv
source .venv/bin/activate
pip install -e .
Download model weights following upstream README (approximately 2 GB).

## First baseline
python examples/basic_inference.py --weights-dir ./weights --person-image /path/person.png --garment-image /path/dress.png --category one-pieces

Use upstream's current CLI help if flags change. Do not treat this command as executed or tested by this repository.

## Validation protocol
Start with dress only. Then optionally try top followed by dress, comparing whether collar/sleeves survive. Two garments, new scene, handbag and shoes are outside the proven single-garment baseline. Keep a fixed input and seed for comparisons. Log native dimensions and upscale separately.

## License
V3 instructions are original; upstream model Apache-2.0. Verify all third-party dependencies, source images, branding rights, and weights before commercial deployment.
