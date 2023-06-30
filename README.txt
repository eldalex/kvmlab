Разворачивание стенда kubernetes на виртуалках KVM.

Стенд разворачивается согласно заданным параметрам.
1)  Вариант установки:
    - all-in-one, аналог minikube, всё в одном сервере.
    - ha-cluster, кластер из 5 машин, 3 менеджмента, 2 воркера.
2)  Движок контейнеризации container-d/cri-o/docker

Использование:

1) Заполнить переменные в файле my_vars.yml
    - variant: all-in-one #[all-in-one, ha-cluster]     - Вариант установки
    - engine: cri-o #[container-d, cri-o, docker]       - Движок
    - libvirt_pool_dir: "/home/alex/myStorage/storage_for_VMs/" - Каталог для дисков витруальных машин
    - libvirt_pool_images: "/home/alex/myStorage/iso_images/"   - Каталог для iso образа и шаблона
    - vm_net: vmnet - сеть для ВМ
    - ssh_key: "/home/alex/.ssh/id_rsa.pub" - публичный ключ пользователя, обязательно!
    - параметры машин если надо.

2) Запуск установки:
ansible-playbook -K ./setup_k8s.yaml -i ./inventory --extra-vars "@my_vars.yml"

3) Удаление стенда:
ansible-playbook -K ./remove_stand.yml
