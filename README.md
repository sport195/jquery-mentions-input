Forked and updated from: <a href="https://github.com/podio/jquery-mentions-input">https://github.com/podio/jquery-mentions-input</a>.

Forked again from <a href="https://github.com/brennanmceachran/jquery-mentions-input">https://github.com/brennanmceachran/jquery-mentions-input</a>.

<h2>Getting started</h2>

<ol>
  <li>
    Add a script reference to jquery.mentionsInput.js:<br/>
    <pre>&lt;script src=&#39;jquery.mentionsInput.js&#39; type=&#39;text/javascript&#39;&gt;&lt;/script&gt;</pre>
  </li>
  <li>
    Add a bit of markup: <br/>
    <pre>&lt;textarea class=&#39;mention&#39;&gt;</pre>
  </li>
  <li>
    <p>Initialise the mentionsInput: <br/>
    <pre>
$('textarea.mention').mentionsInput({
  onDataRequest:function (mode, query, callback) {
    var data = [
      { id:1, name:'Kenneth Auchenberg', 'avatar':'http://cdn0.4dots.com/i/customavatars/avatar7112_1.gif', 'type':'contact' },
      { id:2, name:'Jon Froda', 'avatar':'http://cdn0.4dots.com/i/customavatars/avatar7112_1.gif', 'type':'contact' },
      { id:3, name:'Anders Pollas', 'avatar':'http://cdn0.4dots.com/i/customavatars/avatar7112_1.gif', 'type':'contact' },
      { id:4, name:'Kasper Hulthin', 'avatar':'http://cdn0.4dots.com/i/customavatars/avatar7112_1.gif', 'type':'contact' },
      { id:5, name:'Andreas Haugstrup', 'avatar':'http://cdn0.4dots.com/i/customavatars/avatar7112_1.gif', 'type':'contact' },
      { id:6, name:'Pete Lacey', 'avatar':'http://cdn0.4dots.com/i/customavatars/avatar7112_1.gif', 'type':'contact' }
    ];

    data = _.filter(data, function(item) { return item.name.toLowerCase().indexOf(query.toLowerCase()) > -1 });

    callback.call(this, data);
  }
});
    </pre>
    </p>

    <p>
      Bam, you are in business.
    </p>
  </li>
</ol>

<h2>Configuration</h2>
<p>jquery.mentionsInput does have a number of extra configuration options which you may change to customise the way it behaves.</p>

<p>The meaning of the options and their default values are listed below. </p>

<table>
  <tr>
    <td><b>onDataRequest</b></td>
    <td><tt>function(mode, query, triggerChar, callback)</tt></td>
    <td class="definition">
      <p>This function is a callback function which is used to provide data for the autocomplete. When a search starts
      this function is called with following arguments:</p>
      <p>'mode' &mdash; always set to 'search'</p>
      <p>'query' &mdash; what's been typed so far by the user</p>
      <p>'triggerChar' &mdash; which is the character that started this data request, so you can take different actions on a '@' or '#'.</p>
      <p>'callback' &mdash; function which needs to be called inside onDataRequest with a data collection to be searched on as a first argument.</p>
      
    </td>
  </tr>
  <tr>
    <td><b>triggerChar</b></td>
    <td><tt>@</tt></td>
    <td class="definition">
      <p>Trigger character which triggers the mentions search, when the character has been typed into the
      mentions input field.</p>
      <p>You can specify more than one trigger char by providing an array.<br>
      eg triggerChar : ['@', '#'] <br>
      <small> Thanks to <a href="https://github.com/podio/jquery-mentions-input/pull/7">@ryanramage</a></small>
      </p>
    </td>
  </tr>
  <tr>
    <td><b>onCaret</b></td>
    <td><tt>true</tt></td>
    <td class="definition">
      When set to true the autocomplete will be positioned beside the Caret (like how Github does it)<br>
     <small> Thanks to <a href="https://github.com/podio/jquery-mentions-input/pull/53">@juliocesar</a></small>
    </td>
  </tr>
  <tr>
    <td><b>minChars</b></td>
    <td><tt>2</tt></td>
    <td class="definition">
      The minimum amount of characters after the trigger character necessary to perform a search.
    </td>
  </tr>
  <tr>
    <td><b>showAvatars</b></td>
    <td><tt>true&nbsp;|&nbsp;false</tt></td>
    <td class="definition">
      Toggles whether or not items within the autocomplete-dropdown will be rendered with an icon/avatar.
    </td>
  </tr>
  <tr>
    <td><b>classes</b></td>
    <td><tt>object</tt></td>
    <td class="definition">
      Object which contains classes used in the layout as key/value pairs.
    </td>
  </tr>
  <tr>
    <td><b>templates</b></td>
    <td><tt>object</tt></td>
    <td class="definition">
      Object which contains templates used to render the layout as key/value pairs.
    </td>
  </tr>
  <tr>
    <td><b>enableHighlight</b></td>
	<td><tt>boolean</tt></td>
	<td class="definition">
	  Enables/disables the mention highlighting mechanism
	</td>
  </tr>
