---
title: "CDataConnection::operator CSession* | Microsoft Docs"
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
  - "CDataConnection.operatorCSession*"
  - "CDataConnection::operatorCSession*"
  - "operatorCSession*"
  - "CSession*"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSession* (operador)"
  - "operador CSession*"
ms.assetid: 0b0feede-5c3e-4835-be5b-03651597014d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataConnection::operator CSession*
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve un puntero al objeto contenido de `CSession` .  
  
## Sintaxis  
  
```  
  
operator const CSession*() throw( );  
  
```  
  
## Comentarios  
 Este operador devuelve un puntero al objeto contenido de `CSession` , permitiendo pasar un objeto de `CDataConnection` donde se espera un puntero de `CSession` .  
  
## Ejemplo  
 Vea [operador CSession&](../../data/oledb/cdataconnection-operator-csession-amp.md) para obtener un ejemplo de uso.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDataConnection \(Clase\)](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CSession&](../../data/oledb/cdataconnection-operator-csession-amp.md)