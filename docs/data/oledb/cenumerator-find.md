---
title: "CEnumerator::Find | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CEnumerator::Find"
  - "ATL::CEnumerator::Find"
  - "ATL.CEnumerator.Find"
  - "CEnumerator.Find"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Find (método)"
ms.assetid: 69a153af-d6c3-40fd-9018-27c7d2f344c6
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CEnumerator::Find
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Busca un nombre especificado entre los proveedores disponibles.  
  
## Sintaxis  
  
```  
  
      bool Find(   
   TCHAR* szSearchName    
) throw( );  
```  
  
#### Parámetros  
 *szSearchName*  
 \[in\] El nombre que se va a buscar.  
  
## Valor devuelto  
 **true** si el nombre se encontró.  De lo contrario, es **false**.  
  
## Comentarios  
 Mapas de este nombre al miembro de **SOURCES\_NAME** de la interfaz de [ISourcesRowset](https://msdn.microsoft.com/en-us/library/ms715969.aspx) .  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CEnumerator \(Clase\)](../../data/oledb/cenumerator-class.md)