# Actor - Torrent Downloader

## Torrent downloader

Since some of the countries doesn't allow the people to download Torrent files or using the Torrent infrastucture, this actor should help you to download any Magnet, HTTP or HTTPS torrent file without any restrictions.

The Torrent data scraper supports the following features:

-   Download any Torrent file - You can paste any Magnet, HTTP or HTTPS torrent file that you want to download

-   Optional Seeding - If you just want to download files rather than seeding them, it is optional for you to do it.

## Disclaimer

**Please keep in mind that this actor is a toolset and the person or company who uses this actor is fully responsible of all the legal statements. Both Apify and the creator(s) of the actor are not responsible for the usage or the actions.**

## Bugs, fixes, updates and changelog

This actor is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/torrent-downloader/issues).

### Incoming Changes

-   Maximum number of connections per torrent
-   Enabling/Disabling trackers
-   More detailed/visual messages about the progress
-   Better compression and memory consumption on actor

## Input Parameters

The input of this actor should be JSON containing the list of URLs of Torrent files. Fields are:

| Field         | Type    | Description                                                                                              |
| ------------- | ------- | -------------------------------------------------------------------------------------------------------- |
| startUrls     | Array   | (optional) List of Torrent URLs. You should only provide torrent file URLs. Can be Magnet, HTTP or HTTPS |
| enableSeeding | Boolean | (optional) Enables the seeding for the torrents. Default is `false`.                                     |
| disableLogs   | Boolean | (optional) Disables the informative messages from the actor logs. Default is `false`.                    |

## Tip

**You can find the download link of the files from the dataset. All the files will be saved into an independent Key Value Store and the dataset contains the links for each of them**

When you want to download a specific file, it is good to right click and "Copy the link" the target URL and paste it to **startUrl** array.

If you enabled seeding by `enableSeeding:true`, then the actor will run forever. So if you are using the API, the best way to get all the files in a proper way is to poll the actor dataset and check if the files exist there or not.

The actor's storage is double the size of the memory that you are giving. So it is always better to use the memory as twice as the size of the file(s) for compression and downloading purposes.

### Compute Unit Consumption

The actor optimized to run blazing fast and download files as soon as possible If actor gets proper amount of seeders it'll going to consumpt ~0.1 CUs per 5 minutes.

### Torrent Actor Input example

```json
{
    "startUrls": [
        "magnet:?xt=urn:btih:04EB41CC8C939DFEA23898A0C1CA80BBC72649D0&dn=700+Adult+Books+in+txt+format+%28some+with+covers%29&tr=udp%3A%2F%2Ftracker.coppersurfer.tk%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.openbittorrent.com%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.opentrackr.org%3A1337&tr=udp%3A%2F%2Ftracker.leechers-paradise.org%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.dler.org%3A6969%2Fannounce&tr=udp%3A%2F%2Fopentracker.i2p.rocks%3A6969%2Fannounce&tr=udp%3A%2F%2F47.ip-51-68-199.eu%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.internetwarriors.net%3A1337%2Fannounce&tr=udp%3A%2F%2F9.rarbg.to%3A2920%2Fannounce&tr=udp%3A%2F%2Ftracker.pirateparty.gr%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.cyberia.is%3A6969%2Fannounce",
        "magnet:?xt=urn:btih:EB123A26408CA931FD8B99126C6A636C3F1250EB&dn=Atlas+Shrugged+Ebook+%28Epub%2C+Mobi%2C+Pdf%2C+Txt%29&tr=udp%3A%2F%2Ftracker.coppersurfer.tk%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.openbittorrent.com%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.opentrackr.org%3A1337&tr=udp%3A%2F%2Ftracker.leechers-paradise.org%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.dler.org%3A6969%2Fannounce&tr=udp%3A%2F%2Fopentracker.i2p.rocks%3A6969%2Fannounce&tr=udp%3A%2F%2F47.ip-51-68-199.eu%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.internetwarriors.net%3A1337%2Fannounce&tr=udp%3A%2F%2F9.rarbg.to%3A2920%2Fannounce&tr=udp%3A%2F%2Ftracker.pirateparty.gr%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.cyberia.is%3A6969%2Fannounce"
    ],
    "enableSeeding": false,
    "disableLogs": false
}
```

## During the Run

During the run, the actor will output messages letting you know what is going on. You can enable or disable the informative messages from the Input Schema if it is necessary.

If you provide incorrect input to the actor, it will immediately stop with failure state and output an explanation of what is wrong.

## Torrent Actor Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Torrent actor.

## Output schema

The structure of each item on dataset when the files are downloaded.

```json
{
    "name": "Atlas Shrugged",
    "url": "https://api.apify.com/v2/key-value-stores/default/records/10122021170156508"
}
```
