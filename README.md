# TestDaF Test Centre Map
A map of all German TestDaF test centres. 

Clicking through the list of test centres can be tedious if you are simply trying to find the centre closest to you. Therefore, I have taken the information from the [TestDaF website](https://www.testdaf.de/index.php?id=181) and plotted them on a map.

![Map of German TestDaF test centres](https://i.imgur.com/3LYlr43.jpg).

Visit the interactive version [here](https://www.mapcustomizer.com/map/testdafmap) (unfortunately, not all places could be mapped, and some are mapped incorrectly).

A complete list (as of 11.02.2019) of all test centres can be found in `testcentres.txt`. The output from scraping can be found in `testcentres.xlsx`.

# Updating

To update the map to reflect any changes on the TestDaF website, follow the steps outlined below.

## Scrape

1. use any scraping tool to get the list of test centres from the TestDaF website
    1. for example the [webscraper.io](https://www.webscraper.io/) Chrome extension.
    2. or manually copy all the place names ;)
2. Use the following entry points for the scraper
    1. `https://www.testdaf.de/fuer-teilnehmende/die-pruefung/testzentren/testzentren-in-deutschland-von-a-bis-c`
    2. `https://www.testdaf.de/fuer-teilnehmende/die-pruefung/testzentren/testzentren-in-deutschland-von-a-bis-c/testzentren-deutschland-von-d-bis-f/`
    3. `https://www.testdaf.de/fuer-teilnehmende/die-pruefung/testzentren/testzentren-in-deutschland-von-a-bis-c/testzentren-deutschland-von-g-bis-i/`
    4. `https://www.testdaf.de/fuer-teilnehmende/die-pruefung/testzentren/testzentren-in-deutschland-von-a-bis-c/testzentren-deutschland-von-j-bis-l/`
    5. `https://www.testdaf.de/fuer-teilnehmende/die-pruefung/testzentren/testzentren-in-deutschland-von-a-bis-c/testzentren-deutschland-von-m-bis-o/`
    6. `https://www.testdaf.de/fuer-teilnehmende/die-pruefung/testzentren/testzentren-in-deutschland-von-a-bis-c/testzentren-deutschland-von-p-bis-s/`
    7. `https://www.testdaf.de/fuer-teilnehmende/die-pruefung/testzentren/testzentren-in-deutschland-von-a-bis-c/testzentren-deutschland-von-t-bis-z/`
3. And the following CSS selector
    1. `div.deut_einzel > ul > li:nth-of-type(1), li:nth-of-type(2) li a.testtz`
    2. make sure to enable multiple selections
4. begin scraping and download the CSV file

## Prepare

1. Take the CSV file and extract the column with place names
2. Remove any empty entries
3. Remove line breaks and tabs within entries
4. remove any numbers that my accidently be within an entry
    1. ```vba
        Function RemoveNumbers(Txt As String) As String
        With CreateObject("VBScript.RegExp")
        .Global = True
        .Pattern = "[0-9]"
        RemoveNumbers = .Replace(Txt, "")
        End With
        End Function
        ```
        A VBA script for Excel that removes numbers
5. export list of cleaned place names

## Map

1. Map the list of places in any mapping software
    1. [Mapcustomizer](https://www.mapcustomizer.com/#) is convenient because it has a bulk input option.
2. Enjoy an easily accessible map of TestDaF centres.
