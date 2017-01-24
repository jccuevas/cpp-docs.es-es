---
title: "CDataConnection::operator CSession&amp; | Microsoft Docs"
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
  - "CSession&"
  - "CDataConnection::operatorCSession&"
  - "CDataConnection.operatorCSession&"
  - "operatorCSession&"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSession& (operador)"
  - "operador CSession&"
ms.assetid: fba1e498-e482-4dda-8e0f-2542163bf627
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataConnection::operator CSession&amp;
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve una referencia al objeto contenido de `CSession` .  
  
## Sintaxis  
  
```  
  
operator const CSession&();  
  
```  
  
## Comentarios  
 Este operador devuelve una referencia al objeto contenido de `CSession` , permitiendo pasar un objeto de `CDataConnection` donde se espera una referencia de `CSession` .  
  
## Ejemplo  
 Si tiene una función \(como `func` abajo\) que toma una referencia de `CSession` , puede utilizar **CSession&** para pasar un objeto de `CDataConnection` en su lugar.  
  
 [!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/CPP/cdataconnection-operator-csession-amp_1.cpp)]  
  
 [!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/CPP/cdataconnection-operator-csession-amp_2.cpp)]  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDataConnection \(Clase\)](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CSession\*](../../data/oledb/cdataconnection-operator-csession-star.md)