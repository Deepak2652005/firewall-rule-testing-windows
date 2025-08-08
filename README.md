# firewall-rule-testing-windows

Firewall Configuration Project - Task 4 

🎯 Project Overview 

This repository documents my hands-on experience with firewall configuration and network traffic filtering as part of the Cyber Security Internship program. The objective was to configure and test basic firewall rules to understand network security fundamentals using Windows Defender Firewall. 

🖥️ Platform Used 

Operating System: Windows 11 

 Firewall Tool: Windows Defender Firewall with Advanced Security 

 Testing Environment: Local machine (localhost) 

 Access Method: GUI interface and Command Line (netsh) 

✅ Objectives Accomplished 

    [x] Analyzed current firewall configuration and rules 

    [x] Created inbound rule to block traffic on port 23 (Telnet) 

    [x] Tested the block rule to verify functionality 

    [x] Created allow rule for specific application/port 

    [x] Removed test rules to restore original configuration 

    [x] Documented entire process with screenshots and commands 

🛡️ Firewall Rules Implemented 

1. Block Rule: Telnet Port 23 

    Rule Name: Block Telnet Inbound 

    Direction: Inbound 

    Action: Block the connection 

    Protocol: TCP 

    Port: 23 (Telnet) 

    Profiles: Domain, Private, Public 

    Reason: Telnet transmits data in plaintext (major security risk) 

2. Allow Rule: Custom Application 

    Rule Name: Allow Test Application 

    Direction: Inbound 

    Action: Allow the connection 

    Protocol: TCP 

    Port: [Specific port used] 

    Profiles: Private 

    Reason: Demonstrate allow rule configuration 

📋 Configuration Steps Performed 

Step 1: Access Windows Firewall 

    Opened Run dialog (Win + R) 

    Typed wf.msc to open Windows Defender Firewall with Advanced Security 

    Reviewed existing inbound and outbound rules 

Step 2: Create Block Rule for Telnet 

    Right-clicked "Inbound Rules" → "New Rule..." 

    Selected "Port" rule type 

    Chose "TCP" protocol and "Specific Local Ports: 23" 

    Selected "Block the connection" 

    Applied to all profiles (Domain, Private, Public) 

    Named the rule "Block Telnet Inbound" 

    Added description: "Block insecure Telnet connections" 

Step 3: Test Block Rule 

    Opened Command Prompt 

    Attempted Telnet connection: telnet localhost 23 

    Verified connection was refused/blocked 

    Checked Windows Event Viewer for firewall block events 

Step 4: Create Allow Rule (Demonstration) 

    Right-clicked "Inbound Rules" → "New Rule..." 

    Selected "Port" rule type 

    Configured specific port for testing 

    Selected "Allow the connection" 

    Applied to appropriate profile 

    Named and documented the rule 

Step 5: Cleanup and Restoration 

    Located created test rules 

    Right-clicked each rule → "Delete" 

    Confirmed deletion 

    Verified original firewall state restored 

🧪 Testing Process 

1. Baseline Testing 

    Documented initial firewall configuration 

    Counted existing inbound rules: [X rules] 

    Counted existing outbound rules: [Y rules] 

    Verified Windows Firewall service status 

2. Block Rule Testing 

# Attempted Telnet connection to localhost 
telnet localhost 23 
 
# Expected Result: "Could not open connection to the host" 
# Actual Result: Connection blocked successfully ✅ 
  

3. Rule Verification 

    Confirmed rule appears in Windows Firewall interface 

    Verified rule properties and settings 

    Checked rule is enabled and active 

4. Event Log Verification 

    Opened Windows Event Viewer 

    Navigated to Windows Logs → Security 

    Found firewall block events (Event ID 5152/5157) 

    Confirmed blocked connection attempts logged 

📊 Results Summary 

Test 
	

Expected Result 
	

Actual Result 
	

Status 

Block Telnet (Port 23) 
	

Connection refused 
	

Connection blocked 
	

✅ Pass 

Rule Creation 
	

Rule appears in firewall 
	

Rule visible and active 
	

✅ Pass 

Event Logging 
	

Block events logged 
	

Events recorded in Event Viewer 
	

✅ Pass 

Rule Cleanup 
	

Rules removed successfully 
	

Original state restored 
	

✅ Pass 

🔍 Key Findings 

Windows Firewall Insights 

    Default configuration includes many predefined rules for Windows services 

    Rule precedence follows specific order - block rules can override allow rules 

    Profile-based rules allow different security levels for different network types 

    Event logging provides detailed audit trail of firewall actions 

    GUI interface is user-friendly but command-line offers automation potential 

Security Observations 

    Windows Firewall is enabled by default with reasonable security posture 

    Many Windows services have automatic firewall exceptions 

    Inbound traffic is generally more restricted than outbound 

    Public profile has strictest default rules 

🛠️ Command Line Interface 

Commands Used for Verification: 

