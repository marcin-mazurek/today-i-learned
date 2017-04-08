# Chrome DevTools

## Finding potentially slow scripts
There are two types of web peformance issues - network and script related.
If you check the Devtools timeline, in the Network section you'll notice "moustache" around loaded scripts:

![screen shot 2017-04-08 at 10 16 13](https://cloud.githubusercontent.com/assets/6684554/24827093/7eebd77e-1c44-11e7-917c-ef044ee3c7e9.png)
This tells us that the network is fine, the server responded quickly. The performance problem lives in the scripts itself.

However, if you see long strap and short "moustache", this is likely a network issue 
(**likely** - I'm not saying it is an issue - there are some network limitations you won't overcome):

![screen shot 2017-04-08 at 10 20 02](https://cloud.githubusercontent.com/assets/6684554/24827111/08a125c8-1c45-11e7-8c5f-cb7aca581562.png)