</table>

<h2>Methods</h2>

<p>jquery.mentionsInput does expose a number of public methods, you can call on an instance. </p>

<table>
  <tr>
    <td><b>init</b></td>
    <td></td>
    <td class="definition">
      Initialises the mentionsInput component on a specific element.
    </td>
  </tr>
  <tr>
    <td><b>reset</b></td>
    <td></td>
    <td class="definition">
      Resets the component, clears all mentions.
    </td>
  </tr>
  <tr>
    <td><b>val()</b></td>
    <td></td>
    <td class="definition">
      A method which returns a value of the input field (including markup) as a first parameter of this function. <br/><br/> This is the value you want to send to your server.
    </td>
  </tr>
  <tr>
    <td><b>getMentions()</b></td>
    <td></td>
    <td class="definition">
      A method which returns a collection of mentions as hash objects as a first parameter.
    </td>
  </tr>
</table>

<h2>Events</h2>

<p>Two events may be triggered on the initialized element <small> Thanks to <a href="https://github.com/podio/jquery-mentions-input/pull/43">@johnfrederik</a></small></p>
<table>
  <tr>
    <td><b>mention</b></td>
    <td></td>
    <td class="definition">
      Triggered when a new mention was added.
    </td>
  </tr>
  <tr>
    <td><b>updated</b></td>
    <td></td>
    <td class="definition">
      Triggered when the input was updated.
    </td>
  </tr>
</table>

<h2>Query data structure</h2>

<p>When the component is preforming a "query" on the data specified through the onDataRequest-callback, it's expecting a specific data structure to be returned. </p>
<pre>
{
  'id'    : 1,
  'name'  : 'Kenneth Auchenberg',
  'avatar': 'http://cdn0.4dots.com/i/customavatars/avatar7112_1.gif',
  'icon'  : 'icon-16 icon-person',
  'type'  : 'contact',
  'value' : 'Kenneth Auchenberg' // *new* the value to be displayed when displaying the mention
}
</pre>
<table>
  <tr>
    <td><b>avatar</b></td>
    <td></td>
    <td class="definition">
      property is a URL used for image avatars when  "showAvatars"-option is enabled 
    </td>
  </tr>
  <tr>
    <td><b>icon</b></td>
    <td></td>
    <td class="definition">
      property is a className used for avatars when "showAvatars"-option is disabled
    </td>
  </tr>
  <tr>
    <td><b>type</b></td>
    <td></td>
    <td class="definition">
      property specifies an object type which is used in the marked-up version of the mentions result
    </td>
  </tr>
</table>


<h2>Markup format</h2>
<p>When mentions are being added to the input, a marked-up version of the value is generated, to allow the mentions to be extracted, parsed and stored later. </p>
<pre>
  This is a message for @[name](type:id) #[name](type:id)
</pre>
<p>Like:</p>
<pre>
  This is a message for @[Kenneth Auchenberg](contact:1) #[Issue 22](tag:22)
</pre>


<h2>Browser support</h2>
<p>jquery.mentionsInput has been tested in Firefox 6+, Chrome 15+, and Internet Explorer 8+. </p>
<p>Please let us know if you see anything weird. And no, we will no make it work for older browsers. Period. </p>

<h2>Dependencies</h2>
<p>jquery.mentionsInput is written as a jQuery extension, so it naturally requires <a href="http://jquery.com">jQuery (1.6+)</a>. In addition to jQuery, it also depends on <a href="http://documentcloud.github.com/underscore/">underscore.js (1.2+)</a>, which is used to simplify stuff a bit.</p>

<p>The component is also using the new HTML5 "input" event. This means older browsers like IE8 need a polyfill which emulates the event (it is bundled).</p>

<p>The component itself is implemented as a small independent function, so it can easily be ported to frameworks other than jQuery. </p>

<p>Furthermore all utility functions have been centralized in the utils-object, which can be replaced with references if you already got functions like htmlEncode, etc. </p>

<p>To make the component grow and shrink to fit it’s content, you can include <a href="http://www.unwrongest.com/projects/elastic">jquery.elastic.js</a></p>

<h2>License</h2>
<p>MIT License - <a href="http://www.opensource.org/licenses/mit-license.php">http://www.opensource.org/licenses/mit-license.php</a></p>

<h2>Change Log</h2>

<p>
  <b class="header">1.0.1</b><br/>
  <ul>
    <li>Removed elastic-option since it wasn't really working without it. <a href="https://github.com/podio/jquery-mentions-input/issues/1"> https://github.com/podio/jquery-mentions-input/issues/1</a>)</li>
    <li>Fixed issue with space on search queries. (<a href="https://github.com/podio/jquery-mentions-input/issues/24"> https://github.com/podio/jquery-mentions-input/issues/24</a>)</li>
  </ul>
</p>

<p>
  <b class="header">1.0.0</b><br/>
  <ul>
    <li>Initial release.</li>
  </ul>
</p>