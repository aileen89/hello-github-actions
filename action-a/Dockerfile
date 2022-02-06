
Chilkat Examples
Chilkat • HOME • Android™ • Classic ASP • C • C++ • C# • Mono C# • .NET Core C# • C# UWP/WinRT • DataFlex • Delphi ActiveX • Delphi DLL • Visual FoxPro • Java • Lianja • MFC • Objective-C • Perl • PHP ActiveX • PHP Extension • PowerBuilder • PowerShell • PureBasic • CkPython • Chilkat2-Python • Ruby • SQL Server • Swift 2 • Swift 3,4,5... • Tcl • Unicode C • Unicode C++ • Visual Basic 6.0 • VB.NET • VB.NET UWP/WinRT • VBScript • Xojo Plugin • Node.js • Excel • Go

Android™ Examples
Web API Categories

ASN.1
Amazon EC2
Amazon Glacier
Amazon S3
Amazon S3 (new)
Amazon SES
Amazon SNS
Amazon SQS
Async
Azure Cloud Storage
Azure Service Bus
Azure Table Service
Base64
Bounced Email
Box
CAdES
CSR
CSV
Certificates
Compression
DKIM / DomainKey
DSA
Diffie-Hellman
Digital Signatures
Dropbox
Dynamics CRM
EBICS
ECC
Ed25519
Email Object
Encryption
FTP
FileAccess
Firebase
GMail REST API
GMail SMTP/IMAP/POP
Geolocation
Google APIs
Google Calendar
Google Cloud SQL
Google Cloud Storage
Google Drive
Google Photos
Google Sheets
Google Tasks
Gzip
HTML-to-XML/Text
HTTP

HTTP Misc
IMAP
JSON
JSON Web Encryption (JWE)
JSON Web Signatures (JWS)
JSON Web Token (JWT)
Java KeyStore (JKS)
MHT / HTML Email
MIME
MS Storage Providers
Microsoft Graph
NTLM
OAuth1
OAuth2
OIDC
Office365
OneDrive
OpenSSL
Outlook
Outlook Calendar
Outlook Contact
PDF Signatures
PEM
PFX/P12
PKCS11
POP3
PRNG
REST
REST Misc
RSA
SCP
SCard
SFTP
SMTP
SSH
SSH Key
SSH Tunnel
ScMinidriver
SharePoint
Socket/SSL/TLS
Spider
Stream
Tar Archive
Upload
WebSocket
XAdES
XML
XML Digital Signatures
XMP
Zip
curl

 

 

 

(Android™) Sign a File to Create a .p7m File (using a PFX)
Android™ example to sign a file creating a .p7m file as output. The .p7m contains the signed contents of the original file. It can be verified and restored by calling VerifyP7M.

Chilkat Android™ Downloads
Android™ Java Libraries

Android C/C++ Libraries

// Important: Don't forget to include the call to System.loadLibrary
// as shown at the bottom of this code sample.
package com.test;

import android.app.Activity;
import com.chilkatsoft.*;

import android.widget.TextView;
import android.os.Bundle;

public class SimpleActivity extends Activity {

  private static final String TAG = "Chilkat";

  // Called when the activity is first created.
  @Override
  public void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);

    // This example requires the Chilkat API to have been previously unlocked.
    // See Global Unlock Sample for sample code.

    CkCrypt2 crypt = new CkCrypt2();

    // Use a digital certificate and private key from a PFX file (.pfx or .p12).
    String signingCertSubject = "Acme Inc";
    String pfxFilename = "/Users/chilkat/testData/pfx/acme.pfx";
    String pfxPassword = "test123";

    CkCertStore certStore = new CkCertStore();
    boolean success = certStore.LoadPfxFile(pfxFilename,pfxPassword);
    if (success != true) {
        Log.i(TAG, certStore.lastErrorText());
        return;
        }

    CkCert cert;
    cert = certStore.FindCertBySubjectCN(signingCertSubject);
    if (certStore.get_LastMethodSuccess() == false) {
        Log.i(TAG, "Failed to find certificate by subject common name.");
        return;
        }

    // Tell the crypt component to use this cert.
    success = crypt.SetSigningCert(cert);

    // We can sign any type of file, creating a .p7m as output:
    String inFile = "/Users/chilkat/testData/pdf/sample.pdf";
    String outputFile = "/Users/chilkat/testData/p7m/sample.pdf.p7m";
    success = crypt.CreateP7M(inFile,outputFile);
    if (success == false) {
        Log.i(TAG, crypt.lastErrorText());

        return;
        }

    // Verify and restore the original file:
    success = crypt.SetVerifyCert(cert);

    inFile = outputFile;
    outputFile = "/Users/chilkat/testData/pdf/restored.pdf";

    success = crypt.VerifyP7M(inFile,outputFile);
    if (success == false) {
        Log.i(TAG, crypt.lastErrorText());

        return;
        }

    Log.i(TAG, "Success!");

  }

  static {
      System.loadLibrary("chilkat");

      // Note: If the incorrect library name is passed to System.loadLibrary,
      // then you will see the following error message at application startup:
      //"The application <your-application-name> has stopped unexpectedly. Please try again."
  }
}

 
© 2000-2022 Chilkat Software, Inc. All Rights Reserved.
