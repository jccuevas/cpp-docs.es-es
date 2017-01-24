---
title: "CCommand::ReleaseCommand | Microsoft Docs"
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
  - "CCommand.ReleaseCommand"
  - "ReleaseCommand"
  - "CCommand::ReleaseCommand"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ReleaseCommand (método)"
ms.assetid: 3b58230c-13d5-45c5-b43e-bb013ecc3019
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCommand::ReleaseCommand
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Libera el descriptor de parámetro, entonces libera el propio comando.  
  
## Sintaxis  
  
```  
  
void CCommandBase::ReleaseCommand( ) throw( );  
  
```  
  
## Comentarios  
 `ReleaseCommand` se utiliza junto con **cerrar**.  Vea [cerrar](../../data/oledb/ccommand-close.md) para los detalles de uso.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CCommand \(Clase\)](../../data/oledb/ccommand-class.md)   
 [CCommand::Close](../../data/oledb/ccommand-close.md)