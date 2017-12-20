# Difference between Android compileSdkVersion, minSdkVersion and targetSdkVersion

**minSdkVersion <= targetSdkVersion <= compileSdkVersion**
 
Ideally, the relationship would look more like this in the steady state:

**minSdkVersion (lowest possible) <= targetSdkVersion == compileSdkVersion (latest SDK)**

You’ll hit the biggest audience with a low minSdkVersion and look and act the best by targeting and compiling with the latest SDK.

---
Reference:
- [Picking your compileSdkVersion, minSdkVersion, and targetSdkVersion by Ian Lake](https://medium.com/google-developers/picking-your-compilesdkversion-minsdkversion-targetsdkversion-a098a0341ebd)
 
