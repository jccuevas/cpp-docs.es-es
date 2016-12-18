---
title: "CSimpleRow::Compare | Microsoft Docs"
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
  - "CSimpleRow.Compare"
  - "CSimpleRow::Compare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Compare (método)"
ms.assetid: 0bb65f09-c7bc-449b-aa4e-c828cac13510
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSimpleRow::Compare
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Compara dos filas para ver si hacen referencia a la misma instancia de fila.  
  
## Sintaxis  
  
```  
  
      HRESULT Compare(   
   CSimpleRow* pRow    
);  
```  
  
#### Parámetros  
 `pRow`  
 Un puntero a un objeto de `CSimpleRow` .  
  
## Valor devuelto  
 Un valor de `HRESULT` , normalmente `S_OK`, que indica las dos filas es la misma instancia de fila, o **S\_FALSE**, que indica las dos filas es diferente.  Vea [IRowsetIdentity::IsSameRow](https://msdn.microsoft.com/en-us/library/ms719629.aspx) en *la referencia del* programador para otros valores devueltos posibles.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [CSimpleRow \(Clase\)](../../data/oledb/csimplerow-class.md)   
 [CSimpleRow::ReleaseRow](../../data/oledb/csimplerow-releaserow.md)   
 [IRowsetImpl::RefRows](../../data/oledb/irowsetimpl-refrows.md)