# JavaNet
In this article I'am going to show you the use of FTP server for communication and file transfer.The application is simple and classes are easy to understand.

Setup

MockFTPServer has been used to check connnection prior to implementations.This is necessary for runnning server transparantly.

FTP Support in JDK

Surprisingly, there’s already basic support for FTP in some JDK flavors in the form of sun.net.www.protocol.ftp.FtpURLConnection.

However, we shouldn’t use this class directly and it’s instead possible to use the JDK’s java.net.URL class as an abstraction.

This FTP support is very basic, but leveraging the convenience APIs of java.nio.file.Files, it could be enough for simple use cases.

Connecting

We first need to connect to the FTP server. Let’s start by creating a class FtpClient.

It will serve as an abstraction API to the actual Apache Commons Net FTP client:We need the server address and the port, as well as the

username and the password. After connecting it’s necessary to actually check the reply code, to be sure connecting was successful. We also

add a PrintCommandListener, to print the responses we’d normally see when connecting to an FTP server using command line tools to stdout.

Uploading Files and Downloading Files

we transform the returned FTPFile array is transformed into a list of Strings using Java 8 Streams:

The Apache Net Commons FTP client contains a convenient API, that will directly write to a defined OutputStream. This means we can use this directly.
