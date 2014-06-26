
class: nobackground
content_class: nobackground

<img src="images/phonegap-architecture.jpg" alt="architecture" class="stretched">

---

class: nobackground fill
content_class: flexbox vcenter

![plugins](images/phonegap-plugins.jpg)

---

title: Uncanny Valley
class: nobackground fill
content_class: flexbox vcenter

![scary](images/uncanny-valley.jpg)

<footer class="source">source: csmonitor</footer>

---

title: Showcase apps
class: nobackground fill
content_class: flexbox vcenter

<img src="images/untappd1.jpg" alt="untappd" width="52%"/>
![bbc sport](images/bbc-sport.jpg)

<footer class="source">source: phonegap</footer>

---

title: Frameworks
class: nobackground fill
content_class: flexbox vcenter

<style>
  #logos {
    border-spacing: 0;
    box-shadow: 0 10px 14px -5px black;
  }
  #logos tr{
    background-color:#999;
  }
  #logos td{
    text-align: center;
  }
</style>

<table id="logos">
  <tr>
    <td>
      <img src=images/logos/AngularJS-large.png>
    <td>
      <img src=images/logos/backbone.png>
    <td>
      <img src=images/logos/jquery.png>
  <tr>
    <td>
      <img src=images/logos/ionic-logo-white.svg width=155px>
    <td>
      <img src=images/logos/requirejs.png>
    <td>
      <img src=images/logos/sencha.png>
  <tr>
    <td>
      <img src=images/logos/topcoat.png>
    <td>
      <img src=images/logos/twitter_bootstrap.jpeg>
    <td>
</table>

---
class: big

<div class="phone-case">
  <div>
    <iframe id="cp_embed_JsHjf" src="//codepen.io/anon/embed/JsHjf?height=568&amp;theme-id=3572&amp;slug-hash=JsHjf&amp;default-tab=result" scrolling="no" frameborder="0" height="568" allowtransparency="true" class="cp_embed_iframe" style="width: 100%; overflow: hidden;"></iframe>
  </div>
  <script async="" src="//codepen.io/assets/embed/ei.js"></script>
</div>

---

title: Starting a mobile project

<pre class="prettyprint" data-lang="command">
#several yeoman generators
yo ionic
yo angular-cordova
yo cordova

#grunt
grunt cordova:build
grunt platform:add:android
grunt ripple

</pre>
---
title: Demo time
subtitle: let's code some stuff
class: segue dark nobackground
---

title: AeroGear
class: nobackground fill
content_class: flexbox vcenter

![AeroGear](images/logos/aerogear-lib.png)

---

title: Complex
class: nobackground fill
content_class: flexbox vcenter

<img src="images/complex_push.png" width="85%"></img>

---

title: AeroGear UnifiedPush
class: nobackground fill
content_class: flexbox vcenter

![UnifiedPush](images/aerogear_unified_push_server.png)

---

title: Demo time
subtitle: let's code some stuff
class: segue dark nobackground

---
title: Pipes

<pre class="prettyprint" data-lang="javascript">
var memberPipe  = AeroGear.Pipeline([{
  name: "members",
  settings: {
      baseURL: "http://todo-aerogear.rhcloud.com/rest/"
  }
}]).pipes.members;
</pre>
<pre class="prettyprint" data-lang="javascript">
memberPipe.read({
  success: function( data ) {
    ...
    $( "#members" ).html( buildMemberRows() );
  },
  error: function (error) {
    console.log(error);
  }
});
</pre>

---
title: Pipes on Android

<pre class="prettyprint" data-lang="java">
Pipeline pipeline = new Pipeline("http://todo-aerogear.rhcloud.com/rest/");
pipeline.pipe(Member.class);
LoaderPipe&lt;Member> pipe = pipeline.get("member", this);
</pre>
<pre class="prettyprint" data-lang="java">

pipe.read(new AbstractActivityCallback&lt;List&lt;Member>>(){
    void onSuccess(List&lt;Member> data) {
        ...
    }
    void onFailure(Exception e){
        //Gracefully handle the exception
    }    
});
</pre>
---

title: Pipes on iOS

<pre class="prettyprint" data-lang="ios">
// Create the 'Pipe'
NSURL* serverURL = [NSURL URLWithString:@"http://todo-aerogear.rhcloud.com/rest/"];
AGPipeline* memberPipe = [AGPipeline pipelineWithBaseURL:serverURL];
id&lt;AGPipe> projects = [todo pipe:^(id&lt;AGPipeConfig> config) {
  [config setName:@"members"];
}];
</pre>
<pre class="prettyprint" data-lang="ios">
// Read
[memberPipe read:^(id response) {
  ...
  [self.tableView reloadData];
} failure: ^(NSError *error) {
  NSLog(@"Error: \n%@", error);
}];
</pre>

---

title: DataManager

<pre class="prettyprint" data-lang="javascript">
var dm = AeroGear.DataManager( "tasks" ).stores[ 0 ];

dm.save({
    id: 12345,
    title: "Created Task"
});

var allData = dm.read();
var justOne = dm.read( 12345 );

var filteredData = dm.filter({
    date: "2012-08-01",
    user: "admin"
});
</pre>

---

title: Crypto

<pre class="prettyprint" data-lang="javascript">
var rawPassword =
AeroGear.Crypto().deriveKey( PASSWORD ),
utf8String = sjcl.codec.utf8String,
hex = sjcl.codec.hex,
cipherText,
options = {
    IV: hex.toBits( BOB_IV ),
    AAD: hex.toBits( BOB_AAD ),
    key: rawPassword,
    data: utf8String.toBits( PLAIN_TEXT )
};

cipherText = AeroGear.Crypto().encrypt( options );
options.data = cipherText;
plainText = AeroGear.Crypto().decrypt ( options );
equal( utf8String.fromBits( plainText ),    PLAIN_TEXT, "Encryption has failed" );
</pre>

---

title: AeroGear Cordova Geo
class: nobackground fill
content_class: flexbox vcenter

![Geo](images/SearchRadius.png)

---

title: AeroGear Cordova Crypto
class: nobackground fill
content_class: flexbox vcenter

![Crypto](images/lock.jpg)
