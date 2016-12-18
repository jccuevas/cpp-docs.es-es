---
title: "CFixedStringT Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFixedStringT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFixedStringT class"
  - "shared classes, CFixedStringT"
ms.assetid: 6d4171ba-3104-493a-a6cc-d515f4ba9a4b
caps.latest.revision: 17
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFixedStringT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase representa un objeto de cadena con un búfer fijo de carácter.  
  
## Sintaxis  
  
```  
  
      template< class   
      StringType  
      , int   
      t_nChars  
       >    
class CFixedStringT : private CFixedStringMgr, public StringType  
```  
  
#### Parámetros  
 `StringType`  
 Se utiliza como clase base para el objeto string fijo y puede ser cualquier `CStringT`\- tipos basándose.  algunos ejemplos incluyen `CString`, `CStringA`, y `CStringW`.  
  
 *t\_nChars*  
 el número de caracteres almacenado en el búfer.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFixedStringT::CFixedStringT](../Topic/CFixedStringT::CFixedStringT.md)|El constructor del objeto de cadena.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFixedStringT::operator \=](../Topic/CFixedStringT::operator%20=.md)|asigna un nuevo valor a un objeto de `CFixedStringT` .|  
  
## Comentarios  
 esta clase es un ejemplo de una clase personalizada de la cadena basada en `CStringT`.  Aunque muy son similares, las dos clases difieren en la implementación.  las diferencias principales entre `CFixedStringT` y `CStringT` son:  
  
-   El búfer inicial de caracteres se asigna como parte del objeto y tiene *t\_nChars*size.  Esto permite que el objeto de **CFixedString** ocupa un fragmento contiguo de memoria por razones de rendimiento.  Sin embargo, si el contenido de un objeto de `CFixedStringT` crecen más allá *de t\_nChars*, el búfer se asigna dinámicamente.  
  
-   El búfer de caracteres para un objeto de `CFixedStringT` es siempre la misma longitud \(*t\_nChars*\).  No hay límite en el tamaño de búfer para los objetos de `CStringT` .  
  
-   Personalizar el administrador de memoria para `CFixedStringT` tales que compartir de un objeto de [CStringData](../../atl-mfc-shared/reference/cstringdata-class.md) entre dos o más objectsis de `CFixedStringT` no permitidos.  los objetos de`CStringT` no tienen esta limitación.  
  
 Para obtener más información sobre la personalización de `CFixedStringT` y administración de memoria para los objetos de cadena vea normalmente [administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
## Jerarquía de herencia  
 `IAtlStringMgr`  
  
 `StringType`  
  
 `CFixedStringMgr`  
  
 `CFixedStringT`  
  
## Requisitos  
 **encabezado:** cstringt.h  
  
## Vea también  
 [CStringT Class](../../atl-mfc-shared/reference/cstringt-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)