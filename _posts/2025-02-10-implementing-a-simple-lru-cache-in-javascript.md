---
title:        "Implementing a Simple LRU Cache in JavaScript"
description:  ""
author:       "sarbull"
---

<pre class="stackoverflow-light"><code class="hljs language-javascript">const searchInArrayByObjectKey = (data, key) => {
  return data.find(d => d.key === key);
};

const removeFromArrayByObjectKey = (data, key) => data.filter((d) => d.key !== key);

class LRUCache {
  constructor(size) {
    this.size = size;
    this.cache = []; // {key: key, value: value }
  }

  get(key) {
    const result = searchInArrayByObjectKey(this.cache, key);

    if(result) {
      this.cache = removeFromArrayByObjectKey(this.cache, result.key);
      this.cache.unshift(result);

      return result;
    } else {
      return -1;
    }
  }

  put(key, value) {
    if(this.cache.length === this.size) {
      return;
    }

    if(this.cache.length < this.size) {
      this.cache = removeFromArrayByObjectKey(this.cache, result.key);

      this.cache.unshift({key: key, value: value});
    }
  }
}


const cache = new LRUCache(3);
cache.put(1, 1); // [{key: 1, value: 1}]
cache.put(2, 2); // [{key: 2, value: 2}, {key: 1, value: 1}]
cache.put(3, 3); // [{key: 3, value: 3}, {key: 2, value: 2}, {key: 1, value: 1}]
cache.get(2);    // [{key: 2, value: 2}, {key: 3, value: 3}, {key: 1, value: 1}]
cache.put(4, 4); // [{key: 2, value: 2}, {key: 3, value: 3}, {key: 1, value: 1}]
</code></pre>
