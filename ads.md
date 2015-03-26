## Show alternate block if Ads are disabled
The following snippet(s) let you show an alternate DOM element if ads are disabled (e.g. by AdBlock Plus). These are specific to ads by Google, but you can modify the CSS selector to fix whatever you need.

Include the following `<style>` in the `<head>` of your page

```css
    <style type="text/css">
        /** show an alternate block if ads are disabled on client browser */
        ins.adsbygoogle:not(:empty) ~ .ad-slot-show-if-blocked{ display: none !important; }
        ins.adsbygoogle:empty ~ .ad-slot-show-if-blocked{ display: block !important; }    </style>
```
Then, in the body of your page, do something like the following

```html
	<div>
		<!-- start the google stuff -->
		<ins><!-- this would all by copy/pasted from your adsense account --></ins>
		<!-- end the google stuff -->
		<div class='ad-slot-show-if-hidden'>
			<p>Hi! You love us, so why not <button>Donate!<button></p>
		</div>
	</div>
```

#### How it works
AdBlock will automatically nuke the Google Adsense script and set `display: none` on the `<ins>` block. This will leave the `<ins>` tag `:empty` and the whole block hidden.

Our CSS then simply un-hides the `ad-slot-show-if-empty` block if the ad was blocked *(namely, `ins:empty`)* or hides itself if the ad wasn't blocked *(namely, `ins:not(:empty)`)*