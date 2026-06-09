---
title: Open source web map creation with qgis2web and GitHub Pages   # Title of the page, which will be displayed in the navigation and the browser title.
layout: page  # Layout type, usually 'page' for standard pages.
nav_order: 1  # Order in the navigation menu.
description: This tutorial shows you how to design a map in QGIS3, then deploy it to the web using qgis2web and GitHub Pages. # A brief description of the page for SEO purposes.
permalink: /  # Optional: Custom URL for the page. It will serve as the slug. For example, /home/
created_date: 2026-06-08 # Date when the page was created. Should be in YYYY-MM-DD format.
has_children: False  # Set to True if the page has sub-pages.
staff:  # Optional: Nested list of staff members associated with the page.
  - name: Cole White  # PLACEHOLDER: Replace with actual staff member's name.
    link: https://library.utoronto.ca/staff/cole-white  # link is optional
maintainer:
  - name: Cole White  # PLACEHOLDER: Replace with actual maintainer's name.
    link: https://example.com/cole-white  # link is optional
# student_staff:  
# - name: Student Name
#   link: https://example.com/student-name
# - name: Another Student
#   link: https://example.com/another-student  # link is optional
---

# Open source web map creation with qgis2web and GitHub Pages

<img src='{{ '/assets/images/qgis2web-logo.png' | relative_url }}' alt="
qgis2web logo"
width='60%' />

If you'd like to <b>publicly share an interactive visualization</b> based on your spatial data, 
<b>qgis2web</b> provides a quick and easy way to do this. The
underlying HTML, CSS, and JavaScript code of your web map can then be endlessly
customized if you have web development skills or would like to learn them.

This tutorial makes use of three different development tools:

* <b><a href="https://www.qgis.org" target="_blank">QGIS</a></b> is a 
<b>free, open source GIS desktop application</b> that runs on Windows, MacOS,
and Linux. If you're new to QGIS, please see the Map and Data Library's <b><a href="
https://mdlutoronto.github.io/qgis-mapping-spatial-analysis-intro/" target=
"_blank">
introductory QGIS tutorial</a></b> before proceeding. QGIS 3.44 in Windows is
used in this example, but the process will be very similar with other versions
of the software or other operating systems. The <b>qgis2web</b> plugin will be
added to your installation of QGIS and used to create the web map.

* <b><a href="https://leafletjs.com" target="_blank">Leaflet</a></b> is an <b>open
source mapping library</b> for the <b>JavaScript</b> programming language,
which is one of the core technologies underlying modern websites. Leaflet is a
beginner-friendly option for creating custom interactive web maps.

* <b><a href="https://www.github.com/" target="_blank">GitHub</a></b> is a web
platform that allows users to share code and other data.
Code uploaded to your GitHub account can be turned into a live website using a
feature called <b>GitHub Pages</b>. We recommend
this as a reliable way to host digital content at no cost.

Because you're using <b>free and/or open source tools</b>, you'll have complete control over your
work and won't be subject to the subscription or licensing restrictions you
might find with proprietary software, such as ArcGIS.

You can follow the steps of this tutorial using your own data. Alternatively,
<b>download and unzip the sample data (Toronto subway lines and stations) used in the
examples <a href="{{ '/assets/data.zip' | relative_url }}">here</a></b>.

## Set up QGIS: Install plugins

* Open QGIS. Click <b>Plugins → Manage and install plugins</b>.

<a href='{{ '/assets/images/qgis-plugins-manage-and-install-plugins.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/qgis-plugins-manage-and-install-plugins.png' | relative_url }}' alt="
QGIS → Plugins → Manage and install plugins" width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

* Click the <b>All</b> tab to the left.

<a href='{{ '/assets/images/plugins-all-tab.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/plugins-all-tab.png' | relative_url }}' alt="
QGIS → Plugins → Manage and install plugins → 'All' tab" width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

* Search for <b>qgis2web</b>. Click the <b>qgis2web</b> result, then click the
<b>Install plugin</b> button.

<a href='{{ '/assets/images/install-qgis2web.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/install-qgis2web.png' | relative_url }}' alt="
Search for and install qgis2web" width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

* <b>Optional</b>: Install the <b><a href="
https://plugins.qgis.org/plugins/quick_map_services/" target="_blank">
NextGIS QuickMapServices</a></b> plugin. This tool
makes it easy to add basemaps to your project. You don't need this plugin to
use qgis2web, but it will be helpful if you want to replicate the example
shown in this tutorial.

<a href='{{ '/assets/images/install-quickmapservices.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/install-quickmapservices.png' | relative_url }}' alt="
Install the Quickmapservices plugin (optional)" width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

