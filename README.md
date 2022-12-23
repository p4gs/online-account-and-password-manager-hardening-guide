# Hardening your password manager and online accounts
This guide was developed based on [part 2](https://justinpagano.substack.com/p/protecting-against-a-password-manager-8f6) of the blog post series _[Protecting against a password manager breach](https://justinpagano.substack.com/p/protecting-against-a-password-manager)_. More context can be found in both posts about why certain apps and technology are recommended over others.

![Personal password vault reference architecture](https://user-images.githubusercontent.com/10093271/209345022-7ffad2e9-6340-4e5a-9015-cbf43ca3379a.svg)

#### Securely setup 1Password

> _Setup 1Password for storing passwords and password equivalents, such as security question answers_

- [ ] Use a unique [passphrase](https://diceware.rempe.us/#eff) for logging into 1Password
- [ ] Setup [MFA with YubiKeys only](https://support.1password.com/security-key/)
- [ ] Store your 1Password passphrase in a secure place ([fireproof safe](https://www.nytimes.com/wirecutter/reviews/best-fireproof-document-safe/) = better security, Apple Keychain = better usability)
- [ ] Your 1Password Secret Key can be stored in the same place since [it's designed to be](https://support.1password.com/secret-key-security/#how-your-secret-key-protects-you) an entropy-boosting addition to your password

#### Harden foundational accounts

> _These are accounts that, if compromised, could be used to reset account passwords or access Passkeys._

- [ ] Ensure email account has a strong password and MFA setup with YubiKeys
- [ ] Use Gmail (Google’s security is top notch). If you're extra paranoid, use Protonmail
- [ ] Ensure Apple ID has strong password and MFA setup with YubiKeys

#### Protect against SMS MFA code theft

> _Some of your accounts may still only support SMS MFA codes (and any form of MFA is better than no MFA). Similarly, some sites and apps, such as Authy, use mobile phone numbers for account creation. Hardening your mobile phone number and account is essential in these contexts._

- [ ] Create a strong password for your mobile carrier online account
- [ ] Setup MFA on your mobile carrier online account
- [ ] Setup a mobile carrier PIN to protect against [SIM hijacking](https://www.verizon.com/about/account-security/sim-swapping) (here are guides for [Verizon](https://www.verizon.com/support/account-pin-faqs/), [T-Mobile](https://www.t-mobile.com/support/account/update-your-customer-pinpasscode), [AT&T](https://www.att.com/support/article/wireless/KM1051385), [Sprint](https://www.sprint.com/en/support/solutions/account-and-billing/learn-more-about-your-account-pin.html), [Cricket](https://www.cricketwireless.com/support/protect-my-phone/account-pin-security.html))
- [ ] Setup Google Voice number to be used for SMS MFA (you can disassociate it from your mobile phone number later on for added security)
  - [ ] Ensure Google Account has strong password and YubiKey-only MFA enabled

#### Securely setup Authy

> _Use Authy whenever time-based one-time passcode (TOTP aka “Google Authenticator”) MFA is the most secure option available. If you’re extra paranoid and are willing to make some usability sacrifices, try storing your MFA codes in a YubiKey and use [Yubico Authenticator](https://www.yubico.com/products/yubico-authenticator/) to access them_

- [ ] Setup Authy using your Google Voice number
- [ ] Enable [Authy Backups](https://support.authy.com/hc/en-us/articles/115001750008-Backups-and-Sync-in-Authy) and create/store a randomly generated Backup Password with 1Password
- [ ] Disable [Authy Multi-Device](https://support.authy.com/hc/en-us/articles/360016317013-Enable-or-Disable-Authy-Multi-Device) access and only re-enable when you're setting up Authy on another device
  - [ ] If you are able to, install Authy on at least two devices so you don't have to go through a painful account recovery process if your only Authy-installed device breaks, is lost, etc.

> _NOTE: Because computer OSes are more at risk of being affected by various kinds of malware, you should only install Authy on iPhones and iPads._

#### Securely setup BitWarden

> _Setup BitWarden for storing TOTP MFA recovery codes and MFA recovery code equivalents such as seed keys._

- [ ] Setup a BitWarden account using an email address from a different provider
  - [ ] E.g. if you used Gmail for your 1Password account and other accounts, use Protonmail for your BitWarden account
- [ ] Use a unique [passphrase](https://diceware.rempe.us/#eff) for logging into BitWarden
  - [ ] Store your BitWarden passphrase in a secure place (fireproof safe = better security, Apple Keychain = better usability) but**not** in your 1Password vault
- [ ] If you're already paying for BitWarden, setup MFA with YubiKeys only. Otherwise, setup TOTP MFA codes using Authy

#### Enable MFA everywhere you can

- [ ] Use [1Password Watchtower](https://support.1password.com/watchtower/#identify-logins-that-support-two-factor-authentication) to identify accounts that support MFA and ensure MFA is setup on all of  them
- [ ] Explore [2fa.directory](https://2fa.directory) to identify additional accounts that support MFA and ensure MFA is setup on all of them

#### Change compromised and vulnerable passwords

- [ ] Use [1Password Watchtower](https://support.1password.com/watchtower/#find-compromised-websites-and-vulnerable-passwords) to identify passwords of yours that have been caught up in past data breaches
- [ ] Change each compromised or vulnerable password

#### Change weak and reused passwords

- [ ] Use [1Password Watchtower](https://support.1password.com/watchtower/#find-compromised-websites-and-vulnerable-passwords) to identify weak and reused passwords of yours
- [ ] Change each weak or reused password
- [ ] Replace passwords with Passkeys (WebAuthN) [where possible](https://passkeys.directory)

#### Detect account compromises as they happen

- [ ] Setup email rules for new device login, suspicious login, password reset, and MFA change notifications
- [ ] Start treating rogue SMS MFA codes and push notification MFA prompts with suspicion, changing passwords when benign cause of rogue codes/prompts can't be identified
  - [ ] _Especially_ if you receive a message from someone who claims to need your MFA codes or for you to approve push notifications. If this happens, change passwords and report to your account provider ASAP