# Display all firewall rules 
netsh advfirewall firewall show rule name=all 
 
# Show specific rule details 
netsh advfirewall firewall show rule name="Block Telnet Inbound" 
 
# Check firewall status 
netsh advfirewall show allprofiles 
 
# Test connectivity 
telnet localhost 23 
ping localhost 
 
# Alternative: PowerShell commands 
Get-NetFirewallRule | Where-Object DisplayName -like "*Block*" 
  

🎓 Skills Developed 

Technical Skills 

    Windows Firewall administration through GUI interface 

    Rule creation and management for inbound/outbound traffic 

    Network testing using built-in Windows tools 

    Event log analysis for security monitoring 

    Command-line firewall management using netsh 

Security Concepts Mastered 

    Network access control principles 

    Defense in depth strategy implementation 

    Risk-based security (blocking high-risk services) 

    Audit logging for security events 

    Profile-based security for different network environments 

🚫 Troubleshooting Encountered 

Issue 1: Administrative Rights 

Problem: Could not access Advanced Security settings initially 

 Solution: Right-clicked and selected "Run as Administrator" 

 Learning: Firewall management requires elevated privileges 

Issue 2: Rule Conflicts 

Problem: Uncertain about rule precedence and conflicts 

 Solution: Researched Windows Firewall rule processing order 

 Learning: Block rules generally take precedence over allow rules 

Issue 3: Telnet Client Missing 

Problem: telnet command not recognized 

 Solution: Enabled Telnet Client through Windows Features 

 Learning: Some networking tools are optional Windows components 

📚 Interview Preparation 

Based on this hands-on experience with Windows Firewall, I can now answer: 

    What is a firewall? A network security system that monitors and filters incoming/outgoing traffic based on predetermined security rules. Windows Defender Firewall protects individual computers from network-based attacks. 

    Stateful vs Stateless firewalls? Windows Defender Firewall is stateful - it tracks connection states and allows return traffic for established connections, providing better security than stateless packet filtering. 

    Inbound vs Outbound rules? 

    Inbound: Control traffic coming TO your computer (more restrictive by default) 

    Outbound: Control traffic going FROM your computer (generally more permissive) 

    How does UFW simplify firewall management? While I used Windows Firewall, UFW on Linux provides similar simplification by offering easy-to-use commands instead of complex iptables syntax. 

    Why block port 23 (Telnet)? Telnet sends all data including passwords in plaintext, making it vulnerable to network sniffing and man-in-the-middle attacks. SSH (port 22) should be used instead. 

    Common firewall mistakes? 

    Not testing rules after creation 

    Creating overly permissive rules 

    Forgetting to apply rules to appropriate profiles 

    Not documenting rule purposes 

    Blocking essential Windows services 

    How does a firewall improve network security? 

    Reduces attack surface by blocking unused ports 

    Prevents unauthorized network access 

    Logs security events for monitoring 

    Provides different security levels for different network types 

    What is NAT in firewalls? Network Address Translation hides internal network structure and provides additional security layer, though Windows Firewall focuses more on port/protocol filtering than NAT functionality. 

🔄 Next Steps 

Immediate Actions 

    [x] Complete comprehensive documentation 

    [ ] Research Windows Firewall logging capabilities 

    [ ] Study integration with Windows Security Center 

Future Learning Objectives 

    [ ] Explore PowerShell firewall management cmdlets 

    [ ] Learn about Windows Firewall with Group Policy 

    [ ] Study enterprise firewall solutions (pfSense, FortiGate) 

    [ ] Practice with complex rule scenarios and exceptions 

    [ ] Investigate Windows Defender Application Guard 

💡 Key Takeaways 

Professional Insights 

    GUI vs CLI: Windows provides both interfaces - GUI for ease of use, CLI for automation 

    Documentation matters: Proper rule naming and descriptions are crucial for management 

    Testing is essential: Rules must be verified to ensure they work as intended 

    Security by default: Windows Firewall provides good baseline protection out-of-the-box 

Personal Development 

    Gained confidence in Windows security administration 

    Developed systematic approach to security testing 

    Learned importance of thorough documentation 

    Enhanced troubleshooting and problem-solving skills 

⚠️ Important Security Notes 

    All testing performed on personal computer with full authorization 

    No unauthorized network access attempts made 

    Test rules properly removed to maintain system security 

    Educational exercise conducted in controlled environment 

    Firewall remains active with appropriate security settings 

📖 References and Resources 

    Microsoft Windows Defender Firewall Documentation 

    Netsh AdvFirewall Commands 

    Windows Firewall Event IDs 

    Network Security Best Practices 

    Common Ports and Services 

 

Project Completion Date: [Current Date] 

 Total Time Investment: Approximately 2 hours 

 Skill Level Achieved: Intermediate Windows Firewall Administration 

 Primary Learning Outcome: Network security through host-based access control 

 
