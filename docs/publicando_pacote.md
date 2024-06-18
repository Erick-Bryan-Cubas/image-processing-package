# Orientações para publicação de pacotes Python

## 1. Crie uma conta no PyPI e no TestPyPI

Para publicar um pacote no PyPI, é necessário criar uma conta no site. Para isso, acesse o site [https://pypi.org/account/register/](https://pypi.org/account/register/) e o site [https://test.pypi.org/account/register/](https://test.pypi.org/account/register/) para criar uma conta no TestPyPI.

## 2. Instale o pacote twine, setuptools e wheel

Para publicar um pacote no PyPI, é necessário instalar o pacote twine, setuptools e wheel. Para isso, execute o comando:

```bash
pip install twine setuptools wheel
```

## 3. Crie um arquivo setup.py

O arquivo setup.py é responsável por configurar o pacote Python. Abaixo, um exemplo de arquivo setup.py:

```python
from setuptools import setup

setup(
    name='image_processing',
    version='0.1',
    packages=['image_processing'],
    install_requires=[
        'numpy',
        'matplotlib',
        'scikit-image',
    ],
    author='Erick Bryan Cubas',

    # Descrição do pacote
    description='The package image_processing is used to: Processing: Histogram matching, Structural similarity. Utils: Read image, Save image, Plot image, Plot result',
    long_description=open('README.md').read(),
    long_description_content_type='text/markdown',

    # URL do repositório
    url='',
    license='MIT',
)
```

## 4. Crie um arquivo README.md

O arquivo README.md é responsável por descrever o pacote Python. Abaixo, um exemplo de arquivo README.md.

## 5. Crie um arquivo MANIFEST.in

O arquivo MANIFEST.in é responsável por incluir arquivos adicionais no pacote Python. Abaixo, um exemplo de arquivo MANIFEST.in.

```bash
include README.md
```

## 6. Crie um arquivo .pypirc

O arquivo .pypirc é responsável por configurar o acesso ao PyPI e ao TestPyPI. Abaixo, um exemplo de arquivo .pypirc. Deve ser criado na pasta do usuário.

Se no Windows, o arquivo deve ser criado em `C:\Users\username\.pypirc`.
Se no Linux, o arquivo deve ser criado em `/home/username/.pypirc`.

```bash
[distutils]
index-servers =
    pypi
    testpypi

[pypi]
repository: https://upload.pypi.org/legacy/
username: __token__
password: pypi-<token>

[testpypi]
repository: https://test.pypi.org/legacy/
username: __token__
password: pypi-<token>
```

## 7. Crie um arquivo .gitignore

O arquivo .gitignore é responsável por ignorar arquivos e pastas no repositório Git. Abaixo, um exemplo de arquivo .gitignore.

```bash
__pycache__/
*.pyc
*.pyo
*.pyd
*.pyw
*.pyz
*.pyzw
*.pyc
*.pyo
*.pyd
*.pyw
*.pyz
*.pyzw
*.egg-info
dist/
build/
```

## 8. Crie um arquivo LICENSE

O arquivo LICENSE é responsável por definir a licença do pacote Python. Abaixo, um exemplo de arquivo LICENSE.

## 9. Crie um arquivo .gitattributes

O arquivo .gitattributes é responsável por definir atributos do repositório Git. Abaixo, um exemplo de arquivo .gitattributes.

```bash
*.md text
*.txt text
*.py text
*.sh text
*.bat text
*.cmd text
*.cfg text
*.conf text
*.ini text
*.json text
*.yml text
*.yaml text
*.xml text
*.html text
*.css text
*.js text
*.ts text
*.scss text
*.less text
*.php text
*.java text
*.c text
*.cpp text
*.h text
*.hpp text
*.cs text
*.go text
*.rs text
*.pl text
*.pm text
*.tcl text
*.r text
*.rb text
*.lua text
*.sh text
*.bash text
*.zsh text
*.awk text
*.ps1 text
*.psm1 text
*.psd1 text
*.ps1xml text
*.pssc text
*.psc1 text
*.psc2 text
*.dll binary
*.exe binary
*.so binary
*.dylib binary
*.bin binary
*.img binary
*.iso binary
*.jar binary
*.war binary
*.ear binary
*.tar binary
*.gz binary
*.zip binary
*.7z binary
*.rar binary
*.bak binary
# Ignore all files in the root directory

/*
!.gitignore
!.gitattributes
!LICENSE
!MANIFEST.in
!README.md
!setup.py
```

## 10. Comandos para publicar o pacote

### 10.1. Build do pacote

Para criar o pacote, execute o comando:

```bash
python setup.py sdist bdist_wheel
```

### 10.2. Upload do pacote no TestPyPI

Para fazer o upload do pacote no TestPyPI, execute o comando:

```bash
twine upload --repository testpypi dist/*
```

Ou com o Twine:

```bash
python -m twine upload --repository testpypi dist/*
```

Ou:

```bash
python -m twine upload --repository-url https://upload.pypi.org/legacy/ dist/*  
```

Utilizando o parâmetro '--verbose', é possível visualizar o log do processo de upload do pacote.

```bash
ython -m twine upload --repository testpypi dist/* --verbose 
```

Para instalar o pacote do TestPyPI, execute o comando:

```bash
pip install --index-url https://test.pypi.org/simple/ image_processing
```

Ou:

```bash
pip install --index-url https://test.pypi.org/simple/ --extra-index-url https://pypi.org/simple image-processing-package-dio 
```

### 10.3. Upload do pacote no PyPI

Para fazer o upload do pacote no PyPI, execute o comando:

```bash
twine upload --repository pypi dist/*
```

Ou com o Twine:

```bash
python -m twine upload --repository-url https://upload.pypi.org/legacy/ dist/*
```

Utilizando o parâmetro '--verbose', é possível visualizar o log do processo de upload do pacote.

```bash
python -m twine upload --repository pypi dist/* --verbose
```

Para instalar o pacote do PyPI, execute o comando:

```bash
pip install image_processing
```

Ou:

```bash
pip install --extra-index-url https://pypi.org/simple image_processing
```

## 11. Referências

- [https://packaging.python.org/tutorials/packaging-projects/](https://packaging.python.org/tutorials/packaging-projects/)
- [https://packaging.python.org/guides/distributing-packages-using-setuptools/](https://packaging.python.org/guides/distributing-packages-using-setuptools/)
- [https://packaging.python.org/guides/making-a-pypi-friendly-readme/](https://packaging.python.org/guides/making-a-pypi-friendly-readme/)