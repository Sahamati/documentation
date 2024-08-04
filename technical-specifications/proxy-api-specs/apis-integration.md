# APIs Integration

## Current API reference <a href="#current-api-reference" id="current-api-reference"></a>

With the current structure, the API requests are sent to the respective recipient member directly. This requires each member to understand the metadata of the recipient member and use their base path while sending.

<figure><img src="../../.gitbook/assets/Proxy-Existing-workflow.png" alt=""><figcaption><p>Existing approach to use the APIs by AA Ecosystem</p></figcaption></figure>

## Using Sahamati Proxy APIs <a href="#using-sahamati-proxy-apis" id="using-sahamati-proxy-apis"></a>

Sahamati Proxy makes it easy for the members to send the request to any recipient just by adding the **recipient identifier** in the request body under **meta.headers** section.

<figure><img src="../../.gitbook/assets/proxy-new-workflow.png" alt=""><figcaption><p>Using Sahamati Proxy APIs for AA Ecosystem</p></figcaption></figure>

<table><thead><tr><th width="157">Particulars</th><th width="176">Comments</th><th></th></tr></thead><tbody><tr><td>Host</td><td>The base path to use by the members of Sahamati Proxy.</td><td><a href="https://api.sandbox.sahamati.org.in/proxy">​https://api.sandbox.sahamati.org.in/proxy</a></td></tr><tr><td>Headers</td><td>This will remain same as previous.</td><td><p>​</p><ul><li>x-jws-signature - Authorization</li><li>Token (from sender)</li></ul></td></tr><tr><td>recipientid</td><td>The recipientid is a required property. It is the identifier of the receiver to whom the API call needs to be forwarded.</td><td><pre class="language-json"><code class="lang-json">{
 "meta": 
  {
    "headers": {
      "recipientid": ""
    }
  },
  "data" : {
  ………..
  }
}
</code></pre></td></tr><tr><td>senderid</td><td>The receiver will get the senderid, the identifier of the sender who initiated the API call.</td><td><pre class="language-json"><code class="lang-json">​{ 
  "meta": 
  {
    "headers": {
      "senderid": ""
    }
  },
  "data" : {
  ………..
  }
} 
</code></pre></td></tr></tbody></table>
