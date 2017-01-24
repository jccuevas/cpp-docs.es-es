---
title: "IRowsetIdentityImpl::IsSameRow | Microsoft Docs"
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
  - "IsSameRow"
  - "IRowsetIdentityImpl.IsSameRow"
  - "ATL.IRowsetIdentityImpl.IsSameRow"
  - "IRowsetIdentityImpl::IsSameRow"
  - "ATL::IRowsetIdentityImpl::IsSameRow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsSameRow (método)"
ms.assetid: e35ad54e-73f1-4dc0-8d8c-9e98202baf0a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetIdentityImpl::IsSameRow
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Compara dos identificadores de fila para ver si hacen referencia a la misma fila.  
  
## Sintaxis  
  
```  
  
      STDMETHOD( IsSameRow )(  
   HROW hThisRow,  
   HROW hThatRow   
);  
```  
  
#### Parámetros  
 Vea [IRowsetIdentity::IsSameRow](https://msdn.microsoft.com/en-us/library/ms719629.aspx) en *la referencia del*programador.  
  
## Comentarios  
 Para comparar los identificadores de fila, este método convierte los identificadores de **HROW** a los miembros de **RowClass** y llama a `memcmp` de punteros.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IRowsetIdentityImpl \(Clase\)](../../data/oledb/irowsetidentityimpl-class.md)