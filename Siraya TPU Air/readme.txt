Flex TPU Air 65A-82A Filament
https://siraya.tech/products/flex-tpu-air-65a-82a-foaming-flexible-filament

Multi step process used to generate settings in this folder. It wasnt as simple as "save the project filament as a user setting" (see bottom ramble):
1) Download Air 3mf files from Siraya website (https://siraya.tech/pages/print-settings-download leads to a drive link: https://drive.google.com/file/d/1vxeuemK6ZQ2sgDM0BFez1ivRn01X6Du2/view?usp=drive_link used with thanks! But PLEASE if Siraya are reading this: create these as config files or something so i can avoid below... Links given are for P1S but they have for all Bambu printers and other brands. So you can use steps below to create your own user settings from these 3mf)
2) Save project filament settings as user filament settings (for explanation sake, 'project.json')
3) Create a new temporary filament based on 'generic tpu': copy the created filament setting from your filaments/base folder (generic.json)
4) In filament settings 'edit' a generic TPU setting (e.g. the one you just created, or the standard generic direct, whatevevs) and this will form the basis of the new settings ('siraya.json')
5) You'll notice if you manually look at siraya.json it basically has nothing apart from 'inherits generic tpu'... So we're going to add a bunch of stuff in the UI, and then add a bunch of remaining stuff from the project.json...
6) Compare generic.json with project.json i.e. an online key/value compare: that will show you what is different from generic: go through editing siraya.json in the UI in the normal way, changing whatever settings you can find: it's a bit hard 
    sometimes to find them from the JSON names, and A LOT of settings aren't actually in the UI at all... see next step...
7) The remaining key value pairs: recommend saving backup of siraya.json at this point incase you break something: if your json is malformed, studio will overwrite it with the last known 'good' profile (which might be the original bare minimum!)
8) Close bambu studio, then Copy paste the remaining key value pairs directly in to siraya.json using text editor
9) Load Bambu Studio: if your user setting still exists, and still has all the text you entered, then it worked!
10) Create a new custom filament using siraya.json...
11) Leave me a comment for an easier way to do this lol 

My theory is there's something about project.json which is malformed... it will save, but you can't use it in custom filament... The obvious reason is that the 'inherits' value is set to 'Siraya 95A'... so maybe a fix is to actually install 
that setting? I tried that and didn't have much luck (long story). 

So you can change inherits to 'Generic TPU'... But still you can't select the user setting when creating a TPU custom filament: it will only show 'Generic TPU'... Super frustrating and why i think there's a key/value pair that is broken. There were a few settings with value 'null' where generic tpu = 0? I didnt copy them over... so maybe that's why it worked. Maybe Studio hates certain null entries. Generic TPU does have some null entries also though, so its not "all null are bad". Anyway, i'm not 100% confident in my eventual solution... i'm 100% sure it's not the most elegant way to achieve the goal.

What might be nice is if there was a fialment setting validator that could pickup the issue with project.json... Maybe ill try work it out through trial and error but there are a fair few key/value pairs to try

Or i might be able to create bambu importable config files from these json files? I'll give it a go
