# Configurando o ambiente
Neste curso vamos utilizar o sistema operacional Ubuntu, porém a escolha do sistema operacional é sua.

## Windows
Acesse a página de downloads do Python [https://www.python.org/downloads/windows/](https://www.python.org/downloads/windows/), neste curso vamos utilizar a versão 3.6.2 que é a versão mais atual no momento da escrita desse material.

Após efetuar o download execute o instalador. **ATENÇÃO:** Na tela inicial marque a opção para adicionar PYTHON_PATH as variáveis de ambiente do sistema.

Abra o CMD e digite `python -V`, o comando deve retornar a versão do Python instalada em sua máquina.

## Unix-like
Muito provavelmente Python já está instalado em seu sistema operacional, caso não esteja consulte como instalar Python através do seu gerenciador de pacotes.

Para checar se Python está instalado e qual a versão `python -V`.

## Pyenv (opcional)
O Pyenv é um projeto que auxilia a manter 'N' versões de Python instaladas na máquina. Para instalar o Pyenv vamos utilizar o projeto [pyenv-installer](https://github.com/pyenv/pyenv-installer).

Para funcionar corretamente o Pyenv precisa que alguns pacotes estejam disponíveis na máquina, o comando de instalação pode ser encontrado em [Pyenv Wiki](https://github.com/pyenv/pyenv/wiki/Common-build-problems), abaixo o comando para Ubuntu:

```sh
sudo apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev \
libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev \
xz-utils tk-dev libffi-dev liblzma-dev
```

Agora vamos instalar o Pyenv utilizando o `pyenv-installer`:

```sh
curl -L https://github.com/pyenv/pyenv-installer/raw/master/bin/pyenv-installer | bash
```

Após finalizar o processo de instalação é necessário adicionar no `.bashrc`:

```sh
export PATH="/home/<your_user>/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```

*Nota: Se estiver utilizando outro shell (zsh, fish, etc), verificar qual arquivo equivalente ao .bashrc.*

Abra um novo terminal e digite `pyenv` se estiver tudo correto um texto semelhante deve ser exibido:

```sh
pyenv 1.2.8
Usage: pyenv <command> [<args>]

Some useful pyenv commands are:
   commands    List all available pyenv commands
   local       Set or show the local application-specific Python version
   global      Set or show the global Python version
   shell       Set or show the shell-specific Python version
   install     Install a Python version using python-build
   uninstall   Uninstall a specific Python version
   rehash      Rehash pyenv shims (run this after installing executables)
   version     Show the current Python version and its origin
   versions    List all Python versions available to pyenv
   which       Display the full path to an executable
   whence      List all Python versions that contain the given executable

See `pyenv help <command>' for information on a specific command.
For full documentation, see: https://github.com/pyenv/pyenv#readme
```
