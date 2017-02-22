---
title: "CAtlFileMapping Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CAtlFileMapping<T>"
  - "ATL.CAtlFileMapping"
  - "ATL::CAtlFileMapping"
  - "CAtlFileMapping"
  - "ATL.CAtlFileMapping<T>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlFileMapping class"
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CAtlFileMapping Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase representa un archivo asignado a memoria, agregando un operador de conversión a los métodos de [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template <  
typename T= char  
>  
class CAtlFileMapping :  
public CAtlFileMappingBase  
```  
  
#### Parámetros  
 `T`  
 El tipo de datos utilizados para el operador de conversión.  
  
## Members  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlFileMapping::operator T\*](../Topic/CAtlFileMapping::operator%20T*.md)|permite la conversión implícita de los objetos de `CAtlFileMapping` a `T`**\***.|  
  
## Comentarios  
 Esta clase agrega un único operador de conversión para permitir la conversión implícita de los objetos de `CAtlFileMapping` a `T`**\***.  La clase base, [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)proporcionan otros miembros.  
  
## Jerarquía de herencia  
 [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)  
  
 `CAtlFileMapping`  
  
## Requisitos  
 **encabezado:** atlfile.h  
  
## Vea también  
 [CAtlFileMappingBase Class](../../atl/reference/catlfilemappingbase-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)