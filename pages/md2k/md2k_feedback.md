---
title: Feedback
keywords: documentation theme, jekyll, technical writers, help authoring tools, hat replacements
tags: [getting_started]
summary: "TODO"
sidebar: md2k_sidebar
permalink: feedback.html
folder: md2k
---

<script type="text/javascript" src="https://md2korg.atlassian.net/s/463656ebdf0010e63f7a8c72a675b214-T/sli67f/72002/b6b48b2829824b869586ac216d119363/2.0.14/_/download/batch/com.atlassian.jira.collector.plugin.jira-issue-collector-plugin:issuecollector/com.atlassian.jira.collector.plugin.jira-issue-collector-plugin:issuecollector.js?locale=en-US&collectorId=c845e9c4"></script>
<script type="text/javascript" src="https://md2korg.atlassian.net/s/463656ebdf0010e63f7a8c72a675b214-T/sli67f/72002/b6b48b2829824b869586ac216d119363/2.0.14/_/download/batch/com.atlassian.jira.collector.plugin.jira-issue-collector-plugin:issuecollector/com.atlassian.jira.collector.plugin.jira-issue-collector-plugin:issuecollector.js?locale=en-US&collectorId=53de3368"></script>
<script type="text/javascript" src="https://md2korg.atlassian.net/s/463656ebdf0010e63f7a8c72a675b214-T/sli67f/72002/b6b48b2829824b869586ac216d119363/2.0.14/_/download/batch/com.atlassian.jira.collector.plugin.jira-issue-collector-plugin:issuecollector/com.atlassian.jira.collector.plugin.jira-issue-collector-plugin:issuecollector.js?locale=en-US&collectorId=b5074839"></script>

# Feedback

## Current bugs and feature suggestions
<a href="https://md2korg.atlassian.net/issues/?filter=-4">JIRA Issue Tracker</a>


## Feedback
<a id="feedback-button">Provide feedback or suggestions</a>


## Bug Reporting

### mCerebrum
<a id="mc-bug-button">Submit bug report</a>

### Cerebral Cortex
<a id="cc-bug-button">Submit bug report</a>


<script type="text/javascript">
window.ATL_JQ_PAGE_PROPS =  $.extend(window.ATL_JQ_PAGE_PROPS, {
  'c845e9c4' : {
    "triggerFunction": function(showCollectorDialog) {
      //Requires that jQuery is available!
      jQuery("#mc-bug-button").click(function(e) {
        e.preventDefault();
        showCollectorDialog();
      });
    },
    // ==== we add the code below to set the field values ====
    fieldValues: {
      description : 'Submitter Name: \n\nEmail: \n\nDetails: \n\n\nExpected result: \n\n\nActual result: \n\n\nSteps to reproduce: \n\n\nAdditional information: \n\n',
      environment : 'Android version: \nApplication name: \nApplication version: '
    }
  },
  '53de3368' : {
    "triggerFunction": function(showCollectorDialog) {
      //Requires that jQuery is available!
      jQuery("#cc-bug-button").click(function(e) {
        e.preventDefault();
        showCollectorDialog();
      });
    },
    // ==== we add the code below to set the field values ====
    fieldValues: {
      description : 'Submitter Name: \n\nEmail: \n\nDetails: \n\n\nExpected result: \n\n\nActual result: \n\n\nSteps to reproduce: \n\n\nAdditional information: \n\n'
    }
  },
  'b5074839' : {
    "triggerFunction": function(showCollectorDialog) {
      //Requires that jQuery is available!
      jQuery("#feedback-button").click(function(e) {
        e.preventDefault();
        showCollectorDialog();
      });
    }
  },
});
</script>

<!-- Required Footer for all pages -->
<!-- {% include links.html %} -->
