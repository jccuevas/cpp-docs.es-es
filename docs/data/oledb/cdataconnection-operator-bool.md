---
title: "CDataConnection::operator BOOL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDataConnection::operatorBOOL"
  - "ATL::CDataConnection::operatorBOOL"
  - "CDataConnection.operatorBOOL"
  - "ATL.CDataConnection.operatorBOOL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BOOL (operador)"
  - "operador bool"
ms.assetid: ad0bea7f-61ff-47f7-8127-32a31e3e9b9d
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDataConnection::operator BOOL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina si la sesión actual está abierto o no.  
  
## Sintaxis  
  
```  
  
operator BOOL( ) throw( );  
  
```  
  
## Comentarios  
 Devuelve el valor de **bool** \(typedef de MFC\).  **VERDADERO** significa que la sesión actual está abierto; **FALSE** significa que se cierra la sesión actual.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDataConnection \(Clase\)](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator bool](../../data/oledb/cdataconnection-operator-bool-ole-db.md)