=  Creating a network from a table of cooccurring items
Clément Levallois <clementlevallois@gmail.com>
2017-02-27

last modified: {docdate}

:icons: font
:iconsfont:   font-awesome
:revnumber: 1.0
:example-caption!:
:sourcedir: ../../../../main/java

:title-logo-image: gephi-logo-2010-transparent.png[width="450" align="center"]

image::gephi-logo-2010-transparent.png[width="450" align="center"]
{nbsp} +

//ST: 'Escape' or 'o' to see all sides, F11 for full screen, 's' for speaker notes


== Presentation of the plugin
//ST: Presentation of the plugin

//ST: !

This plugin is created by https://www.clementlevallois.net[Clement Levallois].

It converts a spreadsheet or a csv file into a network.

//ST: !

This plugin enables you to:

*   Start from a data table in Excel or csv format
*   In the data table, each row describes an "occurrence" (of an event, a purchase, a relation, etc.)
*   In columns A, B, C, D, we have the entities involved: column A for persons, column B for what they bought, etc.
*   Connections will be created between entities, when they appear in the same occurrence (so, when they are on thee same row)
*   Occurrences can have dates, multiple instances of an entity can be listed in a given column.

//ST: !
==== 1. The input
//ST: !

image::en/cooccurrences-computer/excel-1-en.png[align="center", title="An Excel file"]
{nbsp} +


//ST: !
==== 2. The output
//ST: !

image::en/cooccurrences-computer/gephi-result-1-en.png[align="center", title="Resulting network"]
{nbsp} +

== Installing the plugin
//ST: Installing the plugin
//ST: !

image::Choose-the-menu-Tools-then-Plugins.png[align="center", title="Choose the menu Tools then Plugins"]
{nbsp} +

//ST: !

image::Click-on-the-tab-Available-Plugins.png[align="center", title="Click on the tab Available Plugins"]
{nbsp} +

//ST: !

image::Install-the-plugin-then-restart-Gephi.png[align="center", title="Install the plugin then restart Gephi"]
{nbsp} +

== Opening the plugin
//ST: Opening the plugin
//ST: !

image::Open-the-plugin-via-the-menu-File---Import.png[align="center", title="Open the plugin via the menu File - Import"]
{nbsp} +

== Using the plugin
//ST: Using the plugin

//ST: !
==== 2nd panel
//ST: !

image::Select-a-file.png[align="center", title="Select a file"]
{nbsp} +

//ST: Is your file with a header?

//ST: !

image::en/cooccurrences-computer/excel-2-en.png[align="center", title="A file without headers"]
{nbsp} +

//ST: !

image::en/cooccurrences-computer/excel-1-en.png[align="center", title="A file with headers"]
{nbsp} +

//ST: !
To describe the next screens of the plugin, we will take the example of *the Excel file just shown*, with headers.

//ST: !
==== 3rd panel
//ST: !

image::en/cooccurrences-computer/plugin-panels-1-en.png[align="center", title="Which entities should be the nodes?"]
{nbsp} +

//ST: !
What does this panel mean?

If you look back at the Excel file, you see that we have "Clients" and their "Purchases".

-> This means we can build 2 different types of networks, depending on our needs:

//ST: !

1. A network showing clients and products, with relations representing purchases from a client to a product.

[graphviz, client-to-product, png]
----
graph g {
    rankdir="LR";
    client -- product [ label="purchased" ]
}
----

To create this kind of networks, choose "Client" in the upper window, and "Purchases" in the lower window of the plugin screen.


//ST: !
[start=2]
2. Or a network where 2 products are connected, if one client puchased them together.

[graphviz, product-to-product, png]
----
graph g {
    rankdir="LR";
    a -- b [label=" purchased together"]
     a [label="product 1"];
     b [label="product 2"];
}
----

To create this kind of networks, choose "Purchases" in the upper [underline]#and# lower windows of the plugin screen.


//ST: !
==== 4th panel
//ST: !

image::en/cooccurrences-computer/subfield-delimiter-en.png[align="center", title="Choosing which delimiter is used"]
{nbsp} +

//ST: !

This 3rd panel asks: in our Excel file, how are different items separated in a given cell?
In our example, we have used commas: the lists of products purchased are comma-separated:

image::commas-shown-in-red.png[align="center", title="commas shown in red"]
{nbsp} +


//ST: !
==== 5th panel
//ST: !

This panel allows you to specify whether the relations are dynamic in time, or not.

In this case, you need an extra column (column C), where a date is shown. We don't cover this case here.

(read the tutorials on dynamic networks for a starter)


//ST: !
==== 6th panel
//ST: !

image::en/cooccurrences-computer/panel-6-1-en.png[align="center", title="Options panel"]
{nbsp} +

//ST: !

 "Create links between Purchases agents and links between Purchase agents"

-> If you chose a Product <--> Product kind of network in panel 3, then of course you are interested in links between products. *Check the box*.

//ST: !

-> But if you chose a Client <--> Product kind of network  in panel 3, what you need is less obvious.

Let's take the example of client I, who purchased a table and some chairs:

//ST: !

1. Checking the box will create a network where:

[graphviz, inner-links-included, png]
----
graph g {
    rankdir="LR";
    a -- b [label=" purchased"]
    a -- c [label=" purchased"]
    b -- c [label=" co-purchased"]

     a [label="client I"];
     b [label="table"];
     c [label="chairs"];

}
----

//ST: !

1. *Not* checking the box will create a network where:

[graphviz, inner-links-excluded, png]
----
graph g {
    rankdir="LR";
    a -- b [label=" purchased"]
    a -- c [label=" purchased"]

     a [label="client I"];
     b [label="table"];
     c [label="chairs"];

}
----

//ST: !

 "Remove duplicates"

-> Check this option if your Excel or csv file has duplicate rows that you'd like to be removed

//ST: !

 "Remove self-loops"

If a Client has purchased tables twice, so that we have "table, table" in a cell: this would create a link from table to table (a *self loop*).

-> Check this option if you'd like self loops to be removed.

//ST: !
==== 7th panel
//ST: !

This panel recaps all the settings. Click on finish to create the network.

== The end
//ST: The end!

Visit https://www.facebook.com/groups/gephi/[the Gephi group on Facebook] to get help,

or visit https://seinecle.github.io/gephi-tutorials/[the website for more tutorials]
pass:[    <!-- Start of StatCounter Code for Default Guide -->
    <script type="text/javascript">
        var sc_project = 11238920;
        var sc_invisible = 1;
        var sc_security = "8dac6cd5";
        var scJsHost = (("https:" == document.location.protocol) ?
            "https://secure." : "http://www.");
        document.write("<sc" + "ript type='text/javascript' src='" +
            scJsHost +
            "statcounter.com/counter/counter.js'></" + "script>");
    </script>
    <noscript><div class="statcounter"><a title="site stats"
    href="http://statcounter.com/" target="_blank"><img
    class="statcounter"
    src="//c.statcounter.com/11238920/0/8dac6cd5/1/" alt="site
    stats"></a></div></noscript>
    <!-- End of StatCounter Code for Default Guide -->]
