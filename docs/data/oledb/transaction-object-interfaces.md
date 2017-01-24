---
title: "Interfaces del objeto de transacci&#243;n | Microsoft Docs"
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
  - "interfaces, lista"
  - "interfaces, OLE DB"
  - "plantillas del proveedor OLE DB, interfaces de objetos"
  - "proveedores OLE DB, compatibilidad con transacciones"
  - "OLE DB, interfaces"
  - "interfaces del objeto de transacción"
ms.assetid: d2ce99ce-6f7a-4ff9-bc6e-acda3633d5c8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Interfaces del objeto de transacci&#243;n
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El objeto de transacción define una unidad atómica de trabajo en un origen de datos y determina la relación entre las unidades de trabajo.  Las plantillas de proveedor OLE DB no ofrecen directamente compatibilidad con este objeto \(el programador debe crear su propio objeto\).  
  
 En la tabla siguiente se muestran las interfaces obligatorias y opcionales definidas por OLE DB para un objeto de transacción.  
  
|Interfaz|¿Obligatorio?|¿Se implementa mediante plantillas OLE DB?|  
|--------------|-------------------|------------------------------------------------|  
|[\<caps:sentence id\="tgt7" sentenceid\="63e99e63156fc90f114fa402662387ef" class\="tgtSentence"\>IConnectionPointContainer\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms683857)|Obligatorio|No|  
|[\<caps:sentence id\="tgt10" sentenceid\="f5097e646bb93cceb560c38e13953a89" class\="tgtSentence"\>ITransaction\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms723053.aspx)|Obligatorio|No|  
|[\<caps:sentence id\="tgt13" sentenceid\="130702210bcc45e1afd88b1f2aae1a0b" class\="tgtSentence"\>ISupportErrorInfo\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms715816.aspx)|Opcional|No|  
  
## Vea también  
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)