---
title: "CDataConnection::operator CDataSource* | Microsoft Docs"
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
  - "CDataSource*"
  - "CDataConnection::operatorCDataSource*"
  - "CDataConnection.operatorCDataSource*"
  - "operatorCDataSource*"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDataSource* (operador)"
  - "operator * (CDataSource)"
ms.assetid: 9118e324-e68d-45c5-a791-03f041d420ed
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataConnection::operator CDataSource*
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve un puntero al objeto contenido de `CDataSource` .  
  
## Sintaxis  
  
```  
  
operator const CDataSource*() throw( );  
  
```  
  
## Comentarios  
 Este operador devuelve un puntero al objeto contenido de `CDataSource` , permitiendo pasar un objeto de `CDataConnection` donde se espera un puntero de `CDataSource` .  
  
 Vea [operador CDataSource&](../../data/oledb/cdataconnection-operator-cdatasource-amp.md) para obtener un ejemplo de uso.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDataConnection \(Clase\)](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CDataSource&](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)