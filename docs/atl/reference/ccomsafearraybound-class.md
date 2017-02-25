---
title: "CComSafeArrayBound Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComSafeArrayBound"
  - "ATL::CComSafeArrayBound"
  - "CComSafeArrayBound"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComSafeArrayBound class"
ms.assetid: dd6299db-5f84-4630-bbf0-f5add5318437
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CComSafeArrayBound Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase es un contenedor para una estructura de [SAFEARRAYBOUND](http://msdn.microsoft.com/es-es/303a9bdb-71d6-4f14-8747-84cf84936c6d) .  
  
## Sintaxis  
  
```  
  
class CComSafeArrayBound : public SAFEARRAYBOUND  
  
```  
  
## Members  
  
### Métodos  
  
|||  
|-|-|  
|[CComSafeArrayBound](../Topic/CComSafeArrayBound::CComSafeArrayBound.md)|el constructor.|  
|[GetCount](../Topic/CComSafeArrayBound::GetCount.md)|Llame a este método para devolver el número de elementos.|  
|[GetLowerBound](../Topic/CComSafeArrayBound::GetLowerBound.md)|Llame a este método para devolver el límite inferior.|  
|[GetUpperBound](../Topic/CComSafeArrayBound::GetUpperBound.md)|Llame a este método para devolver el límite superior.|  
|[SetCount](../Topic/CComSafeArrayBound::SetCount.md)|Llame a este método para establecer el número de elementos.|  
|[SetLowerBound](../Topic/CComSafeArrayBound::SetLowerBound.md)|Llame a este método para establecer el límite inferior.|  
  
### Operadores  
  
|||  
|-|-|  
|[operador \=](../Topic/CComSafeArrayBound::operator%20=.md)|Establece `CComSafeArrayBound` en un nuevo valor.|  
  
## Comentarios  
 esta clase es un contenedor para la estructura de **SAFEARRAYBOUND** utilizada por [CComSafeArray](../../atl/reference/ccomsafearray-class.md).  Proporciona métodos para consultar y establecer los límites superior e inferior de una sola dimensión de un objeto de `CComSafeArray` y el número de elementos que contiene.  Un objeto multidimensional de `CComSafeArray` utiliza una matriz de los objetos de `CComSafeArrayBound` , uno para cada dimensión.  Por consiguiente, cuando utilice métodos como [GetCount](../Topic/CComSafeArrayBound::GetCount.md), tenga en cuenta que este método no devolverá el número total de elementos de una matriz multidimensional.  
  
 **encabezado:** atlsafe.h  
  
## Requisitos  
 **encabezado:** atlsafe.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)