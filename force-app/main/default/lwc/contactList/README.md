# README

## 一句话概括

这两段代码通过使用 Apex 来抛出处理错误的模拟，以及使用 Lightning Web Components (LWC) 来创建联系人记录并在成功时显示通知，实现了 Salesforce 平台上的前端和后端交互功能。

!!用到了开源的component-ldsUtils
https://github.com/trailheadapps/lwc-recipes

## 概览

此 README 提供了使用 Apex 和 Lightning Web Components (LWC) 实现的两个 Salesforce 代码片段的简要概述。第一部分是一个用于与 Salesforce 联系人交互的 Apex 类，而第二部分是一个使用 LWC 创建联系人记录并通过 toast 通知向用户提供反馈的 JavaScript 类。

### 1. Apex 类：ContactController

**目的**：
- `ContactController` 类旨在与 Salesforce 的联系人数据进行交互，但在此示例中，它被设计为抛出一个错误，以模拟错误处理。

**实现细节**：
- 类使用 `@AuraEnabled(cacheable=true)` 注解，使得其方法 `getContacts` 能够在客户端进行缓存，以提高性能。
- `getContacts` 方法原本应返回从 Salesforce 数据库中查询的联系人列表，但在这段代码中，它通过抛出 `AuraHandledBean('Forced error')` 强制抛出一个错误。这可以用于前端错误处理的演示。

### 2. JavaScript 类：ContactCreator (LWC)

**目的**：
- `ContactCreator` 类用于在 Salesforce 中创建新的联系人记录，并在创建成功后向用户显示通知。

**实现细节**：
- 类通过导入 LightningElement 以及特定的 Salesforce 架构字段，实现了对 Salesforce 数据对象的操作。
- `objectApiName` 和 `fields` 属性分别用于指定操作的 Salesforce 对象和需要处理的字段。
- `handleSuccess` 方法处理记录创建成功的事件，它会触发一个显示 "Contact created" 的 toast 通知，通知中包含了新创建的记录的 ID。这增强了用户界面的交互性和用户体验。

以上代码片段展示了在 Salesforce 平台上使用 Apex 和 LWC 技术进行开发的基本模式，包括错误处理和用户交互的实现。