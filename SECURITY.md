# Zowe Respond to Vulnerability Policy
## Security issues identification
<!-- <span style="display:none" hidden>(Zowe-SSDP-SDLC - #ID: ZSSD-LP:RV-ICV)</span> -->

### Code review and tests
<!--
<div style="display: none;">(Zowe-SSDP-SDLC: C7. Test Executable Code - #ID: ZSSD-LP:PW-TEC)</div>
<span style="display:none">(Zowe-SSDP-SDLC - #ID: ZSSD-LP:RV-ICV-CRT)</span>
-->

* The security architecture of all Zowe projects is reviewed by the Security Workgroup.
* The squads perform internal security code review of newly implemented features and other security related code changes.
* The code reviews are performed by squad members other than the individuals who created the code.
* The squads continuously perform security testing for security issues in their projects' code and configuration.
* A full penetration testing is performed by the Security Workgroup before each major release.

### Vulnerability monitoring</h3>
<!-- Zowe-SSDP-SDLC #ID: ZSSD-LP:RV-ICV-PVM -->

The Security Workgroup continuously monitors well known sources of information about discovered or otherwise severe security issues. Some sources a listed below:
  * [NIST National Vulnerability Database](https://nvd.nist.gov/vuln)
  * [MITRE CVE List](https://cve.mitre.org/)
  * [Snyk Vulnerability DB](https://security.snyk.io/)
  * [CISA Exploited Vulnerabilities Catalog](https://www.cisa.gov/known-exploited-vulnerabilities-catalog)
   
   
Any issues found to have impact on Zowe projects, are further [analyzed](#Analysis-And-Assessment) without unnecessary delay.

Information about any identified issues is propagated by the Security Workgroup to the squads for [mitigation](#Security-Issues-Mitigation).  
    
### Security issues reporting
<!-- Zowe-SSDP-SDLC #ID: ZSSD-LP:RV-ICV-PVM -->

Zowe encourages the community, users and security researchers to perform testing and report vulnerabilities.  

<!-- #TODO: Publish the reporting process on the project web-site: Open SSF: FLOSS Best Practices Criteria  - Vulnerability report process -->

Please direct all security issues to <code>zowe-security@lists.openmainframeproject.org</code>.

To help Zowe developers understand and resolve the issues, please provide accurate details. 

#### Security report template

Please fill in as much as you can of the following template fields:
````
  - General
    - Date discovered
    - Severity
    - Impact
      
  - Reporter information  
    - Full name 
    - Contact - preferably e-mail
    - Organization (optional)
    
  - Environment
    - Operating platform: Win (32/64), Linux (flavor), MacOS (pre-M1 / M1)
    - Hosted (optional):  (y,n,N/A) - (Eclipse Che, Theia, CRW, ...)
    - z/OS (optional) 
      - Version
      - Security manager 
      - Related products names and versions
    - Zowe
      - Version
      - Sub-component/s name and version
  
  - Issue description   
    - Short (one liner) summary
    - Detailed information - pre-conditions, access rights,   
    - Steps to reproduce
````

Additional hints and recommendations:
````
    - While testing or replicating the vulnerability take notes, snapshots, collect log files.
    - Start with a summary.
    - Detail the narrative.
    - Follow the form.
    - Proofread.
    - Avoid emotional language.
    - Avoid abbreviations and conjunctions.
    - Be prompt.
````

#### What happens after security report is received by the Security Workgroup 
* After your report is received, a member of the Security Workgroup replies to acknowledge receipt of the report.
* The reporter may be contacted for clarification.
* Without unnecessary delay the report is [analyzed](#Analysis-And-Assessment).

<!-- **IMPORTANT:**  Please do not file a public issue [disclosing vulnerabilities](#Security-issues-disclosure) as this may be misused by violent attackers. -->
    Note 1: We encourage the reporters to work with the Security Workgroup team to resolve the issue before going publicly with it.

    Note 2: Security vulnerabilities identified through own testing or reported by community members, and which don't yet have assigned a CVE, are reported by the Zowe Security Workgroup to a CVE Numbering Authorityu (CNA).     

## Analysis and assessment 
<!--
    (Zowe-SSDP-SDLC #ID: ZSSD-LP:RV-ARV)
    (Zowe-SSDP-SDLC #ID: ZSSD-LP:RV-ARV-AEV)
    (NIST-SSF: #REF: SSDF:RV.2.1)
-->

* Reported issues are analyzed within the security workgroup.
* The issues' analyzes outcome is determined by the risk severity measured by the combination of vulnerability exploitability and its impact. 

The severity can be one of the:
  * Critical (C) - An event that, if it occurred, would cause program failure (inability to achieve minimum acceptable requirements).
  
        Critical issues are fixed as early as possible

  * High (H) - An event that, if it occurred, would cause major cost and schedule increases. Secondary requirements may not be achieved.
  
        High issues are fixed within next minor/patch release as latest. 
        Alternatively, There are no un-patched vulnerabilities of High severity that have been publicly known for more than 60 days. [vulnerabilities_fixed_60_days policy]

  * Medium (M) - An event that, if it occurred, would cause moderate cost and schedule increases, but important requirements would still be met.
    
        Medium issues are fixed when the squad decides to fix 

  * Low (L) - An event that, if it occurred, would cause only a small cost and schedule increase. Requirements would still be achieved.   

        Low issues are fixed when the squad decides to fix
 
## Security issues mitigation

 After the issue is sufficiently documented, the Security Workgroup coordinates the issue [mitigation](#Security-issues-mitigation).
<!--
    (Zowe-SSDP-SDLC #ID: ZSSD-LP:RV-ARV)
    (NIST-SSF #REF: SSF-A.4.2-B)
-->

The Zowe squads strive to fix the relevant security issues according to their assessed priority within a predefined timeframe. [vulnerabilities_critical_fixed policy]

<!-- 
    (NIST-SSF #REF: SSF-A.4.1-B)
-->

## Security issues disclosure

* Zowe discloses fixed vulnerabilities in a timely manner giving the users sufficient time to plan their upgrades. 
* We however don't disclose the vulnerabilities fixed in the latest release as we respect the need for at least 45 days to decide when and how will the users upgrade. 
* When a new release is published, the project list the vulnerabilities fixed in the previous release.
    
      For example when we'd release Zowe v2.3 we'd publish the list of vulnerabilities that were fixed in the version 2.2 .
      The issues that were fixed would be published in the [Zowe security reports](https://github.com/zowe/security-reports/blob/master/security-vulnerabilities.md) repository listing.

## Solution publishing
### Security advisory
* The project's squad discloses a vulnerability by first creating a draft security advisory in the project repository in GitHub.
* For critical priority vulnerability, security patches are created as soon as the issue is fixed in code and configuration.
* The security fixes become an integral part of the latest Zowe distribution.


    Note: GitHub Security Advisories allow the squad to privately discuss and fix a security vulnerability in their project.
* After collaborating on a fix, the project maintainers publish the security advisory to a project specific place.
  * Will add them to NIST list of issues. TODO: CHeck how is this done.
  * Publish the one that we already fixed. See Mitre: https://cveform.mitre.org/
        

    Note: Projects hosted in GitHub take advantage of the GH features providing special security advisory dedicated pages.   
          See: https://docs.github.com/en/code-security/repository-security-advisories/creating-a-repository-security-advisory

### Security updates 
Security notifications are distributed by the following methods.

* Publishing project specific advisories in the corresponding project GitHub repository Security page.
  * TODO: Check GitHub allows security page for a project


    For example you can find the API Mediation Layer related security advisories here: https://github.com/zowe/api-layer/security/advisories   
* Notification to Zowe users who explicitly signed in for receiving security alerts and advisories. 
       
          #TODO: Subscribe to the mailing lists or apply using  form to apply???
  * <code>zowe-user@lists.openmainframeproject.org</code>
  * <code>zowe-dev@lists.openmainframeproject.org</code>

<!--
## Reporting a Vulnerability

Please direct all security issues to `zowe-security@lists.openmainframeproject.org`. A member of the security team will reply to acknowledge receipt of the vulnerability and coordinate remediation with the affected project.
-->
