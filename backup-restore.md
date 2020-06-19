---

copyright:
  years: 2019, 2020
lastupdated: "2020-06-19"

subcollection: watson-knowledge-studio-data

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:note: .note}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}


# Backing up and restoring data
{: #backup-restore}

If you need to backup and restore a workspace for {{site.data.keyword.knowledgestudioshort}}, perform these tasks. Also, if you need to perform a manual data migration from one {{site.data.keyword.knowledgestudioshort}} instance to another, perform these tasks.
{: shortdesc}

This topic describes backing up and restoring workspace data, such as type systems and ground truth. For information on backing up and restoring databases, see [Backing up and restoring databases](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-backup-restore-databases).
{: note}

_Manual data migration_ is the process of backing up your data from one instance and restoring it on another instance.

To back up and restore your data complete the following steps:

1. [Understand which data can be backed up](#data)

2. [Prepare for backup](#prepare)

3. [Download artifacts from the current instance](#export)

4. [Recreate workspaces on the new instance](#recreateproj)

5. [Restore the workspace data](#restoredata)

6. [Restore the models](#restoremodels)

7. [Restore any incomplete annotation tasks](#restoretasks)

## Data that can be backed up
{: #data}

The following artifacts can be backed up and migrated manually:

- Editable dictionaries
- Type system
- Approved ground truth document sets

The following types of artifacts cannot be backed up and migrated manually:

- In-progress human annotation documents
- Annotation tasks
- Models and snapshots
- Read-only dictionaries

## Preparing for backup
{: #prepare}

To prepare for backing up and restoring your data, complete the following steps:

1. Complete any work that is in progress in your workspace.

    - > **Important:** Finish any in-progress annotation tasks. Only documents that have been annotated, adjudicated, and approved and promoted to ground truth can be backed up. If you do not finish the annotation work, you will lose any annotation effort that is in progress, but not completely done.

    - If you created annotation tasks to track work that you want to do, but none of the annotation work has begun and will not take place until after the workspace is restored, then make a list of the outstanding annotation tasks. Be sure to note the document sets that you imported, but that have not been added to the ground truth yet. Also, make a note of who you assigned to annotate each document set. You will need to reupload these document sets and recreate the annotation tasks after the workspace is restored.

1. Understand tokenizer use.

    For machine learning models, workspaces use the machine learning-based tokenizer by default. If you are using a dictionary-based tokenizer and have a specific need to continue doing so, you can configure the workspace to use the dictionary-based tokenizer when you restore it. For more information, see [Tokenizers](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-create-project#wks_tokenizer).

1. Manage model resources.

    Your model, its versions, and snapshot data cannot be migrated. The resources (except read-only dictionaries) that you used to train those artifacts can be migrated. Therefore, after the migration, you can recreate the model. The model that will be produced will perform the same as the models you generated prior to the migration because the resources that are used for training will be the same.

    **ATTENTION**: If you have a model that is already deployed and you plan to delete the workspace after you back it up, withdraw the model from deployment. You can rebuild and redeploy the model after you restore the workspace from the backup. For information about undeploying models, see [Undeploying machine learning models](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-publish-ml) and [Undeploying rule-based models](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-wks_rule_publish).

    **Be aware that if you fail to withdraw the model from deployment, the result is an _orphaned_ deployed model. Orphaned deployed models will continue to generate charges on your monthly bills.**

1. Manage read-only dictionary information.

    Read-only dictionaries cannot be migrated. Find out where the read-only dictionary was imported from, so you can reupload it to your workspace after the migration.

1. Make a list of current user roles.

    **NOTE**: This step is optional. It is typically performed when a workspace is migrated across instances and the new workspace must be identical to the original workspace. If you want to migrate only the workspace data into a new workspace, you can skip this step.

    If you are migrating workspaces across different instances, consider making a list of users and their roles for the instance that you are backing up. Someone with the Admin role can print the list from the User Account Management page. After the workspaces are recreated on the new instance, someone with the Admin role must add the users and assign their roles.

    For more information about roles, see [User roles in {{site.data.keyword.knowledgestudioshort}}](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-roles).

1. Make note of workspace information.

    While you still have access to the current instance, for each workspace that you want to migrate, make a note of the following information:
    - Workspace name
    - Workspace description
    - Workspace owner
    - Language
    - If you have any incomplete annotation tasks, because they can't be backed up or migrated, note the human annotators who are assigned to incomplete tasks in the workspace. Also note the annotation task details, such as the task name, due date, and which document sets are assigned to which users.

## Downloading artifacts
{: #export}

For each workspace that you want to migrate, download the following artifacts. Store them in a secure location from which you will be able to upload them into the new instance later.

- Type system
- Dictionaries

  **Note**:
    - Only editable dictionaries will be downloaded. You cannot download read-only dictionaries.
    - For dictionaries, entity type mappings are not migrated. After you restore these artifacts, you will need to map the dictionaries to entity types, as necessary.

- Documents

  See [Uploading resources from another workspace](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-exportimport) for information about how to download these artifacts so that they can be imported into a new workspace.

## Recreating workspaces
{: #recreateproj}

**NOTE**: In this step, the only setting that must match the setting of the original (downloaded) workspace is the language. The rest of the settings can differ from the settings of the original workspace.

Recreate each workspace by copying the following information from the previous instance to the new one:

- Workspace name
- Workspace description
- Language of documents (this setting must match the setting in the original workspace)
- If you previously used a dictionary-based tokenizer in the workspace, and have a valid need to continue using it, you must specify that you want to use the dictionary-based tokenizer instead of the default tokenizer at the time that you create the workspace. For more information about the options, see [Tokenizers](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-create-project#wks_tokenizer).

  To use a dictionary-based tokenizer, expand the Advanced Options section of the Create Workspace window and change the tokenizer setting.

## Restoring workspace data
{: #restoredata}

After recreating the workspaces, upload the previously downloaded artifacts:

1. Upload the type system from the previously created type system backup.
   For details, see [Uploading resources from another workspace](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-exportimport).

  **Note**: You must upload the type system before you can upload any other artifacts that you are moving from the backed up workspace.

1. Upload the dictionaries from the previously created dictionary backup.
   For details, see [Uploading resources from another workspace](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-exportimport).

  If you used any read-only dictionaries in the previous version of the workspace, reupload them into this workspace from their original source.

1. For dictionary pre-annotators, associate the dictionaries with an entity type. Dictionaries that don't have mappings for entity types will not apply annotations when you pre-annotate documents.

1. Upload the documents that you downloaded from the previous version of the workspace into this version of the workspace.
   For details, see [Uploading resources from another workspace](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-exportimport).

## Restoring models
{: #restoremodels}

At this point, all the artifacts that were used to train the model in the previous (backed up) version of the workspace are now available in this new instance.

To redeploy a machine learning model that you deployed in the previous instance, complete the following steps:

1. [Train the machine learning model](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-train-ml).

2. After creating the model, deploy it again. For details, see [Using the machine learning model](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-publish-ml).

To redeploy a rule-based model that you deployed in the previous instance, complete the following steps:

1. [Create the rule-based model](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-wks_rule_train).
1. [Deploy the rule-based model](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-wks_rule_publish).

## Restoring incomplete annotation tasks
{: #restoretasks}

If you had any annotation tasks that were created, but not completed in the previous workspace, complete the following steps to recreate the incomplete annotation tasks:

1. [Upload any documents](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-documents-for-annotation#wks_projadd) that have not been annotated yet, but that you want to add to the ground truth to continue to improve the model.
1. From the newly imported and unannotated documents, [create annotation sets](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-documents-for-annotation).
1. [Recreate the annotation tasks](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-annotate-documents#wks_hatask). Give the task the same name, an appropriate due date, and assign annotation sets to the appropriate human annotators.
