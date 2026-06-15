[06:14:2026] Security Incident: Unauthorized SMB Authentication Attempt


Incident Details
Detection Source: Wazuh SIEM / Windows Security Event Log
Attack Vector: Brute-force credential spraying via SMB (T1110.001)



Observation:
At 18:04:15, the SIEM generated multiple alerts under Rule 92652 (Possible pass-the-hash/NTLM abuse).
![Attack1](https://github.com/kaustuv2002/SOC-Home-Lab/blob/cff54af61fdbb28b955fd15b5b8967b4c0f79cb5/image/bruteforce.png)

Discovered 37 Authentication Failure
![Data](https://github.com/kaustuv2002/SOC-Home-Lab/blob/a66c37f9b132d798a26e7e25c2f7073ccc338460/image/authfail.png)

Filtered 4625 Login Failures and Finding the Attacker IP address
![foundattacker](https://github.com/kaustuv2002/SOC-Home-Lab/blob/73da961b86d3124ac1cd9396695179842989181e/image/found%20the%20attacker.png)


