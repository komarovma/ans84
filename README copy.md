<p class="has-line-data" data-line-start="0" data-line-end="4">Работаю на Windows 10 PRO<br>
Создал в <a href="http://cloud.yandex.ru">cloud.yandex.ru</a> 3 виртуальных машины CentOS 7.0<br>
Ansible уставлен в WSL 2.0 (Ubuntu)<br>
Playbook создан, результат работы на 3х хостах Яндекс Облака</p>
<pre><code>mike@HOMEDX79SR:~/ans84$ ansible-playbook -i inventory/hosts.yml site.yml --diff
PLAY [Install Elasticsearch] *************************************
TASK [Gathering Facts] ************************
ok: [el-instance]
TASK [elastic-role : Fail if unsupported system detected] ****************************
skipping: [el-instance]
TASK [elastic-role : include_tasks] *********************************************
included: /home/mike/ans84/roles/elastic-role/tasks/download_yum.yml for el-instance
TASK [elastic-role : Download Elasticsearch's rpm] ******************************
ok: [el-instance -&gt; localhost]
TASK [elastic-role : Copy Elasticsearch to managed node] **********************
ok: [el-instance]
TASK [elastic-role : include_tasks] *********************************************
included: /home/mike/ans84/roles/elastic-role/tasks/install_yum.yml for el-instance
TASK [elastic-role : Install Elasticsearch] ****************************
ok: [el-instance]
TASK [elastic-role : Configure Elasticsearch] ***************************
ok: [el-instance]
PLAY [Install Kibana] ************************************************
TASK [Gathering Facts] *********************************************
ok: [kb-instance]
TASK [kibana-role : Fail if unsupported system detected] ****************
skipping: [kb-instance]
TASK [kibana-role : include_tasks] ****************************************
included: /home/mike/ans84/roles/kibana-role/tasks/download_yum.yml for kb-instance
TASK [kibana-role : Download kibana's rpm] *******************************
ok: [kb-instance -&gt; localhost]
TASK [kibana-role : Copy kibana to managed node] ****************************
ok: [kb-instance]
TASK [kibana-role : include_tasks] **************************************************
included: /home/mike/ans84/roles/kibana-role/tasks/install_yum.yml for kb-instance
TASK [kibana-role : Install kibana] **************************************************
ok: [kb-instance]
TASK [kibana-role : Configure kibana] ********************************************
ok: [kb-instance]
PLAY [Install Filebeat] *********************************************************
TASK [Gathering Facts] **********************************************************
ok: [fb-instance]
TASK [filebeat-role : Fail if unsupported system detected] *********************
skipping: [fb-instance]
TASK [filebeat-role : include_tasks] ************************************************
included: /home/mike/ans84/roles/filebeat-role/tasks/download_yum.yml for fb-instance
TASK [filebeat-role : Download filebeat's rpm] ****************************************
ok: [fb-instance -&gt; localhost]
TASK [filebeat-role : Copy filebeat to managed node] ***********************************
ok: [fb-instance]
TASK [filebeat-role : include_tasks] *************************************************
included: /home/mike/ans84/roles/filebeat-role/tasks/install_yum.yml for fb-instance
TASK [filebeat-role : Install filebeat] *******************************************
ok: [fb-instance]
TASK [filebeat-role : Configure filebeat] *********************************
ok: [fb-instance]
PLAY RECAP *******************************************************
el-instance                : ok=7    changed=0    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0
fb-instance                : ok=7    changed=0    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0
kb-instance                : ok=7    changed=0    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0
</code></pre>