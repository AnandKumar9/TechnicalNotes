[toc]

##### Elements - Styles, Computed tabs

Understand the other things in Developer Tools better, i.e. how styles, computed properties, etc. work.<br>

![image-20230619172935255](assets/image-20230619172935255.png)

##### Console

The logs, etc. can be seen in the console.

![image-20230619173331341](assets/image-20230619173331341.png)

-----

##### Inspecting Elements (Chrome's dev tools)

Inspecting elements, this shows the HTML corresponding to every element. They can even be modified on the fly. This is what probably other browsers called DOM inspector too.

![](assets/Misc-46c04ab5.png)

##### Viewing storages in Safari

In Safari -

There is a separate tab called Storage.

![image-20230706181519928](assets/image-20230706181519928.png)

In Chrome - 

In a tab named 'Application'.

![image-20230806122234141](assets/image-20230806122234141.png)

##### Network

In Chrome -

###### Negated filters

Can have negated filters in the textfield, i.e. not show records that have some text in the URL.

```
-js -woff2 -keymaster -formData -svg -jpg -retrievemessage -track -e.gif -png -tp2 -eval -bam.cell
```

###### Waterfall field (Start time of requests)

The waterfall field is what seems to indicate the request time. So to see the requests in chronological fashion, that is the field using which the view should be sorted.

###### Throttling requests

![image-20230806114246464](assets/image-20230806114246464.png)

###### Some records disappear

Surprisngly, some records disappear. For example, when I try to login to capitalone.com, the record for POST API call is barely shown for a fraction of second and then disappears. I could get it to show only by getting the tab to be offline so that the request fails and I can then see what the request was.

![image-20230806114149123](assets/image-20230806114149123.png)
