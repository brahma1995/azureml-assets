This flow template is an advanced RAG flow modeled on the implementation of Azure AI Playground - on Your Data. The flow consists of tools that rewrites user query input into one or more queries based on chat history context using LLM, retrieves data for rewritten queries from the data index and generates a chat response from LLM by augmenting the prompt with retrieved data as well as chat history.

### Inference samples

Inference type|CLI|VS Code Extension
|--|--|--|
Real time|<a href="https://microsoft.github.io/promptflow/how-to-guides/deploy-a-flow/index.html" target="_blank">deploy-promptflow-model-cli-example</a>|<a href="https://microsoft.github.io/promptflow/how-to-guides/deploy-a-flow/index.html" target="_blank">deploy-promptflow-model-vscode-extension-example</a>
Batch | N/A | N/A

### Sample inputs and outputs (for real-time inference)

#### Sample input
```json
{
    "inputs": {
      "query": "how much does the Trailwalker hiking shoes cost?"
    }
}
```

#### Sample output
```json
{
  "outputs": {
    "reply": "The TrailWalker Hiking Shoes cost $110. [doc1].",
    "documents": [
      {
        "content": "<p>the TrailWalker Hiking Shoes for a weekend hiking trip, and they exceeded my expectations. The fit is comfortable, providing excellent support throughout the journey. The traction is impressive, allowing me to confidently tackle various terrains. The shoes are also durable, showing no signs of wear after a challenging hike. My only minor complaint is that they could provide slightly more cushioning for longer treks. Overall, these shoes are a reliable choice for outdoor enthusiasts.\\n\\n2) <strong>Rating:</strong> 5\\n</p>",
        "score": 0.06557377049180328,
        "metadata": null,
        "title": "# Information about product item_number: 11\\nTrailWalker Hiking Shoes, price $110",
        "filepath": "product_info_11.md",
        "url": "https://foo.blob.core.windows.net/product-info/product_info_11.md",
        "chunk_id": "0"
      },
      {
        "content": "<p>of the laces by pulling both ends simultaneously. Find the desired tightness and comfort level.\\n4. Push the lace lock down to secure the laces in place.\\n5. Tuck any excess lace into the lace pocket for safety and to prevent tripping.\\n\\nNote: It's recommended to wear hiking socks for the best fit and to prevent blisters or discomfort.\\n\\n</p>",
        "score": 0.06451612903225806,
        "metadata": null,
        "title": "# Information about product item_number: 11\\nTrailWalker Hiking Shoes, price $110",
        "filepath": "product_info_11.md",
        "url": "https://foo.blob.core.windows.net/product-info/product_info_11.md",
        "chunk_id": "0"
      },
      {
        "content": "<p>disregard safety precautions:<strong> While the TrekReady Hiking Boots provide support and protection, they do not guarantee immunity from accidents or injuries. Always exercise caution and follow proper hiking safety guidelines, such as using trekking poles, wearing appropriate clothing, and being aware of your surroundings.\\n</p>",
        "score": 0.015384615384615385,
        "metadata": null,
        "title": "# Information about product item_number: 4\\nTrekReady Hiking Boots, price $140",
        "filepath": "product_info_4.md",
        "url": "https://foo.blob.core.windows.net/product-info/product_info_4.md",
        "chunk_id": "0"
      }
    ]
  }
}
```
