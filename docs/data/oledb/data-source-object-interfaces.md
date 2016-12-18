---
title: "Interfaces del objeto de origen de datos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "objetos de orígenes de datos [C++]"
  - "objetos de orígenes de datos [C++], interfaces"
  - "interfaces [C++], lista"
  - "interfaces [C++], OLE DB"
  - "OLE DB [C++], interfaces"
  - "plantillas de proveedores OLE DB [C++], interfaces de objetos"
ms.assetid: 929e100c-c08c-4b64-8437-d8d1357226f6
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Interfaces del objeto de origen de datos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En la tabla siguiente se muestran las interfaces obligatorias y opcionales definidas por OLE DB para un objeto de origen de datos.  
  
|Interfaz|¿Obligatorio?|¿Se implementa mediante plantillas OLE DB?|  
|--------------|-------------------|------------------------------------------------|  
|`IDBCreateSession`|Obligatorio|Sí|  
|`IDBInitialize`|Obligatorio|Sí|  
|`IDBProperties`|Obligatorio|Sí|  
|[\<caps:sentence id\="tgt14" sentenceid\="731a3344bc1c6b5f8f54d9de3524f18a" class\="tgtSentence"\>IPersist\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms688695)|Obligatorio|Sí|  
|[\<caps:sentence id\="tgt17" sentenceid\="63e99e63156fc90f114fa402662387ef" class\="tgtSentence"\>IConnectionPointContainer\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms683857)|Opcional|No|  
|`IDBDataSourceAdmin`|Opcional|No|  
|`IDBInfo`|Opcional|No|  
|[\<caps:sentence id\="tgt26" sentenceid\="7e6a12ecd4cb3b1bd45dccf9421ed567" class\="tgtSentence"\>IPersistFile\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms687223)|Opcional|No|  
|`ISupportErrorInfo`|Opcional|No|  
  
 El objeto de origen de datos implementa las interfaces `IDBProperties`, `IDBInitialize` e `IDBCreateSession` a través de la herencia.  Puede elegir entre ofrecer funcionalidad adicional heredando o no heredando de una de estas clases de implementación.  Si desea admitir la interfaz `IDBDataSourceAdmin`, debe heredar de la clase `IDBDataSourceAdminImpl`.  
  
## Vea también  
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)