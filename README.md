# Deserialization-Insecure
 by k0mth3 and Tryhackme
           ____                      ,
          /---.'.__             ____//
               '--.\           /.---'
          _______  \\         //
        /.------.\  \|      .'/  ______
       //  ___  \ \ ||/|\  //  _/_----.\__
      |/  /.-.\  \ \:|< >|// _/.'..\   '--'
         //   \'. | \'.|.'/ /_/ /  \\
        //     \ \_\/" ' ~\-'.-'    \\
       //       '-._| :H: |'-.__     \\
      //           (/'==='\)'-._\     ||
      ||                        \\    \|
      ||                         \\    '
      |/                          \\
                                   ||
                                   ||
                                   \\

    ## Insecure Deserialization: A Comprehensive Guide for Developers K0mth3

**Introduction**

Insecure deserialization is a critical security vulnerability that can lead to severe consequences, including remote code execution (RCE), denial-of-service (DoS), and even complete system takeover. It occurs when an application deserializes untrusted data without proper security measures, allowing an attacker to manipulate the data and execute arbitrary code on the system.

**What is Serialization?**

In programming, serialization is the process of converting an object's state into a storable or transmittable format (or a mix of both) that can be saved and reconstructed as and when needed. This capability is crucial in applications where data needs to be transferred between different parts of a system or over a network, such as in web-based applications.

**Example:**

```php
<?php
$noteArray = array("title" => "My THM Note", "content" => "0xnc doesn't exists!");
$serialisedNote = serialize($noteArray); // Converting the note into a storable format
file_put_contents('note.txt', $serialisedNote); // Saving the serialised note to a file
?>
```

The output shows the serialized string in the `note.txt`, which includes details of the note's structure and content. This allows data to be stored in a way that can be easily saved or transmitted.

**Serialized Note**: `a:2:{s:5:"title";s:12:"My THM Note";s:7:"content";s:12:"0xnc doesn't exists!";}`

**What is Deserialization?**

Deserialization is the reverse process of serialization, where the serialized data is converted back into its original object. This is often done when retrieving data from storage or receiving data over a network.

**Example:**

```php
<?php
$serialisedNote = file_get_contents('note.txt'); // Reading the serialised note from the file
$noteArray = unserialize($serialisedNote); // Converting the serialised string back into a PHP array
echo "Title: " . $noteArray['title'] . "<br>";
echo "Content: " . $noteArray['content'];
?>
```

This code reads the serialized note from a file and converts it back into an array, effectively reconstructing the original note. Discussing serialization also necessitates a conversation about security. Just as you wouldn't want someone tampering with your school bag, insecure deserialization can lead to significant security vulnerabilities in software applications. Attackers can alter serialized objects to perform unauthorized actions or steal data.

**What is Insecure Deserialization?**

Insecure deserialization occurs when an application deserializes untrusted data without proper security measures. This means that the application does not verify the origin of the data or whether it has been tampered with before deserializing it.

If an attacker can send untrusted data to the application, they may be able to manipulate that data to execute arbitrary code on the system. This can lead to a range of severe consequences, such as:

* **Remote code execution (RCE):** The attacker can execute any code they want on the system, which could lead to data loss, information theft, or even complete control of the system.
* **Denial-of-service (DoS):** The attacker can send malicious data that causes the application or system to crash, making it unavailable to legitimate users.
* **Privilege escalation:** The attacker can elevate their privileges on the system, which could give them access to resources and information they shouldn't have.

**Examples of Insecure Deserialization**

There are many examples of insecure deserialization in different programming languages and frameworks. Some common examples include:

* **Java object deserialization:** The Java `ObjectInputStream` library is vulnerable to insecure deserialization if not used carefully.
* **PHP object deserialization:** The PHP `unserialize()` function is vulnerable to insecure deserialization if not used carefully.
* **JSON deserialization:** JSON serialization libraries in various languages can be vulnerable to insecure deserialization if not configured correctly.

**CVE's To Study about:**

1. **Log4J Vulnerability CVE2021-44228**
2. **WebLogic Server Remote Code Execution CVE-2015-4852**

**How to Prevent Insecure Deserialization**

Several measures can be taken to prevent insecure deserialization:

* **Validate the data source:** Verify that the data comes from a trusted source before deserializing it.
* **Validate the data format:** Ensure the data is in the correct format before deserializing it.
* **Use secure libraries:** Employ serialization and deserialization libraries known to be secure.
* **Limit what can be deserialized:** Specify which object types can be deserialized

                           **Links**
  https://tryhackme.com/r/room/insecuredeserialisation
