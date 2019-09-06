---

copyright:
  years: 2015, 2019
lastupdated: "2019-08-30"

subcollection: watson-knowledge-studio

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

# Annotating document sets directly
{: #annotating-document-sets-directly}

Admins and project managers are able to annotate ground truth document sets directly without creating annotation tasks.
{: shortdesc}

## Procedure
{: #annotating-document-sets-procedure}

Annotations that you apply directly to document sets are not applied to active annotation tasks. To avoid unintended overwrites, do not annotate document sets that are involved in active annotation tasks.
{: note}

1. [Launch the {{site.data.keyword.knowledgestudioshort}} application](/docs/services/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-wks_tutintro#launching-the-knowledge-studio-application).
2. [Add documents to your workspace.](/docs/services/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-documents-for-annotation#wks_projadd)
3. From your workspace menu, click **Machine Learning Model**, then click **Annotations.**
4. Click the **Ground Truth** tab.
5. Click **Annotate** next to the document set that you want to use.
6. Annotate your documents. See [Annotating documents](/docs/services/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-user-guide) for more details.
7. Click **Save** to update the document set with your annotations.

## What to do next
{: #annotating-document-sets-next}

- [Train a machine learning model](/docs/services/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-train-ml).
