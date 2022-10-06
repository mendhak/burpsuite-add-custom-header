Extension for BurpSuite Enterprise which adds a hardcoded `X-BurpSuite: 1` header to every request.  Totally unconfigurable.  

The intention is to use this extension and then filter out BurpSuite traffic in our logging and monitoring stack.  

Forked from [this extension](https://github.com/UthmanPortSwigger/add-custom-headers).  


# Java
 1. Clone this repo
 2. Edit **BurpExtender.java** using vim or a text editor of your choice. Change **urlMatchList** to match your scope, **headersToAdd** to match the headers you want to add, and set **checkForDuplicates** to true or false. In the example under Releases (v1.0), the scope is https://portswigger-labs.net and the headers added are "Header1: value1" and "Header2: Value2"
 3. Run **`./gradlew fatJar`** 
 4. Load the **Add-XBurpSuite-Header.jar** file created at **build/libs** into Burp Suite Professional under **`Extender > Extensions > Add`** or Burp Suite Enterprise under **`Cog/Settings icon > Extensions > Custom extensions > Upload extension`**
    - https://portswigger.net/burp/documentation/enterprise/working/scans/extensions#writing-and-uploading-your-own-extensions

**Note for Enterprise users:**
  - You will need to be running [Burp Suite Enterprise 2021.8](https://portswigger.net/burp/releases/enterprise-edition-2021-8?requestededition=enterprise) or later. Please build this extension with the Java 11 JRE in your `Enterprise installation directory > jres`.<br />
  - The build command in step 4 will then become: `./gradlew -Dorg.gradle.java.home=<path-to-your-enterprise-installation-directory>/jres/11.x/Contents/Home fatJar` or `gradle -Dorg.gradle.java.home=<path-to-your-enterprise-installation-directory>/jres/11.x/Contents/Home fatJar` 
  - In the points above, replace `<path-to-your-enterprise-installation-directory>` and `11.x` as appropriate
 