image: images/desktop_errai_1024x800.jpg
class: fill nobackground

---

title: Oh noo...!
class: nobackground fill
content_class: flexbox vcenter

![noooo!.](images/oh-no-baby.jpg)

<footer class="source">source: pillaiconsulting</footer>
---

image: images/ibm_supercomputer.jpg
class: fill nobackground

---

image: images/weathercom_ui_fail.jpg
class: fill nobackground

---

image: images/reuse.jpg
class: fill nobackground

---

title: Today
class: nobackground fill
content_class: flexbox vcenter

![Many kinds of devices.](images/mobiles.jpg)

<footer class="source">source: flickr ambroseandrei</footer>

---

title: Support Mobile touch
class: nobackground fill
content_class: flexbox vcenter

![detect swipe](images/swipe.jpg)

<footer class="source">source: Josh Clark</footer>

---

title: Html5 Templates
class: big

<pre class="prettyprint" data-lang="html">
    &lt;div class="complaint">
        &lt;input id="name" type="text" placeholder="Full Name">
        &lt;input id="email" type="text" placeholder="you@example.com">
        &lt;textarea id="text" placeholder="How can we help?">&lt;/textarea>
        &lt;button id="saveButton">Save&lt;/button>
    &lt;/div>
</pre>
---
title: Html5 Templates
class: big

<pre class="prettyprint" data-lang="html">
    &lt;div class="complaint">
     &lt;input <b>id="name"</b> type="text" placeholder="Full Name">
     &lt;input id="email" type="text" placeholder="you@example.com">
     &lt;textarea id="text" placeholder="How can we help?">&lt;/textarea>
     &lt;button id="saveButton">Save&lt;/button>
    &lt;/div>
</pre>
... and just attach it
<pre class="prettyprint" data-lang="java">
    @Templated
    public class ComplaintForm extends Composite {
        @Inject @DataField
        <b>private TextBox name;</b>
    }
</pre>

---

title: Navigation and Bookmarking

<pre class="prettyprint" data-lang="java">
@Page @Templated
public class ComplainForm extends Composite {
    ...
}
</pre>

<pre class="prettyprint" data-lang="java">
@Page @Templated
public class WelcomePage extends Composite {
    @Inject
    private TransistionTo&lt;ComplainForm> complainForm;
    
    @EventHandler
    public void onComplaint(ClickEvent e) {
        complainForm.go();
    }
}
</pre>

---
title: Two way binding

<pre class="prettyprint" data-lang="java">
@Page
@Templated
public class ComplaintForm extends Composite {
  
  @Inject
  <b>@Model</b>
  private UserComplaint userComplaint;

  @Inject
  <b>@Bound</b>
  @DataField
  private TextBox name;
</pre>

---
title: Typesafe distributed events

<pre class="prettyprint" data-lang="java">
@Inject
private Event&lt;Document> updatedDocumentEvent;

...

updatedDocumentEvent.fire(document);
</pre>

---
title: Typesafe distributed events

<pre class="prettyprint" data-lang="java">
@Inject
private Event&lt;Document> updatedDocumentEvent;

...

updatedDocumentEvent.fire(document);
</pre>

<pre class="prettyprint" data-lang="java">
public void onUpdatedDocument(@Observes Document document) {
    ...
}
</pre>

---
title: Typesafe RPC and Rest

<pre class="prettyprint" data-lang="java">
@Inject
private Caller&lt;CustomerEndPoint> endPoint;

...

endPoint.call().create(model);
</pre>

---
title: JPA, offline mode data sync

<pre class="prettyprint" data-lang="java">
@Inject
private EntityManger entityManger;

@Inject
private ClientSyncManager syncManager;
</pre>

---
title: Go Mobile!
class: big

<pre class="prettyprint" data-lang="java">
@Inject
private Camera camera;

public void onBatteryLowEvent(@Observers BatteryLowEvent e) {
}
</pre>

---
title: Demo time
subtitle: let's code some stuff
class: segue dark nobackground
