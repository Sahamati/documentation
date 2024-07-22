# APIs Integration

## Current API reference <a href="#current-api-reference" id="current-api-reference"></a>

With the current structure, the API requests are sent to the respective recipient NP directly. This requires each NP to understand the metadata of the recipient NP and use their base path while sending.

<figure><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXd6EmCqn8tdJ2j5W6K_0FDDFeOZPkEKE7-R_Eg33V1Lw0_p1RxuRkX1MyRPz7hnl0McyDLO5naiug60trewGGnIH4zhXO6mTVCf0dRdzL8wm8C2N9EMX-N9TTOc3D-kWyOelh_qf7ETqkENzDDSzRjRaeU?key=-pgXoRMAdWw9sxqZ3vSv2A" alt=""><figcaption><p>Existing approach to use the APIs by AA Ecosystem</p></figcaption></figure>

## Using Sahamati Proxy APIs <a href="#using-sahamati-proxy-apis" id="using-sahamati-proxy-apis"></a>

Sahamati Proxy makes it easy for the NPs to send the request to any recipient just by adding the **recipient identifier** in the request body under **meta.headers** section.

<figure><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXfIYCvZR5ZrzWVGZSHBqc4v-591dvRD7iAbyyfcmGOhrbouc1DNN_OGOGxNHDBB5bK-UiyXEzx7wo6OvVokf-zJiA-sfN8sJ4n_k7UPXf4I5BkqdLdLl44n3Bs8BwMmoZ97ZItvZCNIyl2cLufLgvRU2XTj?key=-pgXoRMAdWw9sxqZ3vSv2A" alt=""><figcaption><p>Using Sahamati Proxy APIs for AA Ecosystem</p></figcaption></figure>

<table><thead><tr><th width="157">Particulars</th><th>Comments</th><th></th></tr></thead><tbody><tr><td>Host</td><td>The base path to use by the participants of Sahamati Proxy.</td><td>​<a href="https://proxy.sandbox.sahamati.org.in/">https://proxy.sandbox.sahamati.org.in</a>​</td></tr><tr><td>Headers</td><td>This will remain same as previous.</td><td><p>​</p><ul><li>x-jws-signature - Authorization</li><li>Token (from sender)</li></ul></td></tr><tr><td>recipientid</td><td>The recipientid is a required property. It is the identifier of the receiver to whom the API call needs to be forwarded.</td><td><pre class="language-json"><code class="lang-json">{
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
