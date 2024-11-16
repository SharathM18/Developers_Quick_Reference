# UV Virtual Environment

#### Install UV:
```bash
pip install uv
```

#### Create a virtual environment at `.venv`:
```bash
uv venv
```

#### Create a virtual environment with a specific name, e.g., `my-name`:
```bash
uv venv my-name
```

#### Activate the virtual environment on Windows:
```bash
source .venv/Scripts/activate
```

#### Install a package into the virtual environment, e.g., Flask:
```bash
uv pip install flask
```

#### Install a package at a specific version, e.g., Ruff v0.3.0:
```bash
uv pip install 'ruff==0.3.0'
```

#### Install from a `requirements.txt` file:
```bash
uv pip install -r requirements.txt
```

#### Uninstall a package, e.g., Flask:
```bash
uv pip uninstall flask
```

#### List all packages in the virtual environment:
```bash
uv pip list
```

#### To deactivate an environment:
```bash
deactivate
```

#### Project Structure
```
my_project/
├── .venv/              # Virtual environment directory (contains Python binaries and libraries)
├── app.py              # Main application file (your Python code)
├── requirements.txt    # List of dependencies for the project
└── README.md           # Documentation for the project
```
