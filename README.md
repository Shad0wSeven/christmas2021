# christmas2021
how i electronically sent out christmas cards for 2021


## how it worked (end user)

first the end user was greeted with a screen asking to enter a passcode, followed by a [GO] button.

![Screen Shot 2021-12-25 at 11 54 01 PM](https://user-images.githubusercontent.com/19739712/147402259-8a8dc5fc-db23-4a44-a3f9-b73c3d4232f4.png)

if they entered the wrong code they would get an invalid code message

![Screen Shot 2021-12-25 at 11 54 57 PM](https://user-images.githubusercontent.com/19739712/147402279-5e2c3bdd-a625-4e05-abee-0aba475d122e.png)

otherwise it would unlock to their actual card

![Screen Shot 2021-12-25 at 11 55 14 PM](https://user-images.githubusercontent.com/19739712/147402283-2bd97ea0-82e2-43fb-b948-e10a5a09e4ff.png)

for those that try to guess, some codes send to a rickroll youtube page.

## how it worked (developer)

so basically, the input form is very basic

```html
passcode <input type="text" id="myText" placeholder="input here">
<button onclick="myFunction()" id="dottedb">Go</button>
```

it calls a function which attempts to route to relative path of the "password"

```javascript
function myFunction() {
  var x = document.getElementById("myText").value;
  if(x.length != 0 ){
  document.getElementById("demo").innerHTML = '🎄unlocking...🎄';
    setTimeout(function(){
        window.location.href = "/" + x + ".html";
        }, 500);

  }
}
```
vercel checks for an HTML file, otherwise redirects to the 404 page.
if an html file exists with that name, it just routes too it, otherwise it routes to the 404 page... 

```html
<script>
	  window.location.href = "index.html?error=1";
</script>
```
which redirects to the index and adds invalid.

```javascript
var url = window.location.href // for current url
var captured = /error=([^&]+)/.exec(url)[1]; // Value is in [1] ('384' in our case)
var result = captured ? captured : '';
if (result == '1') {
    document.getElementById("demo").innerHTML = "Invalid Code";
}
```

so basically add more cards with the specified code by just naming the HTML file whatever you want the password to be, and editing it. 
yeah its very basic, but it's kind of what i thought of at 5pm on the 24th so give me a break!

also the rickroll pages are just HTML pages with this:
```html
<script>
	window.location.href = "https://www.youtube.com/watch?v=dQw4w9WgXcQ";
</script>
```