## Create and configure the QGIS project

* In QGIS, click the <b>New project</b> button.

<a href='{{ '/assets/images/new-project.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/new-project.png' | relative_url }}' alt="
QGIS → new project" width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

* Add your data layers to the map. (If you're using the
<a href="{{ '/assets/data.zip' | relative_url }}">sample data</a>, these will
be found in <b>data.gpkg</b>.)

<a href='{{ '/assets/images/qgis-add-data.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/qgis-add-data.png' | relative_url }}' alt="
New QGIS project with data layers added" width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

* Optionally, add a <b>basemap</b>. If you know the URL of the basemap you'd like to
use, go to <b>Layer → Add Layer → Add XYZ Layer</b> and paste it in. Or, as shown in this
example, use the <a href="
https://plugins.qgis.org/plugins/quick_map_services/" target="_blank"><b>
QuickMapServices</b></a> plugin.

<a href='{{ '/assets/images/qgis-add-basemap.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/qgis-add-basemap.png' | relative_url }}' alt="
Add a basemap using the QuickMapServices plugin" width='100%' height='100%'
style="border: 3px solid #888888;" />
</a>

* In the Layers Panel, give your layers <b>human-friendly names</b> by right-clicking
on their names and selecting <b>Rename Layer</b>. This is how
their names will appear in the legend when your web map is published.

<a href='{{ '/assets/images/rename-layer.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/rename-layer.png' | relative_url }}' alt="
Right-click layer name → Rename Layer" width='100%' height='100%'
style="border: 3px solid #888888;" />
</a>

<a href='{{ '/assets/images/renamed-layers.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/renamed-layers.png' | relative_url }}' alt="
Layers with human-friendly names - Subway Station, Subway Line, Basemap"
width='50%' style="border: 3px solid #888888;" />
</a>

* Adjust your layers' <b>symbology</b> to your liking. In this example, the subway
lines use <b>Categorized</b> symbology, with <b>ROUTE_NAME</b> as the <b>value field</b>. The
subway stations also use Categorized symbology, with <b>Wheelchair Accessible</b> as
the value field. More information on symbology can be found in the Map and
Data Library's introductory QGIS tutorial
<a href="https://mdlutoronto.github.io/qgis-mapping-spatial-analysis-intro/08-symbology/" target="_blank">
here</a>.

<a href='{{ '/assets/images/symbology.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/symbology.png' | relative_url }}' alt="
Symbolized map layers"
width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

* Enable and configure any <b>labels</b> you'd like to appear on your map.
Here, subway stations are labeled with their names. See the 
<a href="https://mdlutoronto.github.io/qgis-mapping-spatial-analysis-intro/04-labels/" target="_blank">
labeling section</a> of MDL's introductory QGIS tutorial for more information.

<a href='{{ '/assets/images/labeled-map.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/labeled-map.png' | relative_url }}' alt="
QGIS map with labels"
width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

* Optionally, go to <b>Project → Properties → Metadata</b> and set a <b>Title</b>
and <b>Abstract</b> for your map. The web map can be configured to display
this information.

<a href='{{ '/assets/images/project-properties.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/project-properties.png' | relative_url }}' alt="
QGIS map with labels"
width='40%' style="border: 3px solid #888888;" />
</a>

<a href='{{ '/assets/images/metadata.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/metadata.png' | relative_url }}' alt="
QGIS map with labels"
width='70%' style="border: 3px solid #888888;" />
</a>

## Create the web map
* Go to <b>Web → qgis2web → Create web map</b>.

<a href='{{ '/assets/images/create-web-map.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/create-web-map.png' | relative_url }}' alt="
QGIS map with labels"
width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

* On the <b>Layers and Groups</b> tab,
configure the <b>visibility</b> and <b>popup</b> settings for each layer in your map.
In this example, informational fields from the Subway Station layer will be
displayed within a popup when the user clicks a feature.
There are no popups associated with the Subway Line layer - the layer will
be displayed, but it won't respond
to any click events from the user.

<a href='{{ '/assets/images/qgis2web-layer-config.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/qgis2web-layer-config.png' | relative_url }}' alt="
qgis2web layer configuration - popups will be displayed for Subway Station, 
showing the station name and other attributes as inline labels (visible with
data). Subway line is visible but has no popups configured. Basemap is
visible and configured as a basemap."
width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

