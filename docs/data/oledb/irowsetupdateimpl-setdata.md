---
title: "IRowsetUpdateImpl::SetData | Microsoft Docs"
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
  - "SetData"
  - "IRowsetUpdateImpl::SetData"
  - "IRowsetUpdateImpl.SetData"
  - "ATL::IRowsetUpdateImpl::SetData"
  - "ATL.IRowsetUpdateImpl.SetData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetData (método)"
ms.assetid: 7288a8d1-a7cf-4957-b832-0f3b18fd0da4
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetUpdateImpl::SetData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece valores de datos en una o más columnas.  
  
## Sintaxis  
  
```  
  
      STDMETHOD ( SetData )(  
   HROW hRow,  
   HACCESSOR hAccessor,  
   void* pSrcData   
);  
```  
  
#### Parámetros  
 Vea [IRowsetChange::SetData](https://msdn.microsoft.com/en-us/library/ms721232.aspx) en *la referencia del*programador.  
  
## Comentarios  
 Este método invalida el método de [IRowsetChangeImpl::SetData](../../data/oledb/irowsetchangeimpl-setdata.md) pero incluye el almacenamiento en caché de datos originales para permitir el procesamiento inmediata o aplazada de la operación.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IRowsetUpdateImpl \(Clase\)](../../data/oledb/irowsetupdateimpl-class.md)