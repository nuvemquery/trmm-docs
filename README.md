# Building with Docker

```
git clone https://github.com/nuvemquery/trmm-docs.git
cd trmm-docs
./build.sh
```

# Building standard

```
git clone https://github.com/nuvemquery/trmm-docs.git
cd trmm-docs
python3 -m venv env
source env/bin/activate
pip install --upgrade pip
pip install --upgrade setuptools wheel
pip install -r requirements.txt
mkdocs serve
```

Browse to http://your-server-ip:8005

[Understanding python and running stuff](https://docs.tacticalrmm.com/devnotes/running_tests_locally/)

# Running from vscode

Open repo

Choose Run > Run Without Debugging
