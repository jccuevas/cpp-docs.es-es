---
title: "IAtlStringMgr Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IAtlStringMgr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAtlStringMgr class"
  - "memoria, administrar"
  - "shared classes, IAtlStringMgr"
ms.assetid: 722f0346-a770-4aa7-8f94-177be8dba823
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# IAtlStringMgr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase representa la interfaz a un administrador de memoria de `CStringT` .  
  
## Sintaxis  
  
```  
  
__interface IAtlStringMgr  
  
```  
  
## Members  
  
### Métodos  
  
|||  
|-|-|  
|[Asigna](../Topic/IAtlStringMgr::Allocate.md)|Llame a este método para asignar una nueva estructura de datos de cadena.|  
|[Clone](../Topic/IAtlStringMgr::Clone.md)|Llame a este método para devolver un puntero a un nuevo administrador de cadena para el uso con otra instancia de `CSimpleStringT`.|  
|[Libre](../Topic/IAtlStringMgr::Free.md)|Llame a este método para liberar una estructura de datos de cadena.|  
|[GetNilString](../Topic/IAtlStringMgr::GetNilString.md)|Devuelve un puntero al objeto de `CStringData` utilizado por los objetos de cadena vacía.|  
|[reasigne](../Topic/IAtlStringMgr::Reallocate.md)|Llame a este método para reasignar una estructura de datos de cadena.|  
  
## Comentarios  
 Esta interfaz administra la memoria utilizada por las clases de la cadena de la MFC\-independiente; por ejemplo [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), [CStringT](../../atl-mfc-shared/reference/cstringt-class.md), y [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md).  
  
 También puede utilizar esta clase para implementar un administrador de memoria personalizado para la clase personalizada de la cadena.  Para obtener más información, vea [administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
## Requisitos  
 **encabezado:** atlsimpstr.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)