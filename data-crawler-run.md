---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-18"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Crawling your data repository

After the crawler options have all been properly configured, you can run a crawl against your data repository.
{: shortdesc}

Never run the crawler as `root`, unless you need access to files only `root` can read.
{: tip}

Run the following command: `crawler`

The crawler prompts you with documentation that explains what to do. You can run a test crawl, or run a crawl, in addition to other crawl options.

## Running a test crawl

Run the following command: `crawler testit`

This runs a test crawl, which crawls only the seed URL and displays any enqueued URLs. If the seed URL results in indexable content (for example, it is a document), then that content is sent to the output adapter, and the content is printed to the screen. If the seed URL retrieval causes URLs to be enqueued, those URLs will be displayed, and no content will be sent to the output adapter. By default, five enqueued URLs are displayed.

You can also specify a custom configuration file as an option for the crawl command, for example: `crawler testit --config [config/myconfigfile.conf]`

The path to the configuration file passed in the `--config` option must be a qualified path. That is, it must be in relative formats, such as `config/myconfigfile.conf` or `./myconfigfile.conf`, or in an absolute path such as `/path/to/config/myconfigfile.conf`.

Additionally, you can set the limit for the number of enqueued URLs that are displayed as an option for the testit command, for example: `crawler testit --limit [number]`

## Running a crawl

Run the following command: `crawler crawl`

This runs a crawl with the default configuration file (`crawler.conf`).

You can also specify a custom configuration file as an option for the crawl command, for example: `crawler crawl --config [config/myconfigfile.conf]`

The path to the configuration file passed in the `--config` option must be a qualified path. That is, it must be in relative formats, such as `config/myconfigfile.conf` or `./myconfigfile.conf`, or in an absolute path such as `/path/to/config/myconfigfile.conf`.

## Restarting a crawl

Run the following command: `crawler restart`

This command runs a restart crawl by starting a new crawl with the default configuration file (`crawler.conf`).

You can also specify a custom configuration file as an option for the restart command, for example: `crawler restart --config [config/myconfigfile.conf]`

The path to the configuration file passed in the `--config` option must be a qualified path. That is, it must be in relative formats, such as `config/myconfigfile.conf` or `./myconfigfile.conf`, or in an absolute path such as `/path/to/config/myconfigfile.conf`.

## Resuming a crawl

Run the following command: `crawler resume`

This command resumes a crawl from where it stopped with the default configuration file (`crawler.conf`).

You can also specify a custom configuration file as an option for the resume command, for example: `crawler resume --config [config/myconfigfile.conf]`

The path to the configuration file passed in the `--config` option must be a qualified path. That is, it must be in relative formats, such as `config/myconfigfile.conf` or `./myconfigfile.conf`, or in an absolute path such as `/path/to/config/myconfigfile.conf`.

## Refreshing a crawl

Run the following command: `crawler refresh`

The command refreshes a previous crawl with the default configuration file (`crawler.conf`).

You can also specify a custom configuration file as an option for the refresh command, for example: `crawler refresh --config [config/myconfigfile.conf]`

The path to the configuration file passed in the `--config` option must be a qualified path. That is, it must be in relative formats, such as `config/myconfigfile.conf` or `./myconfigfile.conf`, or in an absolute path such as `/path/to/config/myconfigfile.conf`.
