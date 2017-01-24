---
title: "CDataConnection::operator CDataSource&amp; | Microsoft Docs"
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
  - "CDataSource&"
  - "CDataConnection.operatorCDataSource&"
  - "operatorCDataSource&"
  - "CDataConnection::operatorCDataSource&"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDataSource& (operador)"
  - "operador & (CDataSource)"
ms.assetid: 852faeee-f1b1-4465-9828-b261d1edf022
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataConnection::operator CDataSource&amp;
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve una referencia al objeto contenido de `CDataSource` .  
  
## Sintaxis  
  
```  
  
operator const CDataSource&() throw( );  
  
```  
  
## Comentarios  
 Este operador devuelve una referencia al objeto contenido de `CDataSource` , permitiendo pasar un objeto de `CDataConnection` donde se espera una referencia de `CDataSource` .  
  
## Ejemplo  
 Si tiene una función \(como `func` abajo\) que toma una referencia de `CDataSource` , puede utilizar **CDataSource&** para pasar un objeto de `CDataConnection` en su lugar.  
  
 [!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/CPP/cdataconnection-operator-cdatasource-amp_1.cpp)]  
  
 [!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/CPP/cdataconnection-operator-cdatasource-amp_2.cpp)]  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDataConnection \(Clase\)](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CDataSource\*](../../data/oledb/cdataconnection-operator-cdatasource-star.md)