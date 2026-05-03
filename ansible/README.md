# Ansible deployment

Folder ini berisi contoh inventory dan playbook untuk provisioning dua VM Ubuntu:

- `ansible/inventory.ini` - daftar host controller dan managed
- `ansible/playbook.yml` - provisioning Docker, instalasi paket, cloning repo, deploy aplikasi, load balancer

## Alur singkat

1. VM1 dijadikan controller
2. VM2 dijadikan managed node
3. Controller install Docker + Ansible dari package
4. Controller gunakan Ansible untuk install Docker di kedua node
5. Controller deploy aplikasi di managed usando `docker-compose`
6. Controller juga deploy `docker-compose.lb.yml` untuk load balancing

## Contoh menjalankan

```bash
cd /path/to/BengkelMobil
ansible-playbook -i ansible/inventory.ini ansible/playbook.yml
```

Pastikan kedua host dapat diakses via SSH dengan user `ubuntu` atau sesuaikan parameter `ansible_user`.
