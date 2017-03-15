---
title: "CSession::Commit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CSession.Commit"
  - "ATL.CSession.Commit"
  - "ATL::CSession::Commit"
  - "CSession::Commit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Commit (método)"
ms.assetid: 1d5f56b9-000c-4bae-a975-89d3452f499f
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CSession::Commit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Confirma la transacción.  
  
## Sintaxis  
  
```  
  
      HRESULT Commit(   
   BOOL bRetaining = FALSE,   
   DWORD grfTC = XACTTC_SYNC,   
   DWORD grfRM = 0    
) const throw( );  
```  
  
#### Parámetros  
 Vea [ITransaction::Commit](https://msdn.microsoft.com/en-us/library/ms713008.aspx) en *la referencia del*programador.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Para obtener más información, vea [ITransaction::Commit](https://msdn.microsoft.com/en-us/library/ms713008.aspx).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CSession \(Clase\)](../../data/oledb/csession-class.md)