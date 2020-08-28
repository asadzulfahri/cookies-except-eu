# Legal Monster Consent non-EU bypass

## Purpose
1. Enable Legal Monster consent widget for users in the Europe
1. Avoid using expensive and tedious GeoIP detection systems
1. Disable Legal Monster widget for non-Europe locations; and enabling all tracking scripts

## How does it work?
- This script replaces the default embed code by Legal Monster
- Using the JavaScript object `Intl.DateTimeFormat` we can detect the users system `timeZone`
- It checks the users actual system time clock
- This means even if users has a VPN, it will still detect the users time zone correctly

## Requirements
1. LegalMonster.com widget key
1. Make sure all your tracking scripts are properly implemented as per documented by Legal Monster: [Collecting cookie consent](https://docs.legalmonster.com/legaljs/collecting-cookie-consent)


## How do I use it on my website?
1. Make sure you have an account and a widget key with [Legal Monster](https://www.legalmonster.com/)
1. Copy & paste the following code to the top of your on the very top within the `<head>` element of your site
```
<!-- Legal Monster Consent non-EU bypass by AsadZulfahri.com -->
<script>
  userTZ = Intl.DateTimeFormat().resolvedOptions().timeZone;
   checkTZ = userTZ.indexOf('Europe');
   if (checkTZ !== -1) {
console.log("User is in Europe. Activating Legal Monster!");
document.write('\x3Cscript>!function(){var i,e,t,s=window.legal=window.legal||[];if(s.SNIPPET_VERSION=\'3.0.0\',i=\'https:\/\/widgets.legalmonster.com\/v1\/legal.js\',!s.__VERSION__)if(s.invoked)window.console&&console.info&&console.info(\'legal.js: The initialisation snippet is included more than once on this page, and does not need to be.\');else{for(s.invoked=!0,s.methods=[\'cookieConsent\',\'document\',\'ensureConsent\',\'handleWidget\',\'signup\',\'user\'],s.factory=function(t){return function(){var e=Array.prototype.slice.call(arguments);return e.unshift(t),s.push(e),s}},e=0;e<s.methods.length;e++)t=s.methods[e],s[t]=s.factory(t);s.load=function(e,t){var n,o=document.createElement(\'script\');o.setAttribute(\'data-legalmonster\',\'sven\'),o.type=\'text\/javascript\',o.async=!0,o.src=i,(n=document.getElementsByTagName(\'script\')[0]).parentNode.insertBefore(o,n),s.__project=e,s.__loadOptions=t||{}},s.widget=function(e){s.__project||s.load(e.widgetPublicKey),s.handleWidget(e)}}}(); legal.widget({ type: \'cookie\', widgetPublicKey: \'YOUR-WIDGET-KEY-HERE\', });\x3C/script>');
console.log("Legal Monster activated!");
  }
  else {
    console.log("User not in Europe. Tracking enabled!");
}
</script>
<!-- END Legal Monster Consent non-EU bypass AsadZulfahri.com-->
```
3. Replace `YOUR-WIDGET-KEY-HERE` with the your own key

## Where can I find my Legal Monster widget key?
1. Login to [Legal Monster](https://www.legalmonster.com/)
1. Navigate to the `Widgets` page
1. Select your widget cookie name
1. On the `Embed your widget` textarea, scroll down to the bottom
1. Your should see your widget key on the `widgetPublicKey` line

