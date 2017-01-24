---
title: "CRowsetImpl::SetCommandText | Microsoft Docs"
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
  - "CRowsetImpl.SetCommandText"
  - "CRowsetImpl::SetCommandText"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetCommandText (método)"
ms.assetid: e016d7df-c1a0-4dee-b19b-c876680221fd
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowsetImpl::SetCommandText
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Valida y almacena s para **DBID**en las dos cadenas \([m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)\).  
  
## Sintaxis  
  
```  
  
      HRESULT CRowsetBaseImpl::SetCommandText(  
   DBID* pTableID,  
   DBID* pIndexID   
);  
```  
  
#### Parámetros  
 `pTableID`  
 \[in\] Un puntero a **DBID** que representa el identificador de la tabla  
  
 `pIndexID`  
 \[in\] Un puntero a **DBID** que representa el índice identificación  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 El método de **SetCommentText** llama `CreateRowset`, un método templatized static de `IOpenRowsetImpl`.  
  
 Este método delega su trabajo llamando a [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) y [GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md) mediante un puntero upcasted.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [CRowsetImpl \(Clase\)](../../data/oledb/crowsetimpl-class.md)