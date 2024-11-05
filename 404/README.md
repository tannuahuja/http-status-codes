# Simulate 404 - Not Found and Fix it

## Create virtual environment

```bash
python3 -m venv myenv

# Activate the virtual environment
# On Windows
myenv\Scripts\activate

# On macOS/Linux
source myenv/bin/activate
```

## Install dependencies

```bash
pip install -r requirements.txt
```

## Run the flask application

```bash
python3 not_found.py
```

### Verify using CURL

```bash
curl -i http://127.0.0.1:5000/
```