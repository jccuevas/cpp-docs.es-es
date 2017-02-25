---
title: "CCommand::Prepare | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CCommand.Prepare"
  - "CCommand::Prepare"
  - "Prepare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Prepare (método)"
ms.assetid: f0e473fc-2f7a-4d29-96c2-1328dc21e702
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CCommand::Prepare
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Valida y optimiza el comando actual.  
  
## Sintaxis  
  
```  
  
      HRESULT CCommandBase::Prepare(  
   ULONG cExpectedRuns = 0   
) throw( );  
```  
  
#### Parámetros  
 *cExpectedRuns*  
 \[in\] El número de veces que espera ejecutar el comando.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Este método encapsula el método [ICommandPrepare::Prepare](https://msdn.microsoft.com/en-us/library/ms718370.aspx)OLE DB.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CCommand \(Clase\)](../../data/oledb/ccommand-class.md)