# Analyze-a-Phishing-Email-Sample
TASK 2: Analyze a Phishing Email Sample. 

1.	A SAMPLE PHISHING EMAIL:
From: "Apple Support" <support@apple.com>
Reply-To: security@apple-id-recovery.com
To: user@example.com
Subject: Urgent: Your Apple ID Has Been Locked
Date: Tue, 18 Jun 2024 14:21:53 -0700
Return-Path: <mailer@appleid-verification-alert.net>
Received-SPF: fail (appleid-verification-alert.net: domain of mailer@appleid-verification-alert.net does not designate 185.234.217.101 as permitted sender)
Authentication-Results: dkim=fail dmarc=fail

Dear Customer,

We have detected suspicious activity on your Apple ID and have temporarily locked your account for your protection.

To restore full access, please verify your identity immediately by following the secure link below:

👉 [Verify Now](http://appleid-verification-alert.net/restore)

Failure to verify within 24 hours will result in permanent suspension of your Apple ID.

Thank you,
Apple Security Team

---

© 2024 Apple Inc. All rights reserved.



2.	Examine Sender's Email Address for Spoofing
Header Values:
From: "Apple Support" <support@apple.com>
Reply-To: security@apple-id-recovery.com
Return-Path: mailer@appleid-verification-alert.net

Issues:
•	Display name is "Apple Support", but Return-Path and Reply-To domains differ.
•	Return-Path domain is not apple.com — it is appleid-verification-alert.net, a lookalike domain.

Verdict: Highly suspicious. Legitimate Apple emails come from verified Apple servers/domains only.

3.	Check Email Headers for Discrepancies
Header Authentication Results:
Received-SPF: fail
Authentication-Results: dkim=fail dmarc=fail
Analysis:
•	SPF failed: sending server isn't allowed by domain policy.
•	DKIM and DMARC both failed: sender authenticity cannot be verified. 

Verdict: Clear spoofing or use of lookalike domain. 

4.	Identify Suspicious Links or Attachments
Link in Body:
http://appleid-verification-alert.net/restore
Suspicious Indicators:
•	Domain is not apple.com
•	Uses HTTP (not secure HTTPS)
•	Domain is designed to mimic Apple ID branding
•	Could lead to a credential harvesting site

Attachments: None in this sample

Verdict: Link is clearly malicious or fraudulent

5.	Look for Urgent or Threatening Language
Sample Phrases from Body:
•	"We have temporarily locked your account for your protection."
•	"Failure to verify within 24 hours will result in permanent suspension"

Analysis:
•	Classic phishing tactic: create panic
•	Forces user to act quickly without thinking

Verdict: Strong use of urgency and fear

6.	Note Any Mismatched URLs (Hover Technique)
Visible text: [Verify Now](http://appleid-verification-alert.net/restore)
Hover link: does not match Apple’s actual site

Legitimate Apple link would be:
https://appleid.apple.com

Verdict: Mismatch confirms phishing

7.	Verify Presence of Spelling or Grammar Errors
Observations:
•	Language is mostly clean, but:
o	Slightly off tone: “for your protection” + “secure link below” = generic phrasing
o	Missing personal info (e.g., user’s name)

Verdict: No glaring grammar errors, but tone is generic and unprofessional for Apple


8.	Summary of Phishing Traits Found:

Trait	Details	Verdict
Sender Spoofing	Mismatched domains: apple.com vs appleid-verification-alert.net	✅ Phishing
Header Discrepancies	SPF, DKIM, DMARC all failed	✅ Phishing
Suspicious Link	Fake Apple login domain	✅ Phishing
Urgent Language	Threat of suspension in 24 hrs	✅ Phishing
Mismatched URL	Displayed text ≠ real link	✅ Phishing
Spelling/Grammar	Mostly clean but overly generic	⚠️ Possibly Phishing
