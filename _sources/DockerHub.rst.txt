Завантаження образу до репозиторію DockerHub
============================================
Для того, щоб запустити образ з будь-якої машини без попередньої побудови образу необхідно завантажити файл до репозиторію образів DockerHub.

- *Крок 1*
    - Перевірте, чи служба Docker служба вімкнена:
        
        .. image:: /Images/launchDocker/1.png
        
    - Якщо вимкнено службу, то запустіть команду:
    
        .. image:: /Images/launchDocker/2.png
        
 - *Крок 2*
   - Перейдіть до папки з Dockerfile:
   
    .. image:: /Images/launchDocker/3.png
    
- *Крок 3*
   - Необхідно побудувати образ, для цього використайте команду:
   
   .. image:: /Images/launchDocker/4.png

- *Крок 4*        
    - Перевірте, чи створився образ:
    
   .. image:: /Images/launchDocker/5.png
   
- *Крок 5*
    - Зареєструйтесь на `DockerHub`_:
    
 .. _DockerHub: https://hub.docker.com/
 
    .. image:: /Images/DockerHub/1.png
    
- *Крок 6*
    - Створіть репозиторій:
    
    .. image:: /Images/DockerHub/2.png
    
 -*Крок 7*
    - Змініть назву образу на назву репозиторію:
    
    *Назва репозиторія*
    
       .. image:: /Images/DockerHub/4.png
       
   *Команда для зміни назви образу*
   
    .. image:: /Images/DockerHub/3.png
    
 - *Крок 8*
    - Перевірка, чи створився образ:
    
    .. image:: /Images/DockerHub/5.png
    
- *Крок 9*
    - Зайдіть в свій репозиторій через термінал:
    
     .. image:: /Images/DockerHub/6.png
     
- *Крок 10*
    -  Загрузимо наш образ в репозиторій:
    
     .. image:: /Images/DockerHub/7.png
     
- *Крок 11*
   - Перевіримо наявність образу в репозиторію:
   
   .. image:: /Images/DockerHub/8.png
   
- *Крок 12*
   - Запускаємо з будь-якої машини командою:
   
   .. image:: /Images/DockerHub/9.png
   
   
