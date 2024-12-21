[toc]

UITextInput protocol<br>UIInteraction<br>UITextInteraction<br>UITextSelectionDisplayInteraction<br>UITextLoupeSession<br>NSTextAttachment<br>NSLinkAttributeName<br>Text Programming Guide ([link](https://developer.apple.com/library/archive/documentation/StringsTextFonts/Conceptual/TextAndWebiPhoneOS/LowerLevelText-HandlingTechnologies/LowerLevelText-HandlingTechnologies.html#//apple_ref/doc/uid/TP40009542-CH15-SW23))<br>What is tokenizer in UITextInput ([SO link](https://stackoverflow.com/questions/16335518/tokenizer-of-uitextinput-what-is-it-used-for))

TextKit 2<br>Text Styles

>If you're using a custom text view in your app, make sure to use the system selection UI to take advantage of all the new features in the OS. Use text items to create better interactions with links in your text views. Leverage the powerful new features of TextKit 2 to provide a more rich text editing experience. And adopt Text Styles in common text elements to ensure a great user experience for everyone, regardless of what language or preferred text size.

Tinkering with QuickType bar - <br>https://stackoverflow.com/questions/31167416/customizing-quicktype-suggestions-in-ios <br>https://stackoverflow.com/questions/28889368/possible-to-programmatically-feed-the-ios-predictive-keyboard-context-source-tex

Observing keyboard display in UIViewController <br>Observing keyboard display in WKWebView <br>

##### UITextInput - marked text

Any UITextInput conforming entity needs to have a selectedTextRange and markedTextRange. The latter is something that is probably needed for ideographic languages (i.e. pictorial languages like Japanese) in which text is only entered in two stages, first something is typed and then it has to be confirmed. 

[Reference](https://developer.apple.com/documentation/uikit/uitextinput?language=objc#Working-with-marked-and-selected-text), [SO post](https://stackoverflow.com/a/24642416/1135417)

> Briefly touched upon in 'WWDC 17 - The Keys to a Better Text Input Experience' at 27:00 mark.

##### WWDC videos

WWDC 23 - What’s new with text and text interactions <br>WWDC 21 - Use the camera for keyboard input in your app - k<br>WWDC 23 - Keep up with the keyboard - k <br>WWDC 21 - Your guide to keyboard layout - k <br>

WWDC 17 - The Keys to a Better Text Input Experience (👈 Excellent video, discusses inputView etc. Have downloaded, [unofficial link](https://nonstrict.eu/wwdcindex/wwdc2017/242/)) - k<br>WWDC 21 - Support full keyboard access in your iOS app - k <br>

##### Undocked and Split keyboard

On iPad keyboard can be undocked (i.e. floating) as well as split. Note that not all iPads support both. FWIW, some of the newer iPads don't support split keyboard (as of 2024). ([Reference](https://support.apple.com/guide/ipad/move-the-onscreen-keyboard-ipad02663f08/ipados))

-----

Out of process keyboard



