---
lang: hi
lang-niv: auto
lang-ref: 051-IMP-programigo_gvidilo
layout: page
title: 'प्रोग्रामिंग गाइड'
---


एपिस 'प्रलेखन यहां देखा जा सकता है: (° 0001 डिग्री)  
* [चीनी में मूल संस्करण (° 0002 डिग्री) (डिग्री 0004 डिग्री)


* (डिग्री 0001 डिग्री) अंग्रेजी संस्करण (डिग्री 0002 डिग्री) (डिग्री डिग्री 0004 डिग्री)


* (° 0001 ° 1 ° 1 ° 1 ° 1 ° फ़्रेंच संस्करण Google द्वारा अनुवादित (° 0002 डिग्री) (° ° 0004 डिग्री)




# छोटा सा (Ingenic मीडिया प्लेटफ़ॉर्म) (छोटा सा भूत_system.h)देखें

## मूल अवधारणा
T20 / T21 प्रोग्रामिंग निम्नलिखित अवधारणाओं पर आधारित है:
1. परिधीय (= उपकरण)  
    परिधीय एक कार्य पूरा करता है। उदाहरण:
     *  फ़्रेम स्रोत: वीडियो डेटा का आउटपुट समाप्त करता है।
     *  एनकोडर: वीडियो एन्कोडिंग या छवि एन्कोडिंग फ़ंक्शन को पूरा करता है।
2. समूह  
    समूह सबसे छोटी डेटा इनपुट इकाई है। एक उपकरण में कई समूह हो सकते हैं और प्रत्येक समूह केवल एक डेटा इनपुट चैनल प्राप्त कर सकता है। समूह के कई परिणाम हो सकते हैं।  
    समूह विशिष्ट "कार्यों"के लिए एक कंटेनर भी है। अधिक विवरण के लिए चैनल अनुभाग में स्पष्टीकरण देखें।
3. बाहर निकलें  
    आउटपुट प्रति समूह डेटा आउटपुट की सबसे छोटी इकाई है। एक समूह में कई आउटपुट हो सकते हैं और प्रत्येक आउटपुट केवल एक डेटा चैनल का उत्पादन कर सकता है।
4. कोशिका  
    सेल एक संग्रह को संदर्भित करता है जिसमें डिवाइस, समूह और आउटपुट के बारे में जानकारी होती है। इसे IMPCell डेटा संरचना में प्रस्तुत किया गया है।
कोशिका मुख्य रूप से Bind (@ref बाइंड)के लिए उपयोग की जाती है। डिवाइस, ग्रुप और आउटपुट की परिभाषा के अनुसार, आउटपुट डेटा आउटपुट के लिए नोड है और डेटा इनपुट के लिए ग्रुप नोड है।
बिंद में, डेटा आउटपुट नोड का सेल इंडेक्स आउटपुट आउटपुट पर है, और डेटा इनपुट नोड का सेल इंडेक्स इनपुट ग्रुप (पर है ताकि सेल, आउटपुट डेटा इनपुट हो एक निरर्थक मूल्य)।
5. चैनल  
    चैनल आमतौर पर एकल फ़ंक्शन वाली इकाई को संदर्भित करता है। चैनल को एक विशिष्ट फ़ंक्शन प्राप्त होता है जब इसे बनाया जाता है (तात्कालिकता)।  
    उदाहरण के लिए:  
     -  एनकोडर के लिए, एक चैनल H264 कोड या JPEG एन्कोडिंग फ़ंक्शन का पूरक है। चैनल बनाते समय विशिष्ट एन्कोडिंग फ़ंक्शन (प्रकार, पैरामीटर) निर्दिष्ट किया जाता है


     -  आईवीएस के लिए, एक चैनल एक विशिष्ट एल्गोरिथ्म के कार्य को पूरा करता है और चैनल बनाते समय विशिष्ट एल्गोरिदम प्रकार निर्दिष्ट किए जाते हैं


     -  ओएसडी के लिए, चैनल के समान एक क्षेत्र है, क्षेत्र एक विशिष्ट ओवरले क्षेत्र है, जो PIC (छवि), COVER (बंद), और इसी तरह हो सकता है ।


     -  फ़्रेमसोर्स के लिए, एक चैनल एक मूल छवि का उत्पादन करता है और फ्रेमसोर्स चैनल वास्तव में एक समूहहै


     
     चैनल, एक कार्यात्मक इकाई के रूप में, आमतौर पर डेटा प्राप्त करने के लिए फ्रेमस्सोर्स) के अलावा समूह (में पंजीकृत होना चाहिए। चैनल समूह में पंजीकृत होने के बाद, यह समूह द्वारा दर्ज किया गया डेटा प्राप्त करेगा।

    विभिन्न उपकरणों के समूह द्वारा रिकॉर्ड किए जा सकने वाले चैनलों की संख्या भी भिन्न होती है।

## बाइंडिंग मॉड्यूल (बिंद)

एक बार दो समूह बिंद द्वारा जुड़े हुए हैं, स्रोत समूह से डेटा स्वचालित रूप से गंतव्य समूह को भेजा जाएगा।  
क्योंकि समूह सबसे छोटी डेटा इनपुट इकाई है और आउटपुट छोटा सा डेटा आउटपुट यूनिट, DeviceID, groupID और आउटपुट के दोनों मापदंडों में srcCell का IMP_System_बाइंड (इंस्पेनेल * है srcCell, IMPCell * dstCell) मान्य है।  

जबकि dstCell केवल डिवाइसआईडी और ग्रुपआईडी के लिए मान्य है, आउटपुट डेटा डेटा प्रविष्टि के रूप में कोई मतलब नहीं है।

उदाहरण 1: 
```
IMPCell fs_chn0 = {DEV_ID_FS, 0, 0};    // FrameSource deviceID: DEV_ID_FS groupID: 0 outputID: 0
IMPCell enc_grp0 = {DEV_ID_ENC, 0, 0}; // ENC deviceID: DEV_ID_ENC groupID : 0 outputID: 0, où le troisième paramètre de enc_grp0 n'a pas de sens. 
int ret = IMP_System_Bind (& fs_chn0, & enc_grp0);
if(ret <0>)
  printf ("Bind FrameSource Channel0 and Encoder Group0 failed \ n");

```

* एक समूह उत्पन्न होता है जो फ्रेमस्कोर से एनकोडर तक लिंक बनाता है।


* एनकोडर ग्रुप में दो चैनल रिकॉर्ड किए जाते हैं, इसलिए एनकोडर ग्रुप में दो आउटपुट H264 और JPEG हैं।



उदाहरण 2:
```
// flux de données principal
IMPCell fs_chn0 = {DEV_ID_FS, 0, 0};
IMPCell osd_grp0 = {DEV_ID_OSD, 0, 0};
IMPCell enc_grp0 = {DEV_ID_ENC, 0, 0};
int ret = IMP_System_Bind(&fs_chn0, &osd_grp0);
if (ret < 0)
    printf("Bind FrameSource Channel0 and OSD Group0 failed\n");

int ret = IMP_System_Bind(&osd_grp0, &enc_grp0);
if (ret < 0)
    printf("Bind OSD Group0 and Encoder Group0 failed\n");

// flux de données lié 
IMPCell fs_chn1_output0 = {DEV_ID_FS, 1, 0};
IMPCell ivs_grp0 = {DEV_ID_IVS, 0, 0};
IMPCell osd_grp1 = {DEV_ID_OSD, 1, 0};
IMPCell enc_grp1 = {DEV_ID_ENC, 1, 0};

int ret = IMP_System_Bind(&fs_chn1_output0, &ivs_grp0);
if (ret < 0)
    printf("Bind FrameSource Channel1 and IVS Group0 failed\n");

int ret = IMP_System_Bind(&ivs_grp0, &osd_grp1);
if (ret < 0)
    printf("Bind IVS Group0 and OSD Group1 failed\n");

int ret = IMP_System_Bind(&osd_grp1, &enc_grp1);
if (ret < 0)
    printf("Bind OSD Group1 and Encoder Group1 failed\n");
```
यह एक विशिष्ट बिंद कार्यक्रम है: एक दो-चैनल कोड स्ट्रीम।
 * फ़्रेमसोर्स के दो आउटपुट हैं, अर्थात् मुख्य धारा Channel0 (1280x720) और दास धारा Channel1 (640x360)।
   *   मुख्य धारा: फ्रेमसोर्स Channel0 Bind OSD Group.0, OSD Group.0 बाइंड एनकोडर Group.0। उनमें से: 
       * OSD Group.0 ने दो क्षेत्रों को रिकॉर्ड किया है जो क्रमशः टाइमस्टैम्प और चरित्र स्ट्रिंग जानकारी प्रदर्शित करने के लिए उपयोग किए जाते हैं
       *        * एनकोडर समूह .0 दो चैनल रिकॉर्ड किए गए। , जो क्रमशः H264 एन्कोडिंग और JPEG एन्कोडिंग हैं। उनमें से, अगर JPEG एन्कोडिंग चैनल की छवि का आकार फ्रेमस्कोर Channel0)के इनपुट पैरामीटर (से मेल नहीं खाता है, तो इसे T10) पर स्केल किया जाएगा (सॉफ़्टवेयर) किसी भी रिज़ॉल्यूशन पर कब्जा करने का लक्ष्य प्राप्त करें।
       
नोट्स:
* यह अनुशंसा की जाती है कि सभी लिंक ऑपरेशन सिस्टम इनिशियलाइज़ेशन के दौरान किए जाएँ।
* Bind और UnBind संचालन सक्रिय रूप से _FrameSource_ सक्रिय होने के बाद नहीं कहा जा सकता है। UnBind निष्क्रिय होने के बाद ही किया जाता है _FrameSource_।

## कार्यों

### int छोटा सा भूत\_सिस्टम\_Init (खाली )
आईएमपी प्रणाली का प्रारंभ।
रिटर्न 0 सफल होने पर।
इस एपीआई कॉल के बाद, बुनियादी डेटा संरचना को इनिशियलाइज़ किया जाएगा, लेकिन हार्डवेयर को इनिशियलाइज़ नहीं किया जाएगा।
ध्यान: यह फ़ंक्शन किसी अन्य ऑपरेशन से पहले दीक्षा के लिए बुलाया जाना चाहिए।
### int छोटा सा भूत_System_आउटपुट (खाली)

इस फ़ंक्शन को कॉल करने के बाद, सभी मेमोरी और IMP _handles_ जारी किए जाएंगे, और हार्डवेयर बंद हो जाएगा। 
नोट: इस API को कॉल करने के बाद, यदि आप फिर से IMP का उपयोग करना चाहते हैं, तो आपको IMP सिस्टम को रीसेट करना होगा।

### int64_t IMP_सिस्टम_GetTimeStamp (void)

माइक्रोसेकंड में छोटा सिस्टम टाइमस्टैम्प प्राप्त करें।  
वापसी: माइक्रोसेकंड में समय।

### int छोटा सा भूत_System_RebaseTimeStamp (आधार int64_t)
छोटा सा भूत टाइमस्टैम्प को माइक्रोसेकंड में सेट करें।  
वापसी: 0 यदि सफल हो।

### uint32_t IMP_सिस्टम_ReadReg32 (uint32_t u32Addr)

32-बिट रजिस्टर का मूल्य पढ़ें।  

### रिक्त IMP_System_WriteReg32 (uint32_t regAddr, valeur uint32_t (
मान को 32-बिट रजिस्टर में लिखें।

नोट: कृपया इस एपीआई को सावधानीपूर्वक कॉल करें और रजिस्ट्री के अर्थ की जांच करें, अन्यथा यह सिस्टम त्रुटियों का कारण हो सकता है।

### int छोटा सा भूत_System_GetVersion (IMPVersion * pstVersion) 

IMP सिस्टम का वर्जन नंबर प्राप्त करें।

### const char * छोटा_System_GetCPUInfo (खाली_System_
सीपीयू मॉडल के बारे में जानकारी प्राप्त करें।  
नोट: रिटर्न मान CPU मॉडल का एक स्ट्रिंग है, उदाहरण के लिए, T10 के लिए "T10"और "T10-Lite"है।

### int IMP_System_बिंद (IMPCell * srcCell, IMPCell * dstCell)

स्रोत सेल और गंतव्य के बीच लिंक।

नोट 1: डिवाइस, समूह और आउटपुट की अवधारणाओं के अनुसार, प्रत्येक डिवाइस में कई समूह हो सकते हैं, और प्रत्येक समूह में कई आउटपुट हो सकते हैं, समूह का उपयोग डिवाइस इनपुट इंटरफ़ेस के रूप में किया जाता है, और आउटपुट का उपयोग डिवाइस उत्पाद इंटरफ़ेस के रूप में किया जाता है। इसलिए लिंक वास्तव में आउटपुट डिवाइस के एक निश्चित समूह को इनपुट डिवाइस के एक निश्चित समूह से जोड़ता है।

नोट 2: एक सफल लिंक के बाद, srcCell (आउटपुट) द्वारा उत्पन्न डेटा स्वचालित रूप से गंतव्य सेल (समूह)तक पहुंच जाएगा।

### int IMP_System_UnBind (IMPCell * srcCell, IMPCell * dstCell)
स्रोतों और गंतव्यों को अनग्रुप करें। 

### int छोटा सा भूत_System_GetBindbyDest (IMPCell * dstCell, IMPCell * srcCell)

गंतव्य से संबंधित स्रोत सेल से जानकारी प्राप्त करता है।




