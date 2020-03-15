# DealEngine Take Home Project: Scraping CWRU Google Groups for Mailing List

> This short script scraps CWRU Google Groups and collects a exposed mailing list of `@case.edu` accounts.

---
## Privacy
Run the following command to avoid synchronizing the content within `my_cwru_token.py` to GitHub, for privacy concerns.
```
git update-index --assume-unchanged my_cwru_token.py
```

## Run
Fill in your credential in `my_cwru_token.py`, and run the `google_group_scraper` (available in both `.ipynb` and `.py`) however you'd like.
Note it take quite a well to complete the task, and you might need to adjust the `time.sleep()` wait time to accompany your internet environment.

You may expect a mailing list output at `CWRU_scrapped_mailing_list.txt`.

## Reflection

This scripts focus on giving a clean and concise delivery, but not a perfect one. Several improvements I could think of include:

1. Identify private group at the `forumsearch` layer (probably not much performance gain since now the script does the check in `forum` layer with an exception handling, which is really fast).
2. Implement a counter on the number of non-private forums (or even number of posts available for scrape), so that we may scroll the `forumsearch` page more rationally — now we have 300 `Keys.END`, which is way too much.
3. Register the total number of post available of each forum, and implement dynamic `WAIT` time on `forum` layer incrementally, so that all posts are guaranteed to be scraped.
4. Implement a check on `forum` layer to skip posts from the same sender with no other reply (as such account is likely scrapped already).
5. Use RSS source link like [this](https://groups.google.com/a/case.edu/forum/feed/cwrumocktrial/msgs/rss_v2_0.xml?num=100) instead of [standard Google Group URL](https://groups.google.com/a/case.edu/forum/feed/cwrumocktrial/msgs/rss_v2_0.xml?num=100), as it will functionally skips all scrolling on the `forum` layer. I did not proceed on this route as I "magic-numbered" the `forumsearch` layer, I feel like if I shortcut the `forum` layer as well there will be no much learning. I also did not use anything like [gggd](https://github.com/henryk/gggd) for the same reason.



--
### Ref.

* [2018-Teatime-W4a-Web Scraping | SDLE Research Center](https://www.youtube.com/watch?v=XuTxkXW2lzw&app=desktop)
* [Scrape dynamic web page (Google Group forum) using Selenium (1) | Huidong Tian](https://withr.github.io/scrape-dynamic-web-page-using-selenium-1/)
