# CBOR Identity Data in QR-Code

**Tag**: 169 (identity-data)

**Data Item**: JSON Object

**Semantics**: Unique Identity Data of a Citizen in QR-Code

**Point of contact**: Resham Chugani (resham@mosip.io)

# Summary

Registering the claim for storing Unique Identity Data of a Citizen registered using any ID platforms.

# Rationale

Once a citizen has been registered in an identity system, their data is typically utilised for identification, enabling them to access social benefits and various government services. The level of assurance for identification varies based on the type of authentication employed. A low assurance level is achieved when an ID, demographic data, password, or PIN is used. In contrast, the assurance level increases when authentication involves methods such as OTP or biometrics. Among these, biometric authentication offers the highest level of assurance, as it enables the system to verify the presence of the citizen. While this is particularly effective for online systems where verification occurs on the server, offline authentication poses challenges in maintaining a high level of assurance.
 
To address this issue, we have devised an approach that involves storing a low-resolution grayscale photograph of the citizen and a minimal demographic data set within a QR code. This QR code would be digitally signed by the ID system and then printed on a physical card. We intend to use the signed data contained within the QR code for facial authentication later. However, it's important to note that QR codes have certain size limitations. To generate a smaller signature and more compact data, we recommend the use of CWT.

# Semantics

Tag 169 represents a JSON Object that includes a range of ID attributes defined by the issuing identity system as key-value pairs. Below, you can find an illustration of the ID JSON structure contained within Tag 169, where:

* 1: tstr,           // ID (text string)
* 2: tstr,           // First name or full name (text string)
* 3: tstr,           // Middle name (text string)
* 4: tstr,           // Last name (text string)
* 5: tstr,           // Gender (text string)
* 6: tstr,           // Date of Birth (text string)
* 7: tstr,           // Place (text string)
* 8: [int],          // Best Quality Fingers (array of integers representing the best quality fingers)
* 9: tstr,           // Binary image (text string)
* 10: tstr,          // Additional attribute 10 (Reserved for future attributes)
* 11: tstr,          // Additional attribute 11 (Reserved for future attributes)
* 12: tstr,          // Additional attribute 12 (Reserved for future attributes)
* 13: tstr,          // Additional attribute 13 (Reserved for future attributes)
* 14: tstr,          // Additional attribute 14 (Reserved for future attributes)
* 15: tstr           // Additional attribute 15 (Reserved for future attributes)

# Example
```CWT
{
   "1":"COUN",
   "6":1665980929,
   "8":{
      "3":"dfd1aa976d8d4575a0fe34b96de2bfad"
   },
   "169":{
        "1": "11110000324013",
        "2": "Peter",
        "3": "S",
        "4": "Alex",
        "5": "Male",
        "6": "1988-01-02",
        "7": "New City, METRO LINE, PA",
        "8": "[1,2]",
        "9": "03CBABDF83D068ACB5DE65B3CDF25E0036F2C546CB90378C587A076E7A759DFD27CA7872B6CDFF339AEAACA61A6023FD1D305A9B4F33CAA248CEDE38B67D7C915C59A51BB4E77D10077A625258873183F82D65F4C482503A5A01F41DEE612C3542E5370987815E592B8EA2020FD3BDDC747897DB10237EAD179E55B441BC6D8BAD07CE535129CF8D559445CC3A29D746FBF1174DE2E7C0F3439BE7DBEA4520CF88825AAE6B1F291A746AB8177C65B2A459DD19BD32C0C3070004B85C1D63034707CC690AB0BA023350C8337FC6894061EB8A714A8F22FE2365E7A904C72DEC9746ABEA1A3296ECACD1A40450794EDCD2B34844E7C19EB7FB1A4AF3B05C3B374BD2941603F72D3F9A62EAB9A2FDAEEEEC8EE6E350F8A1863C0A0AB1B4058D154559A1CD5133EFCF682ABC339960819C9427889D60380B635A7D21D017974BBA57798490F668ADD86DA58125D9C4C1202CA1308F7734E43E8F77CEB0AF968A8F8B88849F9B98B26620399470ED057E7931DED82876DCA896A30D0031A8CBD7B9EDFDF16C15C6853F4F8D9EEC09317C84EDAE4B349FE54D23D8EC7DC9BB9F69FD7B7B23383B64F22E25F"
}
```
![Sample QR Code](https://github.com/mahammedtaheer/open-spec/blob/main/sample_qr_code.png?raw=true "Sample QA Code")


# References

[1] C. Bormann, and P. Hoffman. "Concise Binary Object Representation (CBOR)". [RFC 7049](https://tools.ietf.org/html/rfc7049), October 2013.

[2] Mike Jones, Hannes Tschofenig, Ludwig Seitz  "CBOR Web Token (CWT)". [RFC 8392](https://www.iana.org/go/rfc8392), March 2018.

# Author

Resham Chugani ([resham@mosip.io](mailto:resham@mosip.io))
