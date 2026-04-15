# Data Protection Using Encryption

Cryptography is the conversion of communicated information into secret code to keep information confidential and private. The central function is encryption, which transforms data into an unreadable form (ciphertext). Decryption transforms it back into readable data (plaintext).

In this lab, you will:

- Create an AWS KMS encryption key.

- Install and configure the AWS Encryption CLI on an Amazon EC2 instance.

- Encrypt plaintext files and view them in their encrypted state.

- Decrypt the files to recover the original content.

## Objectives
- Create an AWS KMS encryption key

- Install the AWS Encryption CLI

- Encrypt plaintext

- Decrypt ciphertext

Lab Environment
The environment includes a preconfigured EC2 instance named File Server. I will connect to this instance using AWS Systems Manager Session Manager.

### Task 1: Create an AWS KMS key
In this task, you will create a symmetric encryption key.

In the AWS Console, search for KMS and choose Key Management Service.

Choose Create a key.

For Key type, choose Symmetric, then choose Next.

Configure Labels:

Alias: MyKMSKey

Description: Key used to encrypt and decrypt data files.

Choose Next.

<img width="700" height="502" alt="Lab 278_1" src="https://github.com/user-attachments/assets/3fd82492-a5df-429b-a982-8656fe0995b1" />


Key Administrators: Search for and select the checkbox for voclabs. Choose Next.

Key Usage Permissions: Search for and select the checkbox for voclabs. Choose Next.

Review the settings and choose Finish.

<img width="780" height="500" alt="Lab 278_2" src="https://github.com/user-attachments/assets/f3151c22-dfb5-47f2-8332-93275483040e" />


Click the link for MyKMSKey and copy the ARN (Amazon Resource Name) to a text editor for later use.

<img width="700" height="500" alt="Lab 278_3" src="https://github.com/user-attachments/assets/d496c607-ba30-4ee6-bf6a-d6305e49079f" />


### Task 2: Configure the File Server instance

Set up the AWS Encryption CLI and credentials on your EC2 instance.

In the console, navigate to EC2 and select the File Server instance.

Choose Connect, select the Session Manager tab, and choose Connect.

Run the following commands to initialize the AWS configuration:

Bash
cd ~
aws configure
Configure the prompts with these temporary placeholders:

AWS Access Key ID: 1

AWS Secret Access Key: 1

Default region name: (Paste the Region from your Vocareum AWS Details page)

Default output format: (Press Enter)

On the Vocareum page, go to AWS Details, choose Show next to AWS CLI, and copy the code block starting with [default].

Return to the terminal and edit the credentials file:

<img width="500" height="238" alt="Lab 278_4" src="https://github.com/user-attachments/assets/3e521a49-2fc1-460e-838b-03b0e7122c77" />


Bash
vi ~/.aws/credentials
Delete the existing contents (type dd multiple times) and paste the code block you copied.

Save and close: Press Escape, type :wq, and press Enter.

Install the AWS Encryption CLI and set your path:

Bash
pip3 install aws-encryption-sdk-cli
export PATH=$PATH:/home/ssm-user/.local/bin

<img width="700" height="500" alt="Lab 278_6" src="https://github.com/user-attachments/assets/79e1aa90-5961-4413-bd3d-be6fe1a171ff" />


### Task 3: Encrypt and Decrypt Data
Create a secret file, encrypt it using the KMS key, and then decrypt it.

1. Create the Plaintext Files
Run the following commands to create and view a secret file:

Bash
touch secret1.txt secret2.txt secret3.txt
echo 'TOP SECRET 1!!!' > secret1.txt
cat secret1.txt
mkdir output
2. Encrypt the Data
Set the ARN variable in your terminal (replace (KMS ARN) with your copied ARN):

Bash
keyArn=(KMS ARN)
Run the encryption command:

Bash
aws-encryption-cli --encrypt \
                     --input secret1.txt \
                     --wrapping-keys key=$keyArn \
                     --metadata-output ~/metadata \
                     --encryption-context purpose=test \
                     --commitment-policy require-encrypt-require-decrypt \
                     --output ~/output/.
Check the success status (0 means success):

Bash
echo $?
View the encrypted ciphertext:

Bash
ls output
cd output
cat secret1.txt.encrypted


3. Decrypt the Data
Run the decryption command:

Bash
aws-encryption-cli --decrypt \
                     --input secret1.txt.encrypted \
                     --wrapping-keys key=$keyArn \
                     --commitment-policy require-encrypt-require-decrypt \
                     --encryption-context purpose=test \
                     --metadata-output ~/metadata \
                     --max-encrypted-data-keys 1 \
                     --buffer \
                     --output .
Verify the file location and view the restored plaintext:

Bash

ls

cat secret1.txt.encrypted.decrypted


Screenshot Placeholder: > [Insert screenshot of decrypted plaintext here]

## Conclusions: I have successfully created a symmetric AWS KMS key, configured the Encryption CLI, and performed full-cycle encryption and decryption on sensitive data files.
