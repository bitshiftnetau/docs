---
description: Understand how Auth0 detects anomalies to stop malicious attempts to access your application, alert you and your users of suspicious activity, and block further login attempts. 
topics:
    - security
    - anomaly-detection
    - credential-stuffing
contentType: concept
useCase: anomaly-detection
---
# Automated Attack and Credential Stuffing Protection

Credential stuffing attacks (or *list validation attacks*) occur when bad actors automate the process of trying username and password combinations (usually stolen from another site) for many accounts in a short period of time.  According to recent statistics, as many as 71% of accounts use the same password across multiple sites so a credential stuffing attack represents a legitimate threat to your system.  

Use **Automated Attack Protection** to provide a standard level of protection against credential stuffing attacks with minimal friction for legitimate users. This protection is enabled by default for all connections.  

::: panel Credential Stuffing Attacks: What Are They and How to Combat Them
Download this free [whitepaper](https://auth0.com/resources/whitepapers/credential-stuffing-attacks) to learn how Auth0 can help you combat credential stuffing attacks.
:::

## How it works

Auth0 uses a large amount of data to identify patterns that signal that a credential stuffing attack is taking place. Auth0 uses data statistical models to determine when bursts of traffic are likely to be from a bot or script. Users attempting to sign in from IPs which are determined to have a high likelihood of being a credential stuffing attack will see a CAPTCHA step. The triggers are designed so that this only happens for bad traffic; the objective is to not show any friction to legitimate users. This block remains in place until the user changes their password.

![CAPTCHA Login Screen Example](/media/articles/anomaly-detection/captcha-login-screen.png)

## Restrictions and limitations

Automated Attack Protection works for web and mobile apps that uses Auth0's Universal Login. This feature is not supported in the sign up or account recovery flows. This protection works on most authentication flows but not all.

| Flow | Limitation | 
| -- | -- |
| New Universal Login | Works automatically (if enabled which is the default). |
| Classic Universal Login (Lock) | Works with Lock v11.20 or higher. |
| Classic Universal Login (auth0.js) | Works automatically. |
| `/oauth/token` | Returns an error message "Suspicious request requires validation" when an error code `requires_validation` occurs. You may need to modify your app to accommodate this error case. |
| Embedded Login | Does **not** work in this case. |

## Keep reading

* [Set Anomaly Detection Preferences](/anomaly-detection/guides/set-anomaly-detection-preferences)
* [Customize Blocked Account Emails](/anomaly-detection/guides/customize-blocked-account-emails)
* [View Anomaly Detection Events](/anomaly-detection/guides/view-anomaly-detection-events)