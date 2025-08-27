# Ansible Administration

## Basic ansible
- inventory = untuk menyimpan managed server (server yg mau diremote/automation), gunakan parameter -i untuk define dimana file inverntorynya
- ansible conf = file config ansible
- ansible module = module untuk menjalankan tasks (example: apt, pkg, dnf, kvm, dll). bisa melalui comand dengan parameter -m
- ansible playbook = file manifest/yaml untuk menjalankan task automation
- ansible playbook vars = membuat sebuah vars untuk playbook
- ansible conditions = kita bisa membuat kondisi berdasarkan kondisi tertentu menggunakan parameter "when" didalam plabook. contoh case gunakan apt pada debian dan pkg pada alpine
- ansible facts = ansible.builtin.setup, module untuk melihat bentuk informatsi seperti os, kernel, cpu dll pada remote server kita
- forks = membuat batch pada server untuk task. di define pada ansible conf, misalkan server ada 20. dilakukan forks=5, maka task akan dijalankan per 5 server
- tags = memberikan tags pada task kita di playbook, sehingga kita bisa menjalankan tasks tertentu berdasarkan tags. example: ansible-playbook -i inventory --tags setup_user
- ansible loops = membuat perulangan di playbook. hal ini dapat dilakukan jika misalkan kita ingin menginstall bnyk sub dependencies, seperti php8.2, php8.2-cli, php8.2-zip dll. bisa kita define dengan "with_items" dan list dependenciesnya (baca docs terkait ansible loops, banyak cara selain with_items dan use case nya beda").
- ansible vaults = untuk menyimpan sensitive variable, seperti password. ansible-vault create <nama file>, nanti akan diminta mengisi vault pass nya, kemudian baru masuk ke text editor untuk define variablenya.