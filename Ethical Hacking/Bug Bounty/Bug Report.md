Critical Insecure Direct Object Reference (IDOR) Vulnerability in Kajabi Email Services

Dear [Recipient's Name],

I hope this email finds you well. I am writing to report a significant vulnerability that I have discovered in the email unsubscribe functionality of websites utilizing Kajabi Email Services. This vulnerability poses a high risk of unauthorized individuals being able to unsubscribe and subscribe other users by manipulating the URL's contact ID parameter. Moreover, this vulnerability extends beyond a single website and affects any website that utilizes Kajabi Email Services.

Description: 
The vulnerability identified is an Insecure Direct Object Reference (IDOR) vulnerability. It allows malicious actors to manipulate the contact ID parameter in the URL, enabling them to unsubscribe any user from any website's email service that relies on Kajabi Email Services.

Impact:
This vulnerability presents serious privacy and user experience risks for users of multiple websites. Unauthorized individuals can exploit this vulnerability to unsubscribe users from important updates or newsletters, leading to inconvenience and potentially damaging the trust users have in the affected websites. The potential consequences include a loss of customer engagement, reputational harm, and compromised privacy.

Steps to Reproduce: 
To reproduce the vulnerability, please follow these steps:

1. Subscribe to any website that utilizes Kajabi Email Services, such as papareact.com's newsletter.
(URL for papareact newsletter : www.papareact.com)  

![[Pasted image 20230605182239.png]]  

1. Proceed to unsubscribe from the service.
2. Upon loading the website, manipulate the section indicated in the provided screenshot. 

![[Pasted image 20230605182426.png]]  

3. For example, change that  number to 2391918431.
4. The system will redirect to an email unsubscribe section for a different user, enabling the unsubscribe function to work effectively.
![[Pasted image 20230605182536.png]]  


Recommended Solution: To address this vulnerability, I recommend implementing the following solutions:

1. Access Control: Implement robust access controls to prevent unauthorized users from modifying other users' email preferences. Ensure that only the users themselves can modify their own subscription status.
    
2. User Authentication: Implement strong user authentication measures to verify users before allowing them to modify their email preferences. This will prevent unauthorized users from changing subscription status and ensure that only authorized individuals can make changes.
    
3. Security Testing: Conduct comprehensive security testing, including vulnerability assessments and penetration testing, to identify and address any additional vulnerabilities that may exist in the email unsubscribe functionality.
    

Please give immediate attention to this critical vulnerability to safeguard the privacy and user experience of websites relying on Kajabi Email Services. Should you require any further information or assistance, please feel free to reach out to me.

Thank you for your attention to this matter.

Sincerely,
Krishanthan
krishanthan.2022.4.4@gmail.com