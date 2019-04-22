---
title: "Search"

---
 
<div id="search-box">
    <!-- 検索ボックス用の空DOM -->
</div>
 
<ul id="hits">
    <!-- 検索結果用のDOM、各結果をliで置くためulにしている -->
</ul>
 
<div id="pagination">
    <!-- ページネーションがここに -->
</div>
 
<script>
// instantSearchを初期化
var search = instantsearch({
  appId: '6C1J28V810',
  apiKey: '7d50e48dd57edf7bcf0e8ad4ddf199cc',
  indexName: 'marsblog',
  urlSync: true
});
 
// 検索ボックスをDOMに設定
search.addWidget(
  instantsearch.widgets.searchBox({
	  container: '#search-box',
	  placeholder: '記事を検索',
	  poweredBy: true
  })
);
 
// 検索結果をDOMに設定
// 結果には<li>を使うように
search.addWidget(
  instantsearch.widgets.hits({
	  container: '#hits',
	  templates: {
      empty: '見つかりませんでした。',
	    item: '<li><code>{{ dateString }}</code> <a href="{{permalink}}">{{ title }}</a></li>'
	  }
  })
);
 
// 検索結果をページネーションするための設定
search.addWidget(
  instantsearch.widgets.pagination({
	  container: '#pagination',
	  maxPages: 20,
	  scrollTo: false
  })
);
 
search.start();
</script>