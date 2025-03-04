# UV Virtual Environment

#### Install UV:
```bash
pip install uv
```

#### Create a virtual environment at `.venv`:
```bash
uv venv
```

#### Activate the virtual environment on Windows (if you use the above command):
```bash
source .venv/Scripts/activate
```

#### Create a virtual environment with a specific name, e.g., `my-name`:
```bash
uv venv <my_venv>
```

#### Activate the virtual environment on Windows:
```bash
source <my_venv>/Scripts/activate
```

#### Install a package into the virtual environment:
```bash
uv pip install <package_name>
```

#### Install a package at a specific version, e.g., Ruff v0.3.0:
```bash
uv pip install 'ruff==0.3.0'
```

#### Install from a `requirements.txt` file:
```bash
uv pip install -r requirements.txt
```

#### Uninstall a package:
```bash
uv pip uninstall <package_name>
```

#### List all packages in the virtual environment:
```bash
uv pip list
```

#### To deactivate an environment:
```bash
deactivate
```

#### To automatically generate requirements.txt
```bash
uv pip freeze > requirements.txt
```

#### Project Structure
```
my_project/
├── .venv/              # Virtual environment directory (contains Python binaries and libraries)
├── app.py              # Main application file (your Python code)
├── requirements.txt    # List of dependencies for the project
└── README.md           # Documentation for the project
```
