# SWE_2021_41_2024_2_week_6
__Week 4 Assignment__
* __[Repository Link](https://github.com/dhkimcoding/SWE_2021_41_2024_2_week_4)__
```python
def isHappy(n):
  prev_nums = list()
  prev_nums.append(n)

  while n != 1 :
    sum = 0
    tmp = n
    while tmp > 0 :
      last_digit = tmp % 10
      sum = sum + last_digit * last_digit
      tmp = tmp // 10

    if sum not in prev_nums :
      prev_nums.append(sum)
      n = sum
      tmp = n
    else :
      return False

  return True
```
* __Assignment Description__
  
  The task is to implement a function that checks if a number is a happy number. A happy number follows these rules:
  1. Start with a positive integer and create a new number by finding the sum of the squares of its digits.
  2. Repeat this process. If the result eventually becomes 1, the number is a happy number. If it enters a cycle that does not include 1, then it is not a happy number.

* __Solution__
  
  The function repeats the operation of finding the sum of the squares of the digits, storing each result in a list called prev_nums.
  If a value that already exists in prev_nums appears again. it indicates an infinite loop, and the function returns False, indicating that the number cannot be a happy number.
  If the function reaches the value 1 without entering an infinite loop, it returns True.

__Week 5 Assignment__
* __Task Description__
  
  The purpose of this assignment is to set up an environment for a container that will be used in the Open-Source Software Practice class.
  This environment must meet the following requirements:
  1. Linux OS
  2. Git installed
  3. Pyhthon3 installed
  4. bind mount
  
  The goal of the task is to start with a plain Ubuntu image and create a container that meets the above conditions

* __Process of creating the target container__

> ```console
> docker pull ubuntu
> ```
> ‘docker pull <image_name>:<tag_name>’ will pull docker images from docker hub to local.
> If we don’t provide tag, the default tag (latest in this case) will be used.
> So, we get default tagged ubuntu image.

> ```console
> docker run -i-t -d --name ubuntu-container ubuntu
> ```
> This command will create docker container named ‘ubuntu-container’ from images ‘ubuntu’.

> ```console
> docker attach ubuntu-container
> ```
> ‘docker attach <container_name>’ will attach your terminal to the container.

> ```console
> apt-get install -y git python3
> ```
> Install Git and python3 on 'ubuntu-container'.

> ```console
> docker pause ubuntu-container
> ```
> pause the running container.

> ```console
> docker commit ubuntu-container ossp
> ```
> This command will will commit the container to given image name.

> ```console
> docker run -dit--name ossp-container -v <host_dir_path>:<container_dir_path> ossp
> ```
> This command will mount <host_dir> to <container_dir> and then share the files.
> Enter proper directory for <host_dir> and <container_dir>.

* __Check our new container__
> ```console
> docker exec <container_name> cat /etc/os-release
> docker exec <container_name> git --version
> docker exec <container_name> python3 --version
> docker inspect --format="{{ .HostConfig.Binds }}" <container_name>
> ```
> These commands should be executed on the host system.
  
