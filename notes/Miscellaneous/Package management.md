# Package management
pipsi (deprecated)

## apt
```bash
# list installed packages
apt list --installed
apt list --installed | grep -i <PACKAGE>
dpkg -l
dpkg -l | grep -i <PACKAGE>

# search package
apt search <PACKAGE>
apt list | grep -i <package>

# install package
apt install <PACKAGE>

# uninstall package
apt remove <PACKAGE> #binaries
apt purge <PACKAGE> #binaries + configs (except in /home/)
apt purge --auto-remove <PACKAGE> #binaries + configs (except in /home/) + dependencies

# update
apt list --upgradeable
apt update
apt upgrade <PACKAGE>
apt upgrade
```

## pip
```bash
apt install python3-pip

python3 -m pip install -U pip

# list installed packages
python3 -m pip list
python3 -m pip list | grep -i <PACKAGE>
python3 -m pip freeze
python3 -m pip freeze | grep -i <PACKAGE>

# search package
python3 -m pip search <PACKAGE>

# install package
python3 -m pip install <PACKAGE>

# uninstall package
python3 -m pip uninstall <PACKAGE>

# update
python3 -m pip list --outdated
python3 -m pip install -U <PACKAGE>
python3 -m pip list --outdated --format=freeze | grep -v '^\-e' | awk -F'==' '{print$1}' | xargs -n1 pip install -U
```

## pipx
```bash
apt install pipx
pipx ensurepath

# list installed packages
pipx list
pipx list | grep -i <PACKAGE>

# search package
python3 -m pip search <PACKAGE>

# install package
pipx install <PACKAGE>

# uninstall package
pipx uninstall <PACKAGE>

# update
pipx upgrade <PACKAGE>
pipx upgrade-all


pipx completions
```