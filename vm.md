🎯 Aim

To transfer files from one virtual machine (VM) to another VM using secure methods like SCP (Secure Copy Protocol).

⚙️ Requirements
Two Linux VMs (e.g., Azure / AWS / VirtualBox)
SSH access enabled
Private/public IP of target VM
SSH key or password authentication
📘 Theory

File transfer between virtual machines is commonly done using SCP or SFTP over SSH, which ensures secure encrypted data transfer between systems.

🖥️ Procedure (Using SCP Command)
📌 Method 1: Transfer from VM1 → VM2
Step 1: Check connectivity

From source VM:

ssh user@<target-vm-ip>
Step 2: Copy file using SCP
scp filename.txt user@<target-vm-ip>:/home/user/

Example:

scp test.txt azureuser@20.40.50.60:/home/azureuser/
Step 3: Verify on target VM

Login to target VM:

ssh azureuser@20.40.50.60

Check file:

ls
📌 Method 2: Transfer Entire Folder
scp -r myfolder user@<target-vm-ip>:/home/user/
📌 Method 3: Using SFTP (Alternative)
Connect:
sftp user@<target-vm-ip>
Upload file:
put file.txt
Exit:
exit
📌 Method 4: Using rsync (Advanced)
rsync -avz file.txt user@<target-vm-ip>:/home/user/
📌 Output
File successfully transferred from one VM to another
Verified using ls command on destination VM
🧾 Result

Files were successfully transferred between two virtual machines using SCP/SFTP methods.

📘 Conclusion

Secure file transfer between virtual machines is efficiently achieved using SCP, SFTP, or rsync over SSH, ensuring encrypted and reliable data movement. 