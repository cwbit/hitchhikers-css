## Show alternate block if Ads are disabled
The following snippet(s) let you show an alternate DOM element if ads are disabled (e.g. by AdBlock Plus). These are specific to ads by Google, but you can modify the CSS selector to fix whatever you need.

Include the following `<style>` in the `<head>` of your page

```css
    <style type="text/css">
        /** show an alternate block if ads are disabled on client browser */
        .ad-slot { display:block !important;}
        .ad-slot ins.adsbygoogle:not(:empty) ~ .ad-slot-show-if-blocked{ display: none; }
        .ad-slot ins.adsbygoogle:empty ~ .ad-slot-show-if-blocked{ display: block; }
    </style>
```
Then, in the body of your page, do something like the following

```html
	<div class='ad-slot'>
		<!-- start the google stuff -->
		<ins><!-- this would all by copy/pasted from your adsense account --></ins>
		<!-- end the google stuff -->
		<div class='ad-slot-show-if-hidden'>
			<p>Hi! You love us, so why not <button>Donate!<button></p>
		</div>
	</div>
```

#### How it works
AdBlock will automatically nuke the Google Adsense script and set `display: none` on the `ad-slot` block. This will leave the `<ins>` tag `:empty` and the whole block hidden.

Our CSS then simply forces `ad-slot` to always show and just un-hides the `ad-slot-show-if-empty` block if the `ins:empty` is true (meaning the ad was blocked).