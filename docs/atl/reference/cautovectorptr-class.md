---
title: "CAutoVectorPtr Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CAutoVectorPtr"
  - "ATL.CAutoVectorPtr"
  - "ATL.CAutoVectorPtr<T>"
  - "CAutoVectorPtr"
  - "ATL::CAutoVectorPtr<T>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAutoVectorPtr class"
ms.assetid: 0030362b-6bc4-4a47-9b5b-3c3899dceab4
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CAutoVectorPtr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase representa un objeto de puntero inteligente mediante el vector nuevo y operadores de cancelación.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template<  
typename T  
> class CAutoVectorPtr  
```  
  
#### Parámetros  
 `T`  
 el tipo de puntero.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAutoVectorPtr::CAutoVectorPtr](../Topic/CAutoVectorPtr::CAutoVectorPtr.md)|el constructor.|  
|[CAutoVectorPtr::~CAutoVectorPtr](../Topic/CAutoVectorPtr::~CAutoVectorPtr.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAutoVectorPtr::Allocate](../Topic/CAutoVectorPtr::Allocate.md)|Llame a este método para asignar memoria requerida por la matriz de objetos indicada por `CAutoVectorPtr`.|  
|[CAutoVectorPtr::Attach](../Topic/CAutoVectorPtr::Attach.md)|Llame a este método para realizar la propiedad de un puntero existente.|  
|[CAutoVectorPtr::Detach](../Topic/CAutoVectorPtr::Detach.md)|Llame a este método para liberar la propiedad de un puntero.|  
|[CAutoVectorPtr::Free](../Topic/CAutoVectorPtr::Free.md)|Llame a este método para eliminar un objeto señala `CAutoVectorPtr`.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAutoVectorPtr::operator T \*](../Topic/CAutoVectorPtr::operator%20T%20*.md)|El operador de conversión.|  
|[CAutoVectorPtr::operator \=](../Topic/CAutoVectorPtr::operator%20=.md)|el operador de asignación.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAutoVectorPtr::m\_p](../Topic/CAutoVectorPtr::m_p.md)|La variable miembro de datos de puntero.|  
  
## Comentarios  
 Esta clase proporciona métodos para crear y administrar un puntero inteligente, que ayuda a protegerse frente a pérdidas de memoria automáticamente libera los recursos cuando está fuera de ámbito.  `CAutoVectorPtr` es similar a `CAutoPtr`, la única diferencia que es que las aplicaciones [vector new &#91;&#93;](../Topic/operator%20new\(%3Cnew%3E\).md) y [el vector elimina &#91;&#93;](../Topic/operator%20delete\(%3Cnew%3E\).md) de `CAutoVectorPtr` de asignar y liberar memoria en lugar de C\+\+ **nuevo** y operadores de **borrar** .  Vea [CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md) si las clases de colección de `CAutoVectorPtr` se requieren.  
  
 Vea [CAutoPtr](../../atl/reference/cautoptr-class.md) para obtener un ejemplo de cómo utilizar una clase de puntero inteligente.  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [CAutoPtr Class](../../atl/reference/cautoptr-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)