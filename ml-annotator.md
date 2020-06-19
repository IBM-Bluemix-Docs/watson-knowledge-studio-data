---

copyright:
  years: 2019, 2020
lastupdated: "2020-06-19"

subcollection: watson-knowledge-studio-data

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


# Machine learning model creation workflow
{: #ml_annotator}

Create a machine learning model that trains a model you can use to identify entities, coreferences, and relationships of interest in new documents.
{: shortdesc}

Understand the typical workflow for creating a machine learning model in {{site.data.keyword.knowledgestudioshort}} for {{site.data.keyword.icp4dfull_notm}}.

All the steps are performed by the project manager, except for the *Annotate documents* step, which is performed by the human annotator. Because human annotators are often subject matter experts, they might be consulted during the creation of workspace resources, such as the type system, also.

![The workflow for developing a machine learning model](images/wks-checklist.svg "Shows the key steps you must perform to create a model") Figure 1. The workflow for developing a machine learning model

<table summary="Creating and refining a model">
  <caption>Table 1. Creating and refining a workflow</caption>
  <tr>
    <th style="vertical-align:bottom; text-align:left" id="d14771e70">Step</th>
    <th style="vertical-align:bottom; text-align:left" id="d14771e72">Description</th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d14771e70">
      <p>Create a workspace.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d14771e72">
      <p>See [Creating a workspace](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-create-project). A workspace contains the resources that are used to create the model, including:</p>
      <dl>
        <dt>Type system</dt>
        <dd>
          <p>Upload or create the type system, and define the entity types and relation types that human annotators can apply when annotating text. The model process manager typically works with subject matter experts for your domain to define the type system. See [Establishing a type system](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-typesystem)</p>
        </dd>
        <dt>Source documents</dt>
        <dd>
          <p>Create a corpus by uploading sample documents that are representative of your domain content into the workspace. See [Adding documents for annotation](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-documents-for-annotation). Partition the corpus into document sets, specify the percentage of documents that are shared among all document sets, and assign the document sets to human annotators.</p>
        </dd>
        <dt>Dictionaries</dt>
        <dd>
          <p>Upload or create dictionaries for annotating text. You can choose to manually add dictionary entries or upload entries from a file, and then edit the entries. See [Creating dictionaries](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-dictionaries).</p>
        </dd>
      </dl>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d14771e70">
      <p><strong>Optional</strong>: Pre-annotate documents</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d14771e72">
      <p>Pre-annotate documents according to the terms in the workspace dictionaries or based on rules that you define. See [Bootstrapping annotation](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-preannotation).</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d14771e70">
      <p>Annotate documents</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d14771e72">
      <ol>
        <li>
          <p>Admins and project managers can annotate documents directly, without needing to create annotation tasks or go through the adjudication process. See [Annotating document sets directly](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-annotating-document-sets-directly).</p>
        </li>
        <li>
          <p>The project manager generally assigns annotation tasks to human annotators, configures the inter-annotator agreement threshold, and provides annotation guidelines for the human annotators to follow. See [Creating an annotation task](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-annotate-documents#wks_hatask).</p>
        </li>
        <li>
          <p>Human annotators use the ground truth editor to manually annotate documents. A human annotator identifies mentions of interest in your domain content and labels them with entity types. The human annotator also identifies relationships between mentions (for example, Mary is an employee of IBM) and how the mentions co-reference the same entity (such as an occurrence of "she" that refers to Mary). Refer to [Annotating documents](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-user-guide).</p>
        </li>
      </ol>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d14771e70">
      <p>Adjudicate and promote documents</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d14771e72">
      <p>Accept or reject the ground truth that was generated by human annotators, and adjudicate any annotation differences to resolve conflicts. Evaluating the accuracy and consistency of the human annotation effort might be the responsibility of a senior human annotator or a user with stronger subject matter experience than the project manager. See [Adjudication](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-build-groundtruth#wks_haperform).</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d14771e70">
      <p>Train the model</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d14771e72">
      <p>Create the machine learning model. See [Creating a machine learning model](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-train-ml#wks_madocsets).</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d14771e70">
      <p>Evaluate the model.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d14771e72">
      <p>Evaluate the accuracy of the model. See [Evaluating annotations added by the model](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-train-ml#wks_matest). Depending on model accuracy, this step might result in the need to repeat earlier steps again and again until optimal accuracy is achieved. See [Analyzing machine learning model performance](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-evaluate-ml) for ideas about what to update based on common performance issues.</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d14771e70">
      <p>Publish the model.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d14771e72">
      <p>Export the model. See [Using the machine learning model](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-publish-ml).</p>
    </td>
  </tr>
</table>
