### Experiment 1: Decentralized Certificate Verification
```
   Name : Mukesh R
   Reg No: 212224240098
```
## Aim:
  To develop a smart contract for issuing and verifying academic certificates on Ethereum, preventing forgery and ensuring authenticity.
## Algorithm:
1. Deploy a smart contract where universities can issue certificates.
2. Store a hash of certificate data on-chain.
3. Provide a verification function that checks certificate authenticity.
4. Users can verify the certificate by comparing the stored hash.
## Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;
contract CertificateVerification {
address public university;
mapping(bytes32 => bool) public certificates; // Store hashed certificates
event CertificateIssued(bytes32 indexed certHash);
constructor() {
university = msg.sender; // University deploys the contract
}
function issueCertificate(string memory studentName, string memory degree,
uint256 year) public {
require(msg.sender == university, "Only university can issue certificates");
bytes32 certHash = keccak256(abi.encodePacked(studentName, degree,
year));
certificates[certHash] = true;
emit CertificateIssued(certHash);
}
function verifyCertificate(string memory studentName, string memory degree,
uint256 year) public view returns (bool) {
bytes32 certHash = keccak256(abi.encodePacked(studentName, degree,year));
return certificates[certHash];
}
}
# Expected Output:
```
● When the university issues a certificate, it gets stored as a hash.
● A student or employer can verify the certificate by entering the details.
● If valid, it returns true; otherwise, false.
High-Level Overview:
● Used to prevent fake certificates.
● Enables quick verification by employers or other institutions.
● Shows how blockchain can be used in education and credential verification.
```

# Output:

<img width="1423" height="998" alt="Screenshot 2025-10-06 155031" src="https://github.com/user-attachments/assets/32972f46-625f-4cb2-b88c-6d6e242c974a" />

<img width="1437" height="947" alt="Screenshot 2025-10-06 155139" src="https://github.com/user-attachments/assets/c927fdca-4fb3-44a3-942c-5e6ff990e77a" />

<img width="1369" height="935" alt="Screenshot 2025-10-06 155159" src="https://github.com/user-attachments/assets/8ae8db1f-1d0b-40a6-a1cb-6d5a580e0c24" />



# Result:

Thus a smart contract was developed for issuing and verifying academic certificates on Ethereum, preventing forgery and ensuring authenticity.
