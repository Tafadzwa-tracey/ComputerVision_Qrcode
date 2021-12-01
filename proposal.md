Building  Qrcode Scanner
--------
<https://github.com/Tafadzwa-traceComputerVision_Qrcode>

_**`Tracey  BK2018050`**_ ,_**`Vanesa BK2018049`**_ ,_**`Ethel BK2018038`**_

![Qrcode](image.jpg)

----------------
Introduction
----

For our project we thought QR codes/ Barcodes are very cool and interesting because they store information in a different format. The fun part about them is we can’t really tell what they are storing until we scan them. It’s like playing a puzzle game. And one more thing that we like about them is they can be part of the physical world and still connect us to the internet world.

Building a QR Code Scanner 
---

In this project we are going to build a qr code scanner and in order to do  so a deeper  and robust understanding of qr codes is needed.The use of qr codes ,invented by [Denso wave](https://www.denso-wave.com/en/), has risen greatly ,for instance according to Forbes since the pandemic began qr codes have risen by [11%  in US](https://www.forbes.com/sites/forbesagencycouncil/2021/04/13a-touchless-world-qr-codes-and-their-growth-in-north-america) only.Them being used in [seamless payments to financial information delivery](https://www.pymnts.com/consumer-payments-2/2021/retail-adoption-qr-codes-security-touchless-payments/) ,hotels ,hospitals ,restaurants  and online-to-offline marketing , this clearly shows why they are most preferably used in [China](https://a16z.com/2017/08/11/qr-codes-in-china/) ,according to [CNN Tech](https://money.cnn.com/2017/09/08/technology/china-qr-codes/index.htm), USD 1.65 Trillion in transactions was done via QR Codes in [China in 2016](https://scanova.io/blog/qr-code-statistics/).AS QR readers are now native to smartphone cameras, users no longer need to download a separate app to scan a code this has contributed greatly to their use. This project is mainly focused on using OpenCV  and pyzbar to build a qr code scanner.

What is a qrcode
----
It is two-dimensional version of the Barcode which is able to convey a wide range of information  instantly with the scan of a mobile device .It stores up to 7089 digits or 4296 characters.When designing the Static QR Codes more data is added and the bigger the size the more complex the structure becomes .It can take up to [30%  damages  of the Code]( https://www.qr-code-generator.com/qr-code-marketing/qr-codes-basics/) structure without affecting its  readability.According  to [Hara and his team](https://en.wikipedia.org/wiki/Denso), the white to black areas’ ratio are reduced to patterns on printed material  ratio [1:1:3:1:1](https://www.qr-code-generator.com/qr-code-marketing/qr-codes-basics/).QR codes often contain data for a locator, identifier, or tracker that points to a website or application .A QR code use four standardized encoding modes (numeric,alphanumeric,byte/binary, and kanji) to store data efficiently; extensions may also be used .They consist of

    -Position detectors - identify presence and orientation
    Located at three corners of each code allowing a scanner to accurately recognize and read code at high speed  indicating the printed direction of the Code.

    -Alignment markers
    Smaller than the position detection markers, help straighten out QR Codes curved surfaces.  The more the information on Code , the larger it becomes and the more alignment patterns it  need it.

    -Timing pattern
    Alternating black/white modules helping to configure data grid ,using these lines, the 	scanner determines how large the data matrix is.

    -Version Information
    Currently 40 different QR Code versions available, these markers specify the one used.

    -Data and error correction keys
    Mechanism inherent in the QR Code structure , all your data is contained here and shares the space with the error correction blocks that allow up to 30% of the Code to be damaged

    -Quiet zone
    Similar to the importance of white space in design, offering structure and improving comprehension.The quiet zone is vital  in order to distinguish the QR Code from its surroundings.
As shown below:
![Description](description.png)

How qrcode  work
----

Qr codes consist of 7 parts ,each part having a pixel pattern which looks similar to  a crossword puzzle
Each element conveys certain information through the Code  like print direction, timing, error tolerance and empty spaces differentiating the Code its surroundings .It is processed using [Reed–Solomon](https://en.wikipedia.org/wiki/Reed%E2%80%93Solomon_error_correction)  error correction until the image can be appropriately interpreted.Steps of [encoding](https://www.thonky.com/qr-code-tutorial/introduction):

1.[Data analysis](https://www.thonky.com/qr-code-tutorial/data-analysis)
2.Data Encoding
3.Error correction Coding
4.Structure Final Message
5.Module Placement Matrix
6.Data Masking
7.Format and version Formation

How qrcode scanner work
----


QR scanners read both the data codewords and the error correction codewords. By comparing the two, the scanner can determine if it read the data correctly, and correct errors if it did not read the data correctly. Detecting a QR code revolves around identifying finder patterns. The key idea is that there's a ratio in the number of black/white/black/white/black. And this ratio remains the same no matter what angle you look at it.

Libraries
---------

We used a regular code editor and installed three libraries: Pillow, OpenCV and Pyzbar. Pillow library is also known as PIL, which stands for Python Image Library. [OpenCV](https://docs.opencv.org/3.4/) is a well-known library, especially when working with computer vision projects,[Webbrowser](https://docs.python.org/3/library/webbrowser.html) which  provides a high-level interface  allowing displaying web-based documents to users. And lastly [Pyzbar](https://pypi.org/project/pyzbar),[Pillow](https://pypi.org/project/Pillow/)    , a python library that will help us read the barcode and QR codes.

____
Code
----
    #pip install opencv
    #pip  install webbrowser 
Install libraries

```
import cv2
import webbrowser
```
Import libraries to be used 

```
cap = cv2.VideoCapture(0)
# initialize the cv2 QRCode detector
detector = cv2.QRCodeDetector()
while True:
    _, img = cap.read()
    # detect and decode
    data, bbox, _ = detector.detectAndDecode(img)
# check if there is a QRCode in the image
    if data:
        a = data
        break
    cv2.imshow("QRCODEscanner", img)
    if cv2.waitKey(1) == ord("q"):
        break

b = webbrowser.open(str(a))
cap.release()
cv2.destroyAllWindows()
```

First, we are turning on the camera of the computer using OpenCV. If you have an external camera, you have to change the value 0 to 1 depending on the device.Secondly, we run a while loop to keep running the decoding function until the “Esc” key is pressed. Otherwise, the loop will not stop and cause some issues.Thirdly, we are releasing the camera that we turned on in the first step. And then we are closing the application window. OpenCV is doing all the work, we just need to call the methods.Lastly , we are calling the main function to trigger the program.


**NB: To be improved**
Results
-----

The program can scan QR codes of all types for example the one shown below
![Result_one](Results/one.png)

Scanning the QR Code
![Result_two](Results/two.png)

After scanning the code it redirects to the website as shown below
![Result_three](Results/three.png)

___
Shortcomings of qr codes 
----
✧Smartphones used to scan QR codes are often   expensive and costly in comparison with simpler phones.

✧Many users that have mobile phones, do not have smartphones, that have cameras that are unable to get QR reading software for their phone

✧ Not very aesthetic, it contains random patterns of square boxes which might not look pleasing on products, unlike 1-d barcodes.

✧To make changes to QR codes, one needs to create an entirely different code.

✧[They are ugly](https://www.digitaloperative.com/blog/2017/the-death-of-qr-codes-and-the-rise-of-new-technology)


Solution for the shortcomings
----
1.NFC tags
  [Near Field Communication](https://www.digitaloperative.com/blog/2017/the-death-of-qr-codes-and-the-rise-of-new-technology) which does not require an extra application comes already built in smartphones . If a smartphone has NFC enabled, all someone has to do is touch or tap their smartphone against the NFC tag for the desired action to take place but this does not solve the issue of needing to have a smartphone , iphone users.Unlike Qr codes  they can be edited easily ,all is needed is to overwrite the old information

2.SnapTag
[SnapTags ](https://resources.chromotek.com/blog/snap-tag-and-clip-tag-overview) ,  which are prettier than Qr codes.Similar to QR codes that is  they are scannable images that access additional information marketers want consumers to know about since consumers are attracted to colors and interesting designs and qr code black and white square often looks out of place and tends to clash with the design.They also don’t require an extra application.SnapTagscan seamlessly integrate e within the design of the overall product and scanned.

Conclusion
----

QR code stores more information than BARcodes. QR Code stores the information matrix form which stores the information on both axes horizontally or vertically. QR code has many advantages like as they are free to generate and easy to scan.Although QR codes are very flexible and have been around for over eighteen years, their use in many fields like medical ,business, education, security are still in their infancy.It is of great significance to improve the recognition rate of the QR code in special circumstances, especially on papers, and the improvement of the recognition rate can also greatly promote the application of QR codes.

Qrcodes may seem to be ugly or do not align well with many business logos ,but their ugliness can also be used as an advantage because world wide some people don’t know them and their structure on its own draws curiosity.Indeed , for a person to use a qrcode ,they must own a smartphone which is a little bit expensive given the average salary a person can get example in [Rwanda, average annual salary: $744 (£576)](https://www.lovemoney.com/gallerylist/79056/what-the-average-person-earns-in-different-countries-around-the-world) but as we can see the world is becoming technologically advanced  and its only a matter of time before almost everyone can afford a smartphone .As we can see developers of smartphones  are also trying to integrate qrcodes with smartphones for easy usability.Nowarday a person doesn’t need to download an application to scan a qrcode ,as long as your smartphone has a camera it can be scanned for the later versions of smartphones.
