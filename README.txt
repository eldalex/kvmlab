Разворачивание стенда kubernetes на виртуалках KVM.
не окончательный вариант.
Запуск на текущий момент:
ansible-playbook -K ./debian_11_provision.yaml -i ./inventory
Необходимо поправить пути ведущие к дефолтным каталогам в roles/debian_11_provision/defaults/main.yml
