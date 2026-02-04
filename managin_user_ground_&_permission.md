USER - root (admin) and normal user management in Linux 


# useradd -m imam // create user 'imam' with home directory

# sudo usermod -aG sudo imam // Add user 'imam' to sudo group that provide admin rights

# sudo deluser imam sudo // remove admin rights from user 'imam'

# sudo passwd -l imam // lock user 'imam' (disable login)

# sudo passwd -u imam // unlock user 'imam' (enable login)

# sudo userdel -r imam // delete user 'imam' and its home directory

# su imam // switch to user 'imam'

# #-> means the root user command prompt
# $ -> means the normal user command prompt
# ~ -> means the home directory of the user
# . -> means current directory
# .. -> means parent directory
# / -> means root directory
# .filename -> means hidden file
# ~filename -> means file in home directory 


# passwd imam // change password of user 'imam'
# sudo chown imam file.txt // change ownership of file.txt to user 'imam'


to see all the users in the system
# cat /etc/passwd

# sudo su - imam // switch to user 'imam' with environment variables



# addgroup developers // create group 'developers' -> groupadd developers it is works too if addgroup not available
# sudo usermod -aG developers imam // add user 'imam' to group 'developers' -> 
# groups imam // see all groups of user 'imam'
# sudo deluser imam developers // remove user 'imam' from group 'developers'
# sudo groupdel developers // delete group 'developers'
# cat /etc/group // see all groups in the system -- important

Group 2 types:
# Primary group -> each user has one primary group -> usually same as username
# Secondary group -> user can have multiple secondary groups

#  useradd -m -s /bin/bash imam // create user 'imam' with home directory and bash as default shell

-rw-rw-r-- 1 imam imam    0 Jan 15 14:30 file.txt
[first_3_chars] [second_3_chars] [third_3_chars]  
[owner]         [group]          [others]        [size_in_bytes]  [date]         [time]      [filename]
- -> regular file
r -> read permission
w -> write permission
- -> execute permission (no execute permission) -> to give execute permission use chmod +x file.txt -> to give execute permission to owner only use chmod u+x file.txt -> to remove execute permission from owner use chmod u-x file.txt -> to give execute permission to all use chmod a+x file.txt -> to remove execute permission from all use chmod a-x file.txt -> to give read, write and execute permission to owner use chmod u+rwx file.txt -> to give read, write and execute permission to group use chmod g+rwx file.txt -> to give read, write and execute permission to others use chmod o+rwx file.txt -> to remove read, write and execute permission from owner use chmod u-rwx file.txt -> to remove read, write and execute permission from group use chmod g-rwx file.txt -> to remove read, write and execute permission from others use chmod o-rwx file.txt

drwxrwxr-x 2 imam imam 4096 Jan 15 14:31 files 
d -> directory
r -> read permission
w -> write permission
x -> execute permission (permission to enter the directory) -> to remove execute permission use chmod -x files




chown imam:developers file.txt // change ownership of file.txt to user 'imam' and group 'developers'