* Click the <b>Appearance</b> tab. From here, you can configure a variety
of display options. In this example, the project's <b>title</b> and
<b>abstract</b> will be displayed in the upper-right corner of the web map.
A <b>layers list</b> will be visible. The map will be displayed as a smaller
canvas rather than a full-screen display. The extent option has been set to
'<b>Fit to vector layers extent</b>' in order to zoom your viewers in to the area of 
interest.

<a href='{{ '/assets/images/qgis2web-appearance-config.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/qgis2web-appearance-config.png' | relative_url }}' alt="
qgis2web appearance configuration."
width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

* On the <b>Export</b> tab, specify a folder on your computer where the
output files will be saved.

<a href='{{ '/assets/images/qgis2web-export-config.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/qgis2web-export-config.png' | relative_url }}' alt="
qgis2web → Export → Select output folder"
width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

* Click the <b>Update preview</b> button to see what your web map will
look like once deployed. <i>(Note: at the time of writing this tutorial using 
QGIS 3.44 in Windows, the preview was initially not displaying properly. This issue was
resolved by reinstalling PtQtWebEngine using the <a href="
https://trac.osgeo.org/osgeo4w/" target="_blank">OSGeo4W installer</a>.)</i>


<a href='{{ '/assets/images/update-preview.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/update-preview.png' | relative_url }}' alt="
qgis2web → Export → Select output folder"
width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

* Choose whether you'd like the output to use <b>Leaflet</b> or <b>OpenLayers</b>. Leaflet
is used in this example as a more beginner-friendly option.

<a href='{{ '/assets/images/leaflet-or-openlayers.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/leaflet-or-openlayers.png' | relative_url }}' alt="
Choose Leaflet or OpenLayers"
width='60%' style="border: 3px solid #888888;" />
</a>

* When the settings are configured to your liking, click <b>Export</b>.
<a href='{{ '/assets/images/qgis2web-export.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/qgis2web-export.png' | relative_url }}' alt="
Export"
width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

* The HTML, CSS, and JavaScript files needed to create the web map will be saved
to your computer. The project will automatically be opened in a web browser.

<a href='{{ '/assets/images/local-files-in-web-browser.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/local-files-in-web-browser.png' | relative_url }}' alt="
Viewing the local files in a web browser"
width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

## Optional: Further HTML, CSS, and JavaScript customization

* If you'd like to <b>customize your web map further</b>, you
can edit and tweak the output HTML, CSS, and JavaScript files. As an example,
here is the <b>index.html</b> file opened in Microsoft's 
<a href="https://code.visualstudio.com/" target="_blank">Visual Studio Code</a>
editor. (Notepad or any other text editor would also work fine for this.)

<a href='{{ '/assets/images/html-code.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/html-code.png' | relative_url }}' alt="
Viewing index.html in Visual Studio Code"
width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

In this example, let's say we'd like the 'Wheelchair Accessible' or 'Not Wheelchair
Accessible' text in the popup to be <b>centered within the popup and written in
<i>bold italic</i></b>. This change can be made by making a very minor edit
to the HTML.

* To do this, first locate the part of <b>index.html</b> containing
the code that customizes how the popup looks. If you have an understanding of
HTML and JavaScript, this will be very easy to make sense of. But even if you're
unfamiliar with these technologies, you'll notice that the code doesn't look too
different from natural language, and the word '<b>popupContent</b>' on Line 259 will
give you a clue that this is where the popup content is probably found.

<a href='{{ '/assets/images/popup-html-code.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/popup-html-code.png' | relative_url }}' alt="
HTML defining the Leaflet popup"
width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

* The HTML code can be edited directly to change the way this information
is displayed. Some very simple <b>HTML tags</b> (`<b>` for bold, `<i>` for italic,
and `<center>` to center the text) have been added here, on either side of
the logic that displays the wheelchair accessibility info:

<a href='{{ '/assets/images/popup-html-code-edited.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/popup-html-code-edited.png' | relative_url }}' alt="
HTML defining the Leaflet popup"
width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

* <b>Save the .html file</b> and <b>reload the map</b> in your web browser to view the
results:

<a href='{{ '/assets/images/html-edit-results.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/html-edit-results.png' | relative_url }}' alt="
HTML defining the Leaflet popup"
width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

Any further customizations you'd like to make are limited only by your
imagination. If you'd like to learn more about HTML, CSS, and JavaScript, see
the <a href="#resources">Resources section</a> of this tutorial.

## Deploy!

Finally, the output of qgis2web can be <b>uploaded to GitHub</b> and <b>published as a
live webpage</b>.

### Create a GitHub account

If you don't already have a free GitHub account, here's how you can create
one:

* Go to <b><a href="https://www.github.com/" target="_blank">https://www.github.com/
</a></b>. Enter your email and click the <b>Sign up</b>
button.

<a href='{{ '/assets/images/github-signup.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/github-signup.png' | relative_url }}' alt="
github.com signup screen" width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

* Fill in your information and click <b>Create Account</b>.

<a href='{{ '/assets/images/github-create-account.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/github-create-account.png' | relative_url }}' alt="
github.com - specify email, username, password, and region, then click Create Account"
width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

* Once you've verified your account and logged in, you'll be brought to
your GitHub account home page.

<a href='{{ '/assets/images/github-homepage.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/github-homepage.png' | relative_url }}' alt="
GitHub free account homepage"
width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

### Create a repository for your project

* In GitHub, the space where your project files live is called a
<b>repository</b>. Click <b>Create Repository</b> to
start your project.

<a href='{{ '/assets/images/create-repo.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/create-repo.png' | relative_url }}' alt="
GitHub → Create repository"
width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

* For the repository title, input <b>your username</b>, followed by <b>.github.io</b>.
This is the convention used in GitHub when you're using
a repository as the source of a website, rather
than just uploading data. Add a description. Click <b>Create repository</b>.

<a href='{{ '/assets/images/new-repo-details.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/new-repo-details.png' | relative_url }}' alt="
Set repository name and description"
width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

* Click the <b>Uploading an existing file</b> link.

<a href='{{ '/assets/images/upload-existing-file.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/upload-existing-file.png' | relative_url }}' alt="
Upload existing file"
width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

* <b>Select</b> everything in your qgis2web folder. <b>Drag</b> it into the
GitHub page to upload the files.

<a href='{{ '/assets/images/upload-files.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/upload-files.png' | relative_url }}' alt="
Drag the files to your repository page to upload them"
width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

* Scroll to the bottom of the file uploader area and click <b>Commit changes</b>.

<a href='{{ '/assets/images/commit-changes.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/commit-changes.png' | relative_url }}' alt="
Commit changes"
width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

* Once the commit has been made, go back to the main page of your repository.
You may see a note on the right of the page that the <b>deployment</b> is in process or queued.
Typically, the deployment will complete within ten minutes.

<a href='{{ '/assets/images/deployment-status.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/deployment-status.png' | relative_url }}' alt="
Main page of repository - deployment status"
width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

* Once the deployment has completed, navigate to `your-username-here.github.io`.
<b>Your map is now live on the web!</b>
<a href='{{ '/assets/images/deployed-map.png' | relative_url }}' target="_blank">
<img src='{{ '/assets/images/deployed-map.png' | relative_url }}' alt="
Deployed webmap"
width='100%' height='100%' style="border: 3px solid #888888;" />
</a>

## Resources

If you'd like to learn more about the tools and techniques used here, have a
look at the links below.

### QGIS

* <a href="https://mdlutoronto.github.io/qgis-mapping-spatial-analysis-intro/"
target="_blank">Introductory QGIS tutorial</a> by the Map and Data Library

* <a href="https://qgis2web.github.io/qgis2web/">qgis2web 
official documentation</a>

### Learn HTML, CSS, and JavaScript

<b>HTML</b> is the most basic building block of the web, allowing you to define
the structure and layout of your content. <b>CSS</b> gives you more control over
how your HTML looks, and <b>JavaScript</b> allows you to add interactivity and
logic to your creations. <b>The basics of all three are easy to learn</b>, and will
enable you to further customize your digital projects.

* <a href="https://www.w3schools.com/html/" target="_blank">
W3Schools HTML Tutorial</a>

* <a href="https://www.w3schools.com/css/default.asp" target="_blank">
WSchools CSS Tutorial</a>

* <a href="https://www.w3schools.com/js/default.asp" target="_blank">
W3Schools JavaScript Tutorial</a>

### Leaflet

* <a href="https://leafletjs.com/" target="_blank">Official website</a>
containing documentation, tutorials, and plugins.

### GitHub

* <a href="https://github.blog/tag/github-for-beginners/" target="_blank">
GitHub for Beginners</a> blog post series.

### Other helpful links
* <a href="https://login.library.utoronto.ca/index.php?url=https://learning.oreilly.com/home/"
target="_blank">O'Reilly</a>: Access tech how-to ebooks online using your UTORid.
* <a href="https://blogs.tpl.ca/database-guides/2021/07/getting-started-with-lyndacom/"
target="_blank">LinkedIn Learning</a>: Use your public library membership to
access self-guided learning materials for free.
* <a href="https://mdl.library.utoronto.ca/about/contact-form"
target="_blank">Contact the Map and Data Library</a> if you have questions
or would like assistance with anything.