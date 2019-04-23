---
title: "Search"
---
 
<div id="search-box">

</div>
 
<ul id="hits">
</ul>
 
<div id="pagination">
</div>

<script>

var search = instantsearch({
  appId: ALGOLIA_APP_ID,
  apiKey: ALGOLIA_ADMIN_KEY,
  indexName: ALGOLIA_INDEX_NAME,
  urlSync: true
});

search.addWidget(
  instantsearch.widgets.searchBox({
	  container: '#search-box',
	  placeholder: 'Search',
	  poweredBy: true
  })
);
 

search.addWidget(
  instantsearch.widgets.hits({
	  container: '#hits',
	  templates: {
      empty: '查無資料。',
	    item: '<li> <a href="{{permalink}}">{{ title }}</a>  <code>{{ publishdate }}</code></li>'
    	// </br> <a href="{{permalink}}">{{ title }} </a>
	  }
  })
);
 
search.addWidget(
  instantsearch.widgets.pagination({
	  container: '#pagination',
	  maxPages: 20,
	  scrollTo: false
  })
);
 
search.start();
</script>