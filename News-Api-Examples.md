# News API usage examples

Here you will find some example of how to use the [`news_provider` widget constructor option](Widget-Constructor#news_provider).

## Setting the widget title

To set the news widget title use the optional `title` property.

```javascript
new TradingView.widget({
    /* other widget options hidden for simplicity */
    news_provider: function getNews(symbol, callback) {
        callback({
            title: 'This is the title!',
            newsItems: [/* ... */]
        })
    }
});
```

## Fetching non-RSS news

Let's say we have a API endpoint that returns a JSON representation of news items that match the `NewsItem` interface.

```javascript
const jsonNewsApiUrl = 'https://www.example.com';

new TradingView.widget({
    /* other widget options hidden for simplicity */,
    news_provider: function getNews(symbol, callback) {
        fetch(jsonNewsApiUrl)
            .then(res => res.json())
            .then(json => {
                callback({
                    newsItems: json,
                });
            });
    }
});
```

## Updating news on demand

Let's say we want to refresh the news on demand, for example after some user event. We can use `INewsApi`'s `update` method.

```javascript
const widget = new TradingView.widget({
    /* widget options hidden for simplicity */
});

function someEventHandler() {
    widget.news().then(newsApi => newsApi.refresh());
}
```
