---
title: "CAutoPtr Class | Microsoft Docs"
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
  - "CAutoPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAutoPtr class"
ms.assetid: 08988d53-4fb0-4711-bdfc-8ac29c63f410
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAutoPtr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase representa un objeto de puntero inteligente.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template<   
typename T  
>  
class CAutoPtr  
```  
  
#### Parámetros  
 `T`  
 el tipo de puntero.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAutoPtr::CAutoPtr](../Topic/CAutoPtr::CAutoPtr.md)|el constructor.|  
|[CAutoPtr::~CAutoPtr](../Topic/CAutoPtr::~CAutoPtr.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAutoPtr::Attach](../Topic/CAutoPtr::Attach.md)|Llame a este método para realizar la propiedad de un puntero existente.|  
|[CAutoPtr::Detach](../Topic/CAutoPtr::Detach.md)|Llame a este método para liberar la propiedad de un puntero.|  
|[CAutoPtr::Free](../Topic/CAutoPtr::Free.md)|Llame a este método para eliminar un objeto señala `CAutoPtr`.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAutoPtr::operator T\*](../Topic/CAutoPtr::operator%20T*.md)|El operador de conversión.|  
|[CAutoPtr::operator \=](../Topic/CAutoPtr::operator%20=.md)|el operador de asignación.|  
|[CAutoPtr::operator \-\>](../Topic/CAutoPtr::operator%20-%3E.md)|El operador de puntero a miembro.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAutoPtr::m\_p](../Topic/CAutoPtr::m_p.md)|La variable miembro de datos de puntero.|  
  
## Comentarios  
 Esta clase proporciona métodos para crear y administrar un puntero inteligente, que ayuda a protegerse frente a pérdidas de memoria automáticamente libera los recursos cuando está fuera de ámbito.  
  
 Además, el constructor de copias de entity\_CODECAutoPtr y el operador de asignación transfiere la propiedad del puntero, copiando el puntero de origen al puntero de destino y estableciendo el puntero de origen en NULL.  Por consiguiente imposible obtener dos objetos cada uno de `CAutoPtr` que almacena el mismo puntero, y esto reduce la posibilidad de eliminar el mismo puntero dos veces.  
  
 `CAutoPtr` también simplifica la creación de colecciones de punteros.  En lugar de derivar una clase de colección y de reemplazar el destructor, es más fácil crear una colección de objetos `CAutoPtr` .  Cuando se elimina la colección, los objetos de `CAutoPtr` saldrán de ámbito y automáticamente se eliminarán.  
  
 [CHeapPtr](../../atl/reference/cheapptr-class.md) y las variantes funcionan igual que `CAutoPtr`, salvo que asignan y liberan memoria mediante diferente pila funciona en lugar de C\+\+ **nuevo** y operadores de **borrar** .  [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md) es similar a `CAutoPtr`, la única diferencia es que utiliza **vector new\[\]** y **vector delete\[\]** para asignar y liberar memoria.  
  
 Vea también [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) y [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) cuando las matrices o listas de punteros inteligentes se requieren.  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/CPP/cautoptr-class_1.cpp)]  
  
## Vea también  
 [CHeapPtr Class](../../atl/reference/cheapptr-class.md)   
 [CAutoVectorPtr Class](../../atl/reference/cautovectorptr-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)