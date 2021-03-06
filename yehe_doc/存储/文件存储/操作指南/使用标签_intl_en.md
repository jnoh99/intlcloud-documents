## Overview

A [tag](https://intl.cloud.tencent.com/document/product/651) provided by Tencent Cloud to identify cloud resources is a key-value pair (Key-Value). Tags can help you easily classify and manage cloud resources from various dimensions (such as business, purpose, owner, etc.) It should be noted that Tencent Cloud will not use the tags you set for any other purpose than your management of Tencent Cloud resources. This document will help you understand how to edit tags on file storage resources.

## Use Limits

Note the following limits when editing tags:

- **Quantity**: each file system allows up to 50 tags.
- **Tag key**:
  - Do not create tag keys prefixed with `qcloud`, `tencent`, and `project`, because they are reserved for the system.
  - A tag key can only contain `numbers`, `letters`, and `+=.@-`. It cannot exceed 255 characters in length.
- **Tag value**: a tag value can only contain `empty strings or numbers`, `letters`, and `+=.@-`. It cannot exceed 127 characters in length.

## Directions and Cases

### Case description

Case: a company has purchased 6 file systems, of which the operating departments, business scopes, and owners are as follows:

| File System ID  | Operating Department | Scope of Business | Owner |
| ----------- | -------- | -------- | ------ |
| cfs-abcdef1 | E-commerce | Marketing campaigns | John Smith |
| cfs-abcdef2  | E-commerce | Marketing campaigns | Chris   |
| cfs-abcdef3 | Games | Game A | Jane Smith |
| cfs-abcdef4 | Games | Game B | Ada |
| cfs-abcdef5  | Entertainment | Post-production | Chris       |
| cfs-abcdef6 | Entertainment | Post-production | John Smith |

Taking cfs-abcdef1 as an example, we can add the following 3 sets of tags to the file system:

<table id="table02">
	<tr><th>Tag Key</th><th>Tag Value</th></tr>
	<tr><td>dept</td><td>ecommerce</td></tr>
	<tr><td>business</td><td>mkt</td></tr>
	<tr><td>owner</td><td>John Smith</td></tr>
</table>



Similarly, you can add tag key-value pairs to other file systems based on the different settings of operating departments, business scopes, and owners.




## Directions


### Tagging a new file system

#### Prerequisites
Make sure you have owned a tag that you can use before creating a file system. In case of no tags available, go to the [Tag Console](https://console.cloud.tencent.com/tag/taglist) and create one.

1. Log in to the [CFS Console](https://console.cloud.tencent.com/cfs).
2. In the File System List page, click **Create**.
3. In the “Create File System” pop-up window, find **Tag** down below, and click **Add** to add a tag to the file system. Only existing tags can be added in this step.

4. Click **Submit**, and the tag will be bound to the corresponding file system once created successfully.

>For more information on the configuration for creating a file system, see [Creating File Systems and Mount Targets](https://intl.cloud.tencent.com/document/product/582/9132).


### Adding, modifying, or delete a tag on an existing file system

1. On the File System List page, locate the file system for which you want to edit a tag, and click **Edit Tag** in the Operation column.

2. In the "you have selected 1 cloud resource" pop-up window, add, modify or delete the tag as needed.

3. Click **OK**.



### Filtering file systems by tags

To filter file systems with a certain tag, follow the steps below:

1. In the search box, select **Tag**.
2. Enter tag key and tag value behind **Tag:**, and click <img src="https://main.qcloudimg.com/raw/3cca38f08eaa87087cdd1b81eaf08a0a.png" style="margin: 0;">, or press Enter to search as shown below:
For example, if you want to get file systems whose tag key is `business`, you can enter `Tag:business`. If you want to get file systems whose tag key is `business` and tag value is `mkt`, you can enter `Tag:business:mkt` .
