---
title: "CRowsetImpl::m_rgRowData | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CRowsetImpl.m_rgRowData"
  - "CRowsetImpl::m_rgRowData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "m_rgRowData"
ms.assetid: e4e75ca7-12e8-4a0b-94e8-e395c21385b2
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowsetImpl::m_rgRowData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

De forma predeterminada, `CAtlArray` que templatizes en el argumento de plantilla de registro de usuario a `CRowsetImpl`.  
  
## Sintaxis  
  
```  
  
ArrayType CRowsetBaseImpl::m_rgRowData;  
  
```  
  
## Comentarios  
 **ArrayType** es un parámetro de plantilla a `CRowsetImpl`.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [CRowsetImpl \(Clase\)](../../data/oledb/crowsetimpl-class.md)   
 [CRowsetImpl::m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)   
 [CRowsetImpl::m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)