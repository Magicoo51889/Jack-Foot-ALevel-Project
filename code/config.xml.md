# config.xml

```xml
<?xml version='1.0' encoding='utf-8'?>
<widget id="io.cordova.hellocordova" version="1.0.0" xmlns="http://www.w3.org/ns/widgets" xmlns:cdv="http://cordova.apache.org/ns/1.0">
    <name>PhaserALevelGame</name>
    <description>
    </description>
    <author href="">
        Jack Foot
    </author>
    <content src="index.html" />
    <access origin="*" />
    <allow-intent href="http://*/*" />
    <allow-intent href="https://*/*" />
    <allow-intent href="tel:*" />
    <allow-intent href="sms:*" />
    <allow-intent href="mailto:*" />
    <allow-intent href="geo:*" />
    <platform name="android">
        <allow-intent href="market:*" />
    </platform>
    <platform name="ios">
        <allow-intent href="itms:*" />
        <allow-intent href="itms-apps:*" />
    </platform>
    <preference name="Fullscreen" value="true" />
    <preference name="orientation" value="landscape" />
    <plugin name="cordova-plugin-whitelist" spec="^1.3.3" />
    <engine name="android" spec="^7.0.0" />
    <engine name="browser" spec="^5.0.2" />
    <engine name="ios" spec="^4.5.4" />
</widget>
```
