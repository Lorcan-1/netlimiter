# netlimiter
**A short guide for how to crack netlimiter for use in online video games**

**The default file path for netlimiter is C:\Program Files\Locktime Software\NetLimiter 4**

## Prerequisites
To follow this guide, you will need the following software:

1. **NetLimiter 4.1.13**  
   You can download NetLimiter version 4.1.13 [here](https://www.netlimiter.com/download/nl4/NetLimiterSetup_4.1.13.exe).

2. **dnSpy**  
   Download dnSpy from the official GitHub repository:  
   [dnSpy v6.1.8 - Windows 64-bit](https://github.com/dnSpy/dnSpy/releases/download/v6.1.8/dnSpy-net-win64.zip).

## Crack
1. **Open netlimiter.dll in DNSPY**
2. **Select the dropdown for `netlimiter.dll`.**
3. **Scroll down and perform the same action for `NetLimiter service`.**
4. **Finally, locate and select `nllicense`, which can also be found on line 97 of `netlimiterservice`.**
5. **Right click and select edit class within NLlicense and paste the below then press compile**
```cs
using System;
using System.Runtime.Serialization;

namespace NetLimiter.Service
{
    // Token: 0x0200006F RID: 111
    [DataContract]
    public class NLLicense
    {
        // Token: 0x1700007B RID: 123
        // (get) Token: 0x06000269 RID: 617 RVA: 0x0000372C File Offset: 0x0000192C
        // (set) Token: 0x0600026A RID: 618 RVA: 0x00003734 File Offset: 0x00001934
        [DataMember]
        public string ProductCode { get; protected set; }

        // Token: 0x1700007C RID: 124
        // (get) Token: 0x0600026B RID: 619 RVA: 0x0000373D File Offset: 0x0000193D
        // (set) Token: 0x0600026C RID: 620 RVA: 0x00003745 File Offset: 0x00001945
        [DataMember]
        public int Quantity { get; set; }

        // Token: 0x1700007D RID: 125
        // (get) Token: 0x0600026D RID: 621 RVA: 0x0000374E File Offset: 0x0000194E
        // (set) Token: 0x0600026E RID: 622 RVA: 0x00003756 File Offset: 0x00001956
        [DataMember]
        public NLLicenseType LicenseType { get; set; }

        // Token: 0x1700007E RID: 126
        // (get) Token: 0x0600026F RID: 623 RVA: 0x0000375F File Offset: 0x0000195F
        // (set) Token: 0x06000270 RID: 624 RVA: 0x00003767 File Offset: 0x00001967
        [DataMember]
        public string RegistrationName { get; set; }

        // Token: 0x1700007F RID: 127
        // (get) Token: 0x06000271 RID: 625 RVA: 0x00003770 File Offset: 0x00001970
        // (set) Token: 0x06000272 RID: 626 RVA: 0x00003778 File Offset: 0x00001978
        [DataMember]
        public DateTime Expiration { get; set; }

        // Token: 0x17000080 RID: 128
        // (get) Token: 0x06000273 RID: 627 RVA: 0x00003781 File Offset: 0x00001981
        // (set) Token: 0x06000274 RID: 628 RVA: 0x00003789 File Offset: 0x00001989
        [DataMember]
        public bool IsTestingVersion { get; set; }

        // Token: 0x17000081 RID: 129
        // (get) Token: 0x06000275 RID: 629 RVA: 0x00003792 File Offset: 0x00001992
        // (set) Token: 0x06000276 RID: 630 RVA: 0x0000379A File Offset: 0x0000199A
        [DataMember]
        public bool IsRegistered { get; set; }

        // Token: 0x17000082 RID: 130
        // (get) Token: 0x06000277 RID: 631 RVA: 0x000037A3 File Offset: 0x000019A3
        // (set) Token: 0x06000278 RID: 632 RVA: 0x000037AB File Offset: 0x000019AB
        [DataMember]
        public SupportedFeatures SupporetedFeatures { get; protected set; }

        // Token: 0x17000083 RID: 131
        // (get) Token: 0x06000279 RID: 633 RVA: 0x000037B4 File Offset: 0x000019B4
        public bool IsExpired
        {
            get
            {
                return false;
            }
        }

        // Token: 0x17000084 RID: 132
        // (get) Token: 0x0600027A RID: 634 RVA: 0x0000DA38 File Offset: 0x0000BC38
        public int DaysLeft
        {
            get
            {
                if (!this.HasExpiration)
                {
                    return 9999;
                }
                int num = (int)Math.Ceiling((this.Expiration - DateTime.UtcNow).TotalDays);
                if (num <= 0)
                {
                    return 9999;
                }
                return num;
            }
        }

        // Token: 0x17000085 RID: 133
        // (get) Token: 0x0600027B RID: 635 RVA: 0x000037B7 File Offset: 0x000019B7
        public bool HasExpiration
        {
            get
            {
                return this.Expiration != DateTime.MaxValue;
            }
        }

        // Token: 0x0600027C RID: 636 RVA: 0x000037C9 File Offset: 0x000019C9
        public NLLicense(string productCode = null)
        {
            this.Expiration = DateTime.MaxValue;
            this.ProductCode = productCode;
            this.SupporetedFeatures = new SupportedFeatures(productCode);
        }
    }
}
```
6. **finally save the file**

## Avoiding TItle detection
1. **open NLclientapp.core.dll in DNSPY**
2. **Select the dropdown for `NLClientAPP.Core`.**
3. **Scroll down to `ViewModels`.**
4. **Find `MainVM`, which can be located on line 38 of the file.**
5. **Scroll to line 573 you should see this.NLAppVerName = "Netlimiter 4";
6. **Right click and Edit IL instructions**
7. **Scroll to line 109 and edit "Netlimiter 4" to whatever you want your title name to be then select ok**
8. **save the file**
9. **Open your netlimiter folder located at C:\Program Files\Locktime Software\NetLimiter 4**
 10. **Rename the NLClientapp file to anything you want then open it**



