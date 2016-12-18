---
title: "InterfaceTraits (Estructura) | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Details::InterfaceTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "InterfaceTraits (estructura)"
ms.assetid: ede0c284-19a7-4892-9738-ff3da4923d0a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# InterfaceTraits (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
template<  
   typename I0  
>  
struct __declspec(novtable) InterfaceTraits;  
  
template<  
   typename CloakedType  
>  
struct __declspec(novtable) InterfaceTraits<CloakedIid<CloakedType>>;  
  
template<>  
struct __declspec(novtable) InterfaceTraits<Nil>;  
```  
  
#### Parámetros  
 `I0`  
 El nombre de una interfaz.  
  
 `CloakedType`  
 Para RuntimeClass, implementar y ChainInterfaces, una interfaz que no esté en la lista de id. compatibles de la interfaz.  
  
## Comentarios  
 Implementa características comunes de una interfaz.  
  
 La segunda plantilla es una especialización para las interfaces disimuladas.  La tercera plantilla es una especialización de los parámetros de Nil.  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`Base`|Un sinónimo para el parámetro de plantilla de `I0` .|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[InterfaceTraits::CanCastTo \(Método\)](../Topic/InterfaceTraits::CanCastTo%20Method.md)|Indica si el puntero especificado se puede convertir a un puntero a `Base`.|  
|[InterfaceTraits::CastToBase \(Método\)](../windows/interfacetraits-casttobase-method.md)|Convierte el puntero especificado a un puntero a `Base`.|  
|[InterfaceTraits::CastToUnknown \(Método\)](../windows/interfacetraits-casttounknown-method.md)|Convierte el puntero especificado a un puntero a IUnknown.|  
|[InterfaceTraits::FillArrayWithIid \(Método\)](../windows/interfacetraits-fillarraywithiid-method.md)|Asigna el identificador de interfaz de `Base` al elemento de matriz especificado por el argumento index.|  
|[InterfaceTraits::Verify \(Método\)](../Topic/InterfaceTraits::Verify%20Method.md)|Comprueba que la base está derivada correctamente.|  
  
### Constantes públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[InterfaceTraits::IidCount \(Constante\)](../Topic/InterfaceTraits::IidCount%20Constant.md)|Contiene el número de id. de interfaz asociados al objeto actual de InterfaceTraits.|  
  
## Jerarquía de herencia  
 `InterfaceTraits`  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)