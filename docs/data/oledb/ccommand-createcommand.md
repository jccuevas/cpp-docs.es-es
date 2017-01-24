---
title: "CCommand::CreateCommand | Microsoft Docs"
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
  - "CCommand.CreateCommand"
  - "CreateCommand"
  - "CCommand::CreateCommand"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateCommand (método)"
ms.assetid: 3652a313-07a1-40ec-82d6-fc7182f2a6f6
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCommand::CreateCommand
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Crea un nuevo comando.  
  
## Sintaxis  
  
```  
  
      HRESULT CCommandBase::CreateCommand(  
   const CSession& session   
) throw ( );  
```  
  
#### Parámetros  
 `session`  
 \[in\] Un objeto de `CSession` se asocie al nuevo comando.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Este método crea un comando mediante el objeto de sesión especificado.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CCommand \(Clase\)](../../data/oledb/ccommand-class.md)