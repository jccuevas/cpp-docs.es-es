---
title: "CRowsetImpl::NameFromDBID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CRowsetImpl.NameFromDBID"
  - "CRowsetImpl::NameFromDBID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NameFromDBID (método)"
ms.assetid: 6aa5b074-90c7-4434-adfd-c64c13e76c78
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CRowsetImpl::NameFromDBID
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Dibuja una cadena de **DBID** y cópiela en `bstr` pasado.  
  
## Sintaxis  
  
```  
  
      HRESULT CRowsetBaseImpl::NameFromDBID(  
   DBID* pDBID,  
   CComBSTR& bstr,  
   bool bIndex   
);  
```  
  
#### Parámetros  
 *pDBID*  
 \[in\] Un puntero a **DBID** de las que para extraer una cadena.  
  
 `bstr`  
 \[in\] Una referencia de [CComBSTR](../../atl/reference/ccombstr-class.md) para colocar una copia de la cadena de **DBID** .  
  
 `bIndex`  
 \[in\] **true** si un índice **DBID**; **false** si una tabla **DBID**.  
  
## Valor devuelto  
 `HRESULT`estándar.  Dependiendo de si **DBID** es una tabla o un índice \(denotado por `bIndex`\), el método devolverá **DB\_E\_NOINDEX** o **DB\_E\_NOTABLE**.  
  
## Comentarios  
 Este método llama las implementaciones de `CRowsetImpl` de [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) y de [GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md).  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [CRowsetImpl \(Clase\)](../../data/oledb/crowsetimpl-class.md)