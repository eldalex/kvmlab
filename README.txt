Разворачивание стенда kubernetes на виртуалках KVM.
не окончательный вариант.
Использование:

1) Заполнить переменные в файле my_vars.yml
    - variant: all-in-one #[all-in-one, ha-cluster]     - Вариант установки
    - engine: cri-o #[container-d, cri-o, docker]       - Движок
    - libvirt_pool_dir: "/home/alex/myStorage/storage_for_VMs/" - Каталог для дисков витруальных машин
    - libvirt_pool_images: "/home/alex/myStorage/iso_images/"   - Каталог для iso образа и шаблона
    - vm_net: vmnet - сеть для ВМ
    - ssh_key: "/home/alex/.ssh/id_rsa.pub" - публичный ключ пользователя
    - параметры машин если надо.

2) Запуск установки:
ansible-playbook -K ./setup_k8s.yaml -i ./inventory --extra-vars "@my_vars.yml"

3) Удаление стенда:
ansible-playbook -K ./remove_stand.yml

осталось добавить создание сети. на текущий момент надо создать ручками перед установкой.