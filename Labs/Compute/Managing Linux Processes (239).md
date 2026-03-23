

### SSH Connection Guide (macOS & Linux)
Note: These steps are for Mac and Linux only. Windows users should skip to the next section.

# 1. Download Credentials: * Click the Details drop-down above and select Show.

Click Download PEM to save labsuser.pem.

Copy the PublicIP address, then close the panel (X).

# 2.Prepare the Key: * Open your terminal and navigate to your download folder:
bash cd ~/Downloads 

Restrict file permissions (required for SSH):

Bash
chmod 400 labsuser.pem
# 3.Connect via SSH:

Run the following command, replacing <public-ip> with the address you copied:

Bash
ssh -i labsuser.pem ec2-user@<public-ip>
Type yes when prompted. No password is required.
