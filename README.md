# rightmove
A collection of house searching scripts and tools

## Rightmove API
Rightmove has an API, hosted at http://api.rightmove.co.uk . This is used by the mobile apps to get data when searches take place. I believe it is also used to save searches, but my memory is a bit hazy on how that is done as it has been a while.

By running a hotpot on a desktop computer (or other computer with another connection to the internet that is not the WiFi module you are using to make the hotspot), you can sniff the traffic with a tool such as Wireshark. This gets lots of lovely calls to api.rightmove.co.uk, and shows how simple it is.

### Example:
```
curl -X GET "http://api.rightmove.co.uk/api/sale/find?auction=false&appVersion=2.11.5&numberOfPropertiesRequested=1000&apiApplication=ANDROID&index=0&includeSSTC=true&sortType=1&locationIdentifier=LAT_LONG_BOX%5E-1.39871%2C-1.23477%2C51.00765%2C51.12"
```
This simple example gets up to 1000 properties in the bounding box given by the `LAT_LONG_BOX` parameter. In this case, all of Winchester and the surrounding area (which on 20170724 gave 880 results. 

The query as grabbed from the network traffic only got 25 results at once, and I've found that 1000 is as high as you can go. there is an `index=` parameter that appears to be the way to paginate the data to get more.

I think most of the parameters are self explanitory, and I include it here for reference and interest only
