---
title: "CCommand::Unprepare | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Unprepare"
  - "CCommand.Unprepare"
  - "CCommand::Unprepare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Unprepare (método)"
ms.assetid: 4fe59988-fe51-4c7c-a156-72b68e3d642b
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CCommand::Unprepare
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Descarta el plan de ejecución actual del comando.  
  
## Sintaxis  
  
```  
  
HRESULT CCommandBase::Unprepare( ) throw( );  
  
```  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Este método encapsula el método [ICommandPrepare::Unprepare](https://msdn.microsoft.com/en-us/library/ms719635.aspx)OLE DB.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CCommand \(Clase\)](../../data/oledb/ccommand-class.md)