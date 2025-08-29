# Pathogens Portal Node toolbox

This toolbox contains minimal code for a Pathogens Portal Node (PPN). It was created as part of the [Pathogen Data Network (PDN)](https://pathogendatanetwork.org), funded by NIH (award number U24AI183840).

The toolbox uses a [theme](https://github.com/ScilifelabDataCentre/node-pathogens-portal-theme) inspired by the [Swedish](https://www.pathogens.se/) and [Swiss Pathogens Portal](https://pathogensportal.ch/), and applies the visual identity outlined by the [Central Pathogens Portal](https://www.pathogensportal.org/).

More information about PPNs and the Pathogen Data Network (PDN) can be found in the [onboarding material](static/docs/Onboarding_Introduction.pdf).

Information about plans for the year 2025/2026 can be found in our Roadmap (see below).

## Cite this repository

<a href="https://doi.org/10.5281/zenodo.15695579"><img src="https://zenodo.org/badge/919472818.svg" alt="DOI"></a>

Click on 'Cite this repository' near the top right of this repository to see how to formally cite this repository.

The software can alternatively be referenced using the Research Resource Identifier (RRID), as follows: Pathogens Portal Node Toolbox (RRID:SCR_027086).

## Roadmap

To understand upcoming work, view our [roadmap for 2025/6](https://docs.google.com/document/d/1K1vG6zdTM69xpNGdTC3FObPZ2WehXYc6y3F4j1-cfeQ/edit?tab=t.0#heading=h.tza3nqjp30d8).

## Content

- [Requirements](#requirements)
- [Setup](#setup)
- [Configuration](#configuration)
  - [Must updated params](#must-updated-params)
  - [Multi language site](#multi-language-site)
- [Customisation](#customisation)
  - [Dashboards](#dashboards)
  - [Highlights](#highlights)
  - [Topics](#topics)
  - [Publications](#publications)
  - [News](#news)
  - [Events](#events)
  - [How to add New content](#how-to-add-new-content)
  - [How to remove default content](#how-to-remove-default-content)
    - [Disabled temporarily](#disabled-temporarily)
    - [Delete permenantly](#delete-permenantly)
- [Themes](#themes)
  - [Layout](#layout)
  - [Update theme](#update-theme)
- [Analytics](#analytics)
- [Hosting](#hosting)
- [Credits](#credits)

## Requirements

- `Hugo v0.139` or higher (see [here](https://gohugo.io/installation/) for Hugo installation)

## Setup

The following steps are for a quick setup/starting guide, `Hugo` should have been installed (see requirements above) in your computer before following the below mentioned steps.

1. Fork this repository to your own GitHub organisation. You can change the name of the repository whilst forking, if you wish to. More information on how to do that can be found [here](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo), and in the [demo video](https://youtu.be/v53tevQV-7I).

2. Clone the forked repository to your computer using the following command in the terminal ([demo video](https://youtu.be/671ij1kB2EU))

   ```
   git clone --recursive <your fork url>
   ```

   The `<your fork url>` mentioned above is the github url of your fork. It can be found as mentioned [here](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo#cloning-your-forked-repository).

   **Note** the `--recursive` mentioned in the command is **important to include** in the command.

3. Switch to the appropriate repository

   ```
   cd <repository name>
   ```

4. Start `hugo` and see if works as expected ([demo video](https://youtu.be/L4cLXx90dJI))

   ```
   hugo serve
   ```

   If everything is good, you should see output similar to that below:

   ```
   Start building sites …
   hugo v0.139.3+extended+withdeploy darwin/amd64 BuildDate=2024-11-29T15:36:56Z VendorInfo=brew
   ........
   ........
   Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
   Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
   Press Ctrl+C to stop
   ```

5. Open a browser, and type the URL `http://localhost:1313/`. You will see the the minimum example Pathogens Portal Node (PPN) with example content.

## Configuration

By default, `hugo` looks for the config file named `hugo.yaml` in the root directoy. You can configure the site by editing the config file according to your needs. Some useful config options are mentioned below, or you could read [Hugo documentation related to configuration](https://gohugo.io/getting-started/configuration/)

### Must updated params

Site wide variables can be added as custom parameters. The following parameters **should be added/updated** in the `hugo.yaml`. If the below mentioned variables already have a _(dummy)_ value set, overwrite it with desired value.

#### Node info

Information related to your node (i.e. node info) is set using the following variables in the `params` section. These should be set the show your organisaton/group logo beside the pathogens node logo at the top of the website.

```yaml
node_logo: ""
node_url: ""
node_country: ""
```

#### Social media info

Social media accounts related to the node can be highlighted if the following variables are set in the `params` section.

```yaml
social_media:
  show_in_footer: true
  twitter_url: ""
  linkedin_url: ""
  contact_email: ""
```

When `show_in_footer` is set to `true`, it will add a section `Connect` in the footer, with the links to node's social media.

### Multi language site

Hugo supports multilingual websites, so more than one language can be set for a pathogens portal node. Read the `hugo` documentation on [language configuration](https://gohugo.io/content-management/multilingual/#configure-languages) and [multi-language content](https://gohugo.io/content-management/multilingual/) for more.

## Customisation

This section covers how to add and modify your content. All the content should be placed in the `content` folder. Initially, the following types of content are included.

**NOTE:** The existing content comprises sample files, intended only for demonstration. This sample files should be removed and/or replaced with your own desired content.

### Dashboards

Dashboards are displayed on the main page as cards. The dashboard can be either:

- **Internal** - the content and the visualisation are written by you: [see an example](https://raw.githubusercontent.com/ScilifelabDataCentre/node-pathogens-portal/refs/heads/main/content/dashboards/internal_dash.md))
- **External** - the content file only has front matter with a `redirect_url` ([example](https://raw.githubusercontent.com/ScilifelabDataCentre/node-pathogens-portal/refs/heads/main/content/dashboards/external_dash.md))

To add a new dashboard, run the following command from the root of the GitHub repository on your computer. The `<desired file name>` in the command is the new file you want (but without spaces).

```
hugo new content dashboards/<desired file name>.md
```

The above command will create a new file in the `content/dashboards` directory. Fill in the frontend matter (i.e. the variables at the top of the file and between the two `---`) with appropriate values, and start writing your content.

### Highlights

Data highlights are lay summaries of relevant research completed by members of the national research community. In Sweden, the policy has been only to highlight research that shares data and/or code as openly and FAIRly as possible. To add a new highlight, run the following command from the root of the GitHub repository on your computer. The `<desired file name>` in the command is the new file you want (but without spaces).

```
hugo new content highlights/<desired file name>.md
```

The above command will create a new file in the `content/highlights` directory. Fill in the front end matter (i.e. the variables at the top of the file and between the two `---`) with appropriate values, and start writing your content.

### Topics

Topics are a refined list of categories that you could use to group your content for a faster overview. For example, adding a topic about 'influenza' would enable you to group all of the content related to influenza, and your users can see just content related to influenza. To add a topic, run the following command from the repository's root. The `<desired file name>` in the command is the new file you want (but without spaces).

```
hugo new content topics/<desired file name>.md
```

The above command will create a new file in the `content/topics` directory. Fill in the front end matter (i.e. the variables at the top of the file and between the two `---`) with appropriate value, and start writing your content.

**Note:** In order to include a dashboard or highlight under a specific topic, you must list that topic in the front matter of the corresponding content.

### Publications

The publications page included in the PPN theme uses the `Europe PMC API` to fetch and display relevant publications. In particular, it shows 10 recent publications for each of the pathogens given in `query_list`. The publications will all involve a researcher affiliated with a specified nation, which should be specified under `country`.

The configurations related to this page should be set in the `params.publications` section of the `hugo.yaml` config file. See below for an example:

```yaml
params:
   publications:
      country: "Sweden"
      # It is important to use "" (double quotes) within the query string
      query_list:
         covid-19: 'ABSTRACT:("sars-cov-2" OR "covid-19")'
         influenza: 'ABSTRACT:"influenza"'
      # Optional setting
      category_display: "list"
```

`country` - Should be set as the relevant nation for the node. Here, the country is set to 'Sweden', so publications including researchers affiliated with Swedish institutions will be shown.

`query_list` - List of _keyword_ and _query string_ to define the pathogens that publications should related to, and what search should be used to identify relevant publications. The _keyword_ is used for category (navigation) in the rendered page. This means that it will be what shows in the filter on the page in the PPN. The _query string_ is used by the _Europe PMC API_ to search publications for relevant keywords. For example, here,  the abstracts of papers are searched for the terms 'SARS-CoV-2' OR 'COVID-19' to identify papers related to COVID-19.  Any pathogen can be listed here, at the users discretion.

**NOTE:** When setting the query string for a keyword, it should be enclosed within `''` (single quotes), because the query string itself should contain `""` (double quotes) for word matching. To get deep understanding of the query syntax and build efficient query, see the Europe PMC [documentation](https://europepmc.org/help).

`category_display` - An optional setting to define how the category links (i.e. the list of pathogens) are displayed in the rendered page. If this parameter is set to _"dropdown"_, the categories are displayed as a dropdown menu. If the parameter is set to anything else or if the parameter is not included in the config file, the category links are displayed as a list of links on the side.

### News

News articles are updates regarding the portal, and perhaps other relevant information/news from the area in which the node is based. For example, the Swedish node also posts news about outbreaks in Sweden. To add a news article, run the following command from root of the repository on your computer. The `<desired file name>` in the command is the new file you want (but without spaces).

```
hugo new content news/<desired file name>.md
```

The above command will create a new file in the `content/news` directory. Fill in the front end matter (i.e. the variables at the top of the file and between the two `---`) with appropriate values, and start writing your content.

### Events

The events page consists of a list of upcoming events, including training. To add a new event, copy the following fields (including the `{}` brackets), and paste at the top (after the opening bracket `[`) of the `data/events.json` file. Then fill in the neccessary information for the event.

```json
{
    "title": "",
    "type": "",
    "date_start": "",
    "time_start": "",
    "date_end": "",
    "time_end": "",
    "venue": "",
    "organisers": "",
    "event_url": "",
    "description": ""
},
```

**Tip:** As time progresses, the data file might get very large if no expired events are removed. It may therefore be better to remove expired events from time to time, or when you add a new event.

### How to add New content

You can add new content to the node by creating a file (for single pages, e.g. an about page, or contact page) or folder (for a section that contains multiple similar types of pages, e.g. dashboards, news).

#### Single page

You can create a single page by directly creating a file under the `content` directory. For example, creating `content/services.md` will create a new page and can be accesed via the URL `https://yourwebsite.com/services/`

If you want to add the new page to menu of your site i.e. the navigation bar at the top of the website, you have two options:

1. To add in the top menu (i.e. the same level as the About and Contact pages), add `navbar_top` to the `menu` in the front matter of the file as follows:

   ```yaml
   ---
   title: Anytitle
   menu:
     navbar_top:
       name: <name>
       identifier: <identifier>
   ---

   ```

   Replace `<name>` and `<identifier>` with desired values. This will create an entry in the top navigation bar.

2. To add in the main menu (i.e. the same level as the Dashboards and Topics sections), add `navbar_main` to the `menu` in the front matter of the file as follows:

   ```yaml
   ---
   title: Anytitle
   menu:
     navbar_main:
       name: <name>
       identifier: <identifier>
   ---

   ```

   Replace `<name>` and `<identifier>` with desired values. This will create an entry in the main navigation bar.

#### Sections

You can create a section by creating a folder (and index file within it). Adding `content/services/_index.md`, will create a folder called `services`, that has an index file inside. This will create a `services` section on the site. The index file will be the landing page of this section. You can then create pages within that section by adding new files within the folder. For example, creating `content/services/sequencing.md` will create a single page `sequencing` within the section `services`. To add new section and its pages into the main menu as a dropdown set of options, we would do the following:

1. Add the section's index file to the main menu. Expanding on the above `services` example, you should add the following to the `content/services/_index.md` file:

   ```yaml
   ---
   title: Anytitle
   menu:
     navbar_main:
       name: Services
       identifier: services
       params:
         type: dropdown
         include_parent: true
   ---

   ```

   **Note:** Adding `type: dropdown` in the params will ensure the section shows as a dropdown set of options in the main menu. The `include_parent: true` code will also ensure that `content/services/_index.md` (i.e. the landing page of the section) is included in the dropdown menu. You can leave out this line entirely is this is not something that you want to include.

2. In order to add the individual pages of the section to the dropdown section, you need to add some information to the font matter. Taking the above example of having a sequencing page within the services section, you'd bee to add the following to `content/services/sequencing.md`

   ```yaml
   ---
   title: Anytitle
   menu:
     services:
       name: Sequencing
       identifier: sequencing
   ---

   ```

   **Note:** Here, `services` is used instead of `navbar_main` as the `menu` key. In all cases, you should use the `identifier` used for the section index file (see step 1) as the key.


### How to remove default content

Not all of the sections/pages provided in the PPN Toolbox will be relevant for all PPNs. Irrelevant/unwanted sections/pages can either be disabled temporarily or permanently removed by following the instructions below.

#### Disabled temporarily

If you do not want to display a page/section, but think that you might want to display it later, then you can temporarily disable it. Temporarily disabling the page/section will ensure that the relevant files/code will remain in your repository, making them easy to activate later. In order to temporarily disable a page/section, list it under `ignoreFiles` in the config settings.

-  For example, to disable the `highlights` section:

```yaml
ignoreFiles:
   - highlights
```

- To disable the 'demo highlight 2' page within the highlight section:
```yaml
ignoreFiles:
   - demo2_highlight.md
```

- To disable multiple sections (`news` and `events`) and pages (demo highlight 2):
```yaml
ignoreFiles:
   - news
   - events
   - demo2_highlight.md
```

#### Delete permanently

To remove a section/page permanently, the respective folder or file can be deleted from the repository.

## Themes

This repository uses the [pathogens portal node theme](https://github.com/ScilifelabDataCentre/node-pathogens-portal-theme). It defines the layout and design for displaying content on the website.

### Layout

#### New layout

If you want to create a new layout, create a `layouts` directory and start filling it with your own layouts for each section/page. For example, let's imagine there is a content section called _articles_. To create your own layout for that section, you need to create a directory `layouts/articles`. In that directory, you can have two files:

- `list.html` - this file would determine how the `content/articles/_index.md` file is displayed
- `single.html` - this file would determine how the `content/articles/<individual file name>.md` files are displayed

In order to read more about options with `hugo` layouts, please see the [Hugo documentation](https://gohugo.io/templates/)

#### Edit default

If you want to edit a layout that is included in the PPN theme, you can copy the respective folders from the theme layout in to the project's layout. For example, if you want to change the _dashboards_ layout included in the PPN theme:

1. Open a terminal and go into the repository root

   ```
   cd <path to repository>
   ```

2. Copy the desired layout from themes (_dashboard_ for example)

   ```
   cp -r themes/node-pathogens-portal-theme/layouts/dashboards layouts/
   ```

**NOTE:** You can create your own _dashboards_ layout using the _"new layout"_ approach mentioned above. However, copying the layout from PPN theme will save a lot of time if major changes are needed. **Please avoid directly modifying the files in themes directory**.

### Update theme

The [pathogens portal node theme](https://github.com/ScilifelabDataCentre/node-pathogens-portal-theme) might be updated from time to time. If you would like to pull the latest changes for your own site, follow the steps below.

1. Open a terminal and go into the repository root

   ```
   cd <path to repository>
   ```

2. Run the submodule update command, this will pull all latest changes in the theme

   ```
   git submodule update --remote
   ```

3. Add this change so that the lastest commit of the theme is linked to this repository

   ```
   git add themes/node-pathogens-portal-theme
   ```

4. Commit the change and push to remote as usual

   ```
   git commit -m "Updated the theme"
   git push origin <branch name>
   ```

   **Note:** Above steps have two commands and `<branch name>` will be the name of the branch that you are working on.

## Analytics

It can be useful to collect metrics for a website (like the number of visits across the site and for each page). There are several tools (e.g. [Google Analytics](https://developers.google.com/analytics/devguides/collection/ga4), [Motomo](https://matomo.org/), [Mixpanel](https://mixpanel.com/)) that can be used for this, some of which are free, whilst others come at a financial cost. You should consider where the data is held, as this can have privacy implications for your users. This is important for populating any page on a privacy policy.

## Hosting

Hosting means getting the content on to the internet. There are many ways in which this can be done. Contact your university/group IT team to understand the best options for you.

## Credits

This project is supported by the National Institute Of Allergy And Infectious Diseases of the National Institutes of Health (NIH) (Award Number: U24AI183840). The content is solely the responsibility of the authors, and does not necessarily represent the official views of the National Institutes of Health (NIH).

This software is developed by [Scilifelab Data Centre](https://www.scilifelab.se/data/) as part of [PDN project](https://pathogendatanetwork.org/). It is based on the [Central Pathogens Portal](https://www.pathogensportal.org/), [Swedish Pathogens Portal](https://www.pathogens.se/) and [Swiss Pathogens Portal](https://pathogensportal.ch/).

We thank [Swiss Institute of Bioinformatics](https://www.sib.swiss/), [EMBL-EBI](https://www.ebi.ac.uk/) and all collaborators.
