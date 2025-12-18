# Absolute Foundation.

## 1️⃣ What is a packet?

<img src="https://lh5.googleusercontent.com/vi3V0geTnBGxDQ89T343aEFds-yTKRZ0T1PjWQdxgKc5czSaCS3s9huvkGt2q757XDlIAF9x04ab107Ej8KoUaXdt-m5BCwEzrrkEtH0Iq8HBaHtyf6WJB8k2emZXAxKHiMGJyrcIU7iTl2QHQ">

The internet uses TCP/IP protocol (Set of rules on how data is transfered over an internet). And in this TCP/IP network the data is not sent in one piece. Instead the datais first broken down into smaller chunks called **data packets**. 

#### Why does the internet use data packets?
- The reason fpr using data packets is to make the internet run smoother and more efficient.
- If internet didnt use data packets and instead it sent all the data together in a long uninterrupted stream of bits and inorder for the data to be read, those bits whould have to be sent in the correct order and this method is what we call **circuit switching**. But a problem with it is that during the transmission of the data no other computers will be able to use those lines until the transmission is complete.

## 2️⃣ What is a port?

- A port is not a physical connection. It is a logical connection that is used by programs and services to exchange information.
- It specifically determines which program or service on a computer or server is going to be used.
- Whether that is pulling up a web page, using a FTP service, accessing email's and so on.
- Ports will have unique numbers that will identify them.
- The number ranges from 0 - 65535.
- Example common ports:

  - **80, 443** - Web pages (http, https).
  - **21** - For FTP (File transfer protocol).
  - **25** - For E-mail (SMTP).
 
- A port number will be always associated with IP address.
- IP address and port number work together to exchange data on a network.
- The IP address determines the location of that server.
- A port number determines which service or program on that server it wants to use.
- Port numbers are divided into 3:

  - Port numbers: 0-1023 are system or well known ports. These are common ports that people use everyday. **Example**: 80,443,21,25.
  - Port numbers: 1024-49151 are called user or registered ports. These are ports that are registered by companies and developers for particular services.
  - Port numbers: 49152-65535 are called dynamic or private ports. These are client side ports that are free to use. These are ports that your computer assigns temporarily to itself during a session.
