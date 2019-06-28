---

copyright:
  years: 2019
lastupdated: "2019-06-28"

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

# Troubleshooting, support, and FAQs
{: #troubleshooting}

To isolate and resolve problems with your {{site.data.keyword.IBM_notm}} products, you can use the troubleshooting and support information. This information contains instructions for using the problem-determination resources that are provided with your {{site.data.keyword.IBM_notm}} products, including {{site.data.keyword.knowledgestudiofull}}.
{: shortdesc}

## Techniques for troubleshooting problems
{: #ts_overview}

*Troubleshooting* is a systematic approach to solving a problem. The goal of troubleshooting is to determine why something does not work as expected and how to resolve the problem. Certain common techniques can help with the task of troubleshooting.

The first step in the troubleshooting process is to describe the problem completely. Problem descriptions help you and the {{site.data.keyword.IBM_notm}} technical-support representative know where to start to find the cause of the problem. This step includes asking yourself basic questions:

- What are the symptoms of the problem?
- Where does the problem occur?
- When does the problem occur?
- Under which conditions does the problem occur?
- Can the problem be reproduced?

The answers to these questions typically lead to a good description of the problem, which can then lead you to a problem resolution.

### What are the symptoms of the problem?
{: #ts_overview_symptoms}

When starting to describe a problem, the most obvious question is "What is the problem?" This question might seem straightforward; however, you can break it down into several more-focused questions that create a more descriptive picture of the problem. These questions can include:

- Who, or what, is reporting the problem?
- What are the error codes and messages?
- How does the system fail? For example, is it a loop, hang, crash, performance degradation, or incorrect result?

### Where does the problem occur?
{: #ts_overview_where}

Determining where the problem originates is not always easy, but it is one of the most important steps in resolving a problem. Many layers of technology can exist between the reporting and failing components. Networks, disks, and drivers are only a few of the components to consider when you are investigating problems.

The following questions help you to focus on where the problem occurs to isolate the problem layer:

- Is the problem specific to one platform or operating system, or is it common across multiple platforms or operating systems?
- Is the current environment and configuration supported?
- Do all users have the problem?
- (For multi-site installations.) Do all sites have the problem?

If one layer reports the problem, the problem does not necessarily originate in that layer. Part of identifying where a problem originates is understanding the environment in which it exists. Take some time to completely describe the problem environment, including the operating system and version, all corresponding software and versions, and hardware information. Confirm that you are running within an environment that is a supported configuration; many problems can be traced back to incompatible levels of software that are not intended to run together or have not been fully tested together.

### When does the problem occur?
{: #ts_overview_when}

Develop a detailed timeline of events leading up to a failure, especially for those cases that are one-time occurrences. You can most easily develop a timeline by working backward: Start at the time an error was reported (as precisely as possible, even down to the millisecond), and work backward through the available logs and information. Typically, you need to look only as far as the first suspicious event that you find in a diagnostic log.

To develop a detailed timeline of events, answer these questions:

- Does the problem happen only at a certain time of day or night?
- How often does the problem happen?
- What sequence of events leads up to the time that the problem is reported?
- Does the problem happen after an environment change, such as upgrading or installing software or hardware?

Responding to these types of questions can give you a frame of reference in which to investigate the problem.

### Under which conditions does the problem occur?
{: #ts_overview_conditions}

Knowing which systems and applications are running at the time that a problem occurs is an important part of troubleshooting. These questions about your environment can help you to identify the root cause of the problem:

- Does the problem always occur when the same task is being performed?
- Does a certain sequence of events need to happen for the problem to occur?
- Do any other applications fail at the same time?

Answering these types of questions can help you explain the environment in which the problem occurs and correlate any dependencies. Remember that just because multiple problems might have occurred around the same time, the problems are not necessarily related.

### Can the problem be reproduced?
{: #ts_overview_reproduce}

From a troubleshooting standpoint, the ideal problem is one that can be reproduced. Typically, when a problem can be reproduced you have a larger set of tools or procedures at your disposal to help you investigate. Consequently, problems that you can reproduce are often easier to debug and solve.

However, problems that you can reproduce can have a disadvantage: If the problem is of significant business impact, you do not want it to recur. If possible, re-create the problem in a test or development environment, which typically offers you more flexibility and control during your investigation.

- Can the problem be re-created on a test system?
- Are multiple users or applications encountering the same type of problem?
- Can the problem be re-created by running a single command, a set of commands, or a particular application?


## Cannot access the application
{: #wks_ts_access}

Find out how to grant users access to {{site.data.keyword.knowledgestudioshort}}, and address common access issues.

### Administrator
{: #wks_ts_access_administrator}

Each {{site.data.keyword.knowledgestudioshort}} instance has an administrator role associated with it. The person who originally signs up to use the application is given the administrator role automatically. The administrator can invite other people.

For information about how to invite people to use your instance of the application, see [Assembling the team](/docs/services/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-team).

### Human annotator
{: #wks_ts_access_annotator}

If you have been invited to someone's instance of {{site.data.keyword.knowledgestudioshort}} to serve as a human annotator, you likely received an email invitation. First, you must register with {{site.data.keyword.IBM_notm}} if you do not have {{site.data.keyword.IBM_notm}} registration credentials already. Once you register with {{site.data.keyword.IBM_notm}} and accept the invitation, you are given access to the instance. However, after you are given access and before you can start to annotate documents, the administrator or a project manager of the instance must add you to a workspace and assign an annotation task to you. It is not until after you have been assigned a task that you can perform any actions in the {{site.data.keyword.knowledgestudioshort}} instance. To annotate documents, use the ground truth editor. Use a Google Chrome browser for the best performance.

For help using the ground truth editor, see [Annotating documents](/docs/services/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-user-guide).

## Experimental services and features: What does *experimental* mean?
{: #experimental}

{{site.data.keyword.IBM_notm}} releases experimental services and features for you to try out. These services might be unstable, change frequently in ways that are not compatible with earlier versions, and might be discontinued with short notice. These services and features are not recommended for use in production environments.

For more information about experimental services, see the [{{site.data.keyword.cloud_notm}} documentation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/docs/get-support/servicessupport.html#s-services-exporcont){: new_window}. For the full details of experimental services, see the latest version of the [{{site.data.keyword.cloud_notm}} Service Description ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/software/sla/sladb.nsf/sla/bm?OpenDocument){: new_window}.

## Storage space issues
{: #storage}

### Symptoms
{: #storage_symptoms}

You might see a message about having exceeded the allowed storage space when you attempt to perform one of these tasks:

- Upload documents or dictionaries
- Deploy a model or version a model
- Run a pre-annotator on documents

### Causes
{: #storage_causes}

The storage limit has been met or would be exceeded if the action were to proceed.

### Resolving the problem
{: #storage_resolve}

The largest consumers of storage space are machine learning and rule-based models. To free up space, you can take the following actions:

- Delete snapshot versions of any models that you do not expect to need to revert to.
- Delete any models that you do not need.
- If your models are too important to delete, consider increasing the amount of storage in your deployment.

## Contacting IBM Support
{: #ts_contactingibmsupport}

{{site.data.keyword.IBM_notm}} Support provides assistance with product defects, answers FAQs, and helps users resolve problems with the product.

The developer communities are open to everyone and are a great place to start. For links, see the "Developer community" section at the bottom of the table of contents.

**To contact {{site.data.keyword.IBM_notm}} Support:**

You must be authorized to create support cases on the {{site.data.keyword.cloud_notm}} Service Portal.

1. Define the problem, gather background information, and determine the severity of the problem.
2. Gather diagnostic information, if possible.
3. Create a case on the [{{site.data.keyword.cloud_notm}} Service Portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://watson.service-now.com/wcp){: new_window}.
