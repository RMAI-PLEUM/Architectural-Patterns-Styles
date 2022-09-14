## Architectural Patterns Styles Homework

## ศุภเกียรติ ธัญญะประกอบ 63010930


## Matplotlib

Matplotlib คือ ไลบรารี่ที่ครอบคลุม creating static, animated, and interactive visualizations ด้วย Python.

### architectural patterns/styles

รูปแบบสถาปัตยกรรมที่ Matplotlib ใช้คือรูปแบบ **Layer architectural** 

**Scripting layer** เป็น layer ที่ใช้สำหรับการเขียนโปรแกรม โดยในส่วนนี้จะเป็นการเขียนโปรแกรมเพื่อใช้งานกับ Matplotlib โดยจะเขียนโปรแกรมเพื่อสร้างกราฟ และส่วนนี้จะเป็นส่วนที่ผู้ใช้งานสามารถเขียนโปรแกรมเพื่อใช้งานกับ Matplotlib ได้

**Artist Layer** เป็น layer ที่ช่วยให้ควบคุมและปรับจูนของ figure เช่น spines, tick direction, tick label size, tick label font, tick color. โดยในส่วนนี้จะเป็นการสร้าง figure และส่วนนี้จะเป็นส่วนที่ผู้ใช้งานสามารถเขียนโปรแกรมเพื่อใช้งานกับ Matplotlib ได้

**Backend Layer** เป็น layer ที่ใช้สำหรับการแสดงผลของ figure โดยในส่วนนี้จะเป็นการแสดงผลของ figure ที่สร้างขึ้นมา
![image](https://miro.medium.com/max/700/1*-AodXsh3AIymW83WLPwYqw.png)

### Quality attribute scenarios

#### Scenario 1: Modifiability
```
Source(ผู้พัฒนา) 
Stimulus(ต้องการเพิ่มคุณสมบัติใหม่) 
Environment(เวลาที่ใช้ในการพัฒนา) 
Response(ระบบที่สามารถเพิ่มคุณสมบัติใหม่ได้) 
Response Measure(เวลาที่ใช้ในการพัฒนา) 
```

#### Scenario 2: Usability
```
Source(ผู้ใช้งาน) 
Stimulus(ใช้งาน matplotlib ในการสร้างกราฟด้วย python) 
Environment(Deployment, Deployment, Runtime, Integration) 
Response(สำเร็จหรือไม่) 
Response Measure(มีการแสดงผล) 
```

#### Scenario 3: Performance
```
Source(ผู้ใช้งาน) 
Stimulus(คำสั่งสร้างกราฟจากผู้ใช้งาน) 
Environment(Deployment, Deployment, Runtime, Integration) 
Response(เวลาที่ใช้ในการสร้างกราฟ) 
Response Measure(Latency)
```

## Audacity

Audacity คือ **crossplatform multitrack audio editor and recorder**.

### architectural patterns/styles

รูปแบบสถาปัตยกรรมที่ Audacity ใช้คือรูปแบบ **Layer architectural** 

**Layer ส่วนที่ติดต่อกับผู้ใช้งาน (GUI)** ใช้ Lib wxWidgets (GUI components in a cross-platform way) โดยในส่วน GUI ถูกแบ่งออกมาหลายๆส่วน เช่น Blockfiles, ShuttleGUI โดยในส่วนนี้ทำหน้าที่รับคำสั่งและแสดงผลต่อผู้ใช่งาน

**Layer ส่วนที่ติดต่อกับ Hardware** ใช้ Lib PortAudio (provides a low-level audio interface in a cross-platform way) โดยในส่วนนี้ทำหน้าที่ติดต่อกับ OS เพื่อใช้งาน Interface ต่างๆของ Hardwawre

![image](https://www.aosabook.org/images/audacity/Layers.png)

### Quality attribute scenarios

#### Scenario 1: Usability
```
Source(ผู้ใช้งาน)
Stimulus(เรียนรู้การใช้งาน)
Response Measure(ความพึงพอใจ)
Response(ช่วยเหลือการใช้งาน)
Environment(Runtime)
```

#### Scenario 2: Integrability
```
Source(ผู้ใช้งาน)
Stimulus(ต้องการเพิ่ม Plugin ให้กับ Audacity)
Environment(Deployment, Deployment, Runtime, Integration)
Response(New Configuration)
Response Measure(มี Plugin ใหม่)
```

#### Scenario 3: Performance
```
Source(Hacker)
Stimulus(Library ที่ใช้งานไม่ปลอดภัย)
Environment(Plugin Online)
Response(Data, Resource)
Response Measure(Intrustion detection devices)
```

## Jitsi

Jitsi คือ open-source projects สำหรับการสร้าง video conference และ chat โดยใช้ WebRTC และ XMPP ซึ่งเป็นโปรเจคที่เปิดโอกาสให้ผู้ใช้งานสามารถเข้ามาเพิ่มเติม แก้ไข และปรับปรุงโปรเจคได้

### architectural patterns/styles

รูปแบบสถาปัตยกรรมที่ Jitsi ใช้คือรูปแบบ **Layer architectural**

**Jitsi Meet** WebRTC compatible JavaScript application that uses Jitsi Videobridge to provide high quality, scalable video conferences. Build upon React and React Native

**Jitsi Videobridge (jvb)** WebRTC compatible server designed to route video streams amongst participants in a conference

**Jitsi Conference Focus (jicofo)** server-side focus component used in Jitsi Meet conferences that manages media sessions between each of the participants and the videobridge

**Jitsi Gateway to SIP (jigasi)** server-side application that allows regular SIP clients to join Jitsi Meet conferences

**Jitsi Broadcasting Infrastructure (jibri)** tools for recording and/or streaming a Jitsi Meet conference that works by launching a Chrome instance rendered in a virtual framebuffer and capturing and encoding the output with ffmpeg

![image](https://raw.githubusercontent.com/jitsi/handbook/master/docs/assets/ArchitectureDiagram.png)

### Quality attribute scenarios

#### Scenario 1: Usability
```
Source(ผู้ใช้งาน) 
Stimulus(video conference ผ่าน Jitsi) 
Environment(Jitsi Meet, Jitsi Videobridge, Jitsi Conference Focus, Jitsi Gateway to SIP, Jitsi Broadcasting Infrastructure) 
Response(สำเร็จหรือไม่) 
Response Measure(สามารถเข้าร่วม video conference ได้) 
```

#### Scenario 2: Performance
```
Source(ผู้ใช้งาน)
Stimulus(คำสั่งสร้าง video conference จากผู้ใช้งาน)
Environment(Jitsi Meet, Jitsi Videobridge, Jitsi Conference Focus, Jitsi Gateway to SIP, Jitsi Broadcasting Infrastructure)
Response(เวลาที่ใช้ในการสร้าง video conference)
Response Measure(Latency)
```

#### Scenario 3: Security
```
Source(ผู้ใช้งาน)
Stimulus(เข้าร่วม video conference ที่ไม่ได้รับอนุญาติผ่าน Jitsi)
Environment(Jitsi Meet, Jitsi Videobridge, Jitsi Conference Focus, Jitsi Gateway to SIP, Jitsi Broadcasting Infrastructure)
Response(สำเร็จหรือไม่)
Response Measure(ไม่สามารถเข้าร่วม video conference ได้)
```
