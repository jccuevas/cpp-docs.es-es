---
title: "MakeAllocator (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::MakeAllocator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MakeAllocator (clase)"
ms.assetid: a1114615-abd7-4a56-9bc3-750c118f0fa1
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# MakeAllocator (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
  
template<  
   typename T,  
   bool hasWeakReferenceSupport =   
         !__is_base_of(RuntimeClassFlags<InhibitWeakReference>,   
   T)> , T)> class MakeAllocator;  
  
template<  
   typename T  
>  
class MakeAllocator<T, false>;  
  
template<  
   typename T  
>  
class MakeAllocator<T, true>;  
```  
  
#### Parámetros  
 `T`  
 Nombre de tipo.  
  
 `hasWeakReferenceSupport`  
 `true` para asignar memoria para un objeto que admite referencias parciales; `false` para asignar memoria para un objeto que no admite referencias parciales.  
  
## Comentarios  
 Asigna memoria para una clase activatable, con o sin compatibilidad parcial de referencia.  
  
 Reemplace la clase de MakeAllocator para implementar un modelo de asignación de memoria definido por el usuario.  
  
 MakeAllocator se utiliza normalmente para evitar pérdidas de memoria si un objeto produce durante la construcción.  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[MakeAllocator::MakeAllocator \(Constructor\)](../windows/makeallocator-makeallocator-constructor.md)|Inicializa una nueva instancia de la clase de MakeAllocator.|  
|[MakeAllocator::~MakeAllocator \(Destructor\)](../Topic/MakeAllocator::~MakeAllocator%20Destructor.md)|Desinicializa la instancia actual de la clase de MakeAllocator.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[MakeAllocator::Allocate \(Método\)](../Topic/MakeAllocator::Allocate%20Method.md)|Asigna memoria y la asocia al objeto actual de MakeAllocator.|  
|[MakeAllocator::Detach \(Método\)](../windows/makeallocator-detach-method.md)|Desasocia la memoria asignada por el método de [Asigna](../Topic/MakeAllocator::Allocate%20Method.md) del objeto actual de MakeAllocator.|  
  
## Jerarquía de herencia  
 `MakeAllocator`  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)