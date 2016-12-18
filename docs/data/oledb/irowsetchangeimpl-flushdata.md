---
title: "IRowsetChangeImpl::FlushData | Microsoft Docs"
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
  - "IRowsetChangeImpl::FlushData"
  - "IRowsetChangeImpl.FlushData"
  - "FlushData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FlushData (método)"
ms.assetid: fd4bc73b-bc25-4aab-90d5-0bed92670c88
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetChangeImpl::FlushData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Overidden por el proveedor para confirmar datos al almacén.  
  
## Sintaxis  
  
```  
  
      HRESULT FlushData(  
   HROW hRowToFlush,  
   HACCESSOR hAccessorToFlush   
);  
```  
  
#### Parámetros  
 *hRowToFlush*  
 \[in\] Identificador a las filas de los datos.  Determinan el tipo de esta fila de argumento de plantilla *de RowClass* de la clase de `IRowsetImpl` \(`CSimpleRow` de forma predeterminada\).  
  
 *hAccessorToFlush*  
 \[in\] Identificador del descriptor de acceso, que contiene información de enlace y de tipos en el **PROVIDER\_MAP** \(vea [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)\).  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IRowsetChangeImpl \(Clase\)](../../data/oledb/irowsetchangeimpl-class.md)