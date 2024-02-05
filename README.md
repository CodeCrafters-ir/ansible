# install ansible and run project
```
1: clone project to the machin
    1-1: cd to favroite directory
    1-2: git clone 

2: install dependency
    2-1: sudo apt update
    2-2: sudo apt install software-properties-common
    2-3: sudo add-apt-repository ppa:ansible/ansible
    2-4: sudo wget -O - https://keyserver.ubuntu.com/pks/lookup?op=get&search=0xE251165069C45C89 & apt-key add -
    2-5: sudo apt update
    2-6: sudo apt install ansible
    2-7: sudo apt update
    2-8: sudo apt install python3-pip python3-dev libffi-dev libssl-dev libjansson-dev

3: install environment and python dependency
    3-1: python -m venv venv
    3-2: source venv/bin/activate
    3-3: pip install -r requirements.txt
   
4: test ansible
    4-1: ansible --version
    4-2: ansible-playbook playbook/test.yml
```

# ansible commands

```
1: for test one playbook in your machin
    1-1: change hosts in playbook to localhost
    1-2: ansible-playbook <path to playbook> --ask-become-pass

2: Checks the reachability of all hosts in your Ansible
    2-1: ansible all -m ping 

3: Gathers facts about all hosts, collecting system
    3-1: ansible all -m setup

4: Copies a file from the control machine to all hosts.
    4-1: ansible all -m copy -a "src=<path> dest=<path>"

5: Creates a file with specified content on all hosts.
    5-1:ansible all -m copy -a "dest=<path> content='<text-writing>' mode=0777"

6: Removes a file from all hosts.
    6-1:ansible all -m file -a "path=<path> state=absent"

7: Validates the syntax of an Ansible playbook before execution, catching potential errors early on.
    7-1:ansible-playbook --syntax-check <path-to-file>.yml
```

# ssh config
```
ssh-keygen -t rsa

ssh-copy-id username@server_address

ssh username@server_address
```


# توضیحات ansible:
```
1-group_vars directory for varibles in any group in main inventory

2-host_vars directory for varibles in any host in main inventory

3-inventory directory for define my hosts

4-log directory have a file for save logs ansible running

5-playbooks directory:
    describtions: 
    5-1: this directory contains multi file yaml differences , any file 
        connect with a sub directory in roles directory with host (connect roles to hosts) 
    5-2: file config.yml for import other file in the directory and 
        running all settings for   ansible command

6-roles directory:
    توضیحات: in this directory we define tasks for run , every roles install or config
        a package or work or config and every role have one or multi task in multi directories
    6-1:for every yaml file in playbooks directory (without config file)
        we have a directory with same name file, every directory do a work, in subdirectory 
        do tasks, tasks directory is main for playbook for read 
    6-2:files directory is that for static files use in server
    6-3:templates directory is that for use tasks with varibles
    6-4:vars directory have a varibles for that work can use in tasks
    6-5:common directory is defain resable tasks
    6-6:handlers directory is define one use task  
    6-7:meta directory for do difference task

7-ansible.cfg file is settings global ansible and configuration customize
```

‍‍‍‍‍‍```
**1. دایرکتوری group_vars: برای متغیرهای گروهی**

- متغیرهایی را که برای همه میزبان‌های درون یک گروه در فایل inventory اصلی اعمال می‌شوند، ذخیره می‌کند.

**2. دایرکتوری host_vars: برای متغیرهای میزبان**

- متغیرهایی را که برای یک میزبان خاص در فایل inventory اصلی اعمال می‌شوند، ذخیره می‌کند.

**3. دایرکتوری inventory: برای تعریف میزبان‌ها**

- فایلی به نام hosts (یا فایلی با پسوند .ini) را شامل می‌شود که میزبان‌ها و گروه‌های آن‌ها را مشخص می‌کند.

**4. دایرکتوری log: برای ذخیره‌سازی گزارش‌ها**

- فایل‌های گزارشی از اجرای دستورات Ansible را در خود نگه می‌دارد.

**5. دایرکتوری playbooks: برای playbook ها**

- **توضیحات:**
    - شامل چندین فایل YAML است که هر کدام یک playbook را تعریف می‌کنند.
    - هر فایل به یک زیردایرکتوری در دایرکتوری roles متصل می‌شود تا نقش‌ها را به میزبان‌ها پیوند دهد.
    - فایل config.yml برای وارد کردن سایر فایل‌های playbook و اجرای تنظیمات کلی Ansible استفاده می‌شود.

**6. دایرکتوری roles: برای تعریف نقش‌ها**

- **توضیحات:**
    - وظایفی را که باید اجرا شوند، تعریف می‌کند.
    - هر نقش یک بسته، کار یا تنظیمات را نصب یا پیکربندی می‌کند.
    - هر نقش می‌تواند شامل یک یا چند وظیفه در دایرکتوری‌های مختلف باشد.
    - **6-1:** برای هر فایل YAML در دایرکتوری playbooks (به جز فایل config.yml)، یک دایرکتوری با همان نام فایل وجود دارد.
        - هر دایرکتوری یک کار خاص را انجام می‌دهد و زیردایرکتوری‌های آن، وظایف مربوط به آن کار را شامل می‌شوند.
        - دایرکتوری tasks اصلی‌ترین دایرکتوری برای خواندن playbook است.
    - **6-2:** دایرکتوری files: برای فایل‌های ایستایی که در سرور استفاده می‌شوند.
    - **6-3:** دایرکتوری templates: برای استفاده از وظایف همراه با متغیرها.
    - **6-4:** دایرکتوری vars: شامل متغیرهایی است که در وظایف قابل استفاده هستند.
    - **6-5:** دایرکتوری common: برای تعریف وظایف قابل استفاده مجدد.
    - **6-6:** دایرکتوری handlers: برای تعریف وظایفی که تنها یک بار اجرا می‌شوند.
    - **6-7:** دایرکتوری meta: برای انجام کارهای مختلف و مدیریت نقش‌ها.

**7. فایل ansible.cfg: برای تنظیمات کلی Ansible**

- تنظیمات و پیکربندی‌های سفارشی Ansible را در خود جای می‌دهد.

```