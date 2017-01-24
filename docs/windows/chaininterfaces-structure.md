---
title: "ChainInterfaces (Estructura) | Microsoft Docs"
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
  - "implements/Microsoft::WRL::ChainInterfaces"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ChainInterfaces (estructura)"
ms.assetid: d7415b59-5468-4bef-a3fd-8d82b12f0e9c
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ChainInterfaces (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica las funciones de comprobación y de inicialización que se pueden aplicar a un conjunto de id. de la interfaz.  
  
## Sintaxis  
  
```  
template <  
   typename I0,  
   typename I1,  
   typename I2 = Details::Nil,  
   typename I3 = Details::Nil,  
   typename I4 = Details::Nil,  
   typename I5 = Details::Nil,  
   typename I6 = Details::Nil,  
   typename I7 = Details::Nil,  
   typename I8 = Details::Nil,  
   typename I9 = Details::Nil  
>  
struct ChainInterfaces : I0;  
template <  
   typename DerivedType,  
   typename BaseType,  
   bool hasImplements,  
   typename I1,  
   typename I2,  
   typename I3,  
   typename I4,  
   typename I5,  
   typename I6,  
   typename I7,  
   typename I8,  
   typename I9  
>  
struct ChainInterfaces<MixIn<DerivedType, BaseType, hasImplements>, I1, I2, I3, I4, I5, I6, I7, I8, I9>;  
```  
  
#### Parámetros  
 `I0`  
 Identificador \(necesario\) 0 de la interfaz.  
  
 `I1`  
 Identificador \(necesario\) 1. de interfaz.  
  
 `I2`  
 \(Opcional\) Identificador 2. de interfaz.  
  
 `I3`  
 \(Opcional\) Identificador 3. de interfaz.  
  
 `I4`  
 \(Opcional\) Identificador 4. de interfaz.  
  
 `I5`  
 \(Opcional\) Identificador 5. de interfaz.  
  
 `I6`  
 \(Opcional\) Identificador 6. de interfaz.  
  
 `I7`  
 \(Opcional\) Identificador 7. de interfaz.  
  
 `I8`  
 \(Opcional\) Identificador 8. de interfaz.  
  
 `I9`  
 \(Opcional\) Identificador 9. de interfaz.  
  
 `DerivedType`  
 Un tipo derivado.  
  
 `BaseType`  
 El tipo base de un tipo derivado.  
  
 `hasImplements`  
 Un valor booleano que si `true`, significa que no se puede utilizar una estructura de [MixIn](../windows/mixin-structure.md) con una clase que no se deriva de la estructura de [Implementa](../Topic/Implements%20Structure.md) .  
  
## Miembros  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ChainInterfaces::CanCastTo \(Método\)](../Topic/ChainInterfaces::CanCastTo%20Method.md)|Indica si el identificador de interfaz especificado se puede convertir a cada una de las especializaciones definidas por los parámetros de plantilla de ChainInterface.|  
|[ChainInterfaces::CastToUnknown \(Método\)](../windows/chaininterfaces-casttounknown-method.md)|Convierte el puntero de interfaz de tipo definido por el parámetro de plantilla de `I0` a un puntero a IUnknown.|  
|[ChainInterfaces::FillArrayWithIid \(Método\)](../Topic/ChainInterfaces::FillArrayWithIid%20Method.md)|Almacena el identificador de interfaz especificado por el parámetro de plantilla de `I0` en una ubicación especificada de una matriz de id. de la interfaz.|  
|[ChainInterfaces::Verify \(Método\)](../windows/chaininterfaces-verify-method.md)|Comprueba que cada interfaz definida por los parámetros `I0` de plantilla con `I9` hereda de IUnknown o de IInspectable, y que `I0` hereda de `I1` con `I9`.|  
  
### Constantes protegidas  
  
|Name|Descripción|  
|----------|-----------------|  
|[ChainInterfaces::IidCount \(Constante\)](../windows/chaininterfaces-iidcount-constant.md)|El número total de id. de interfaz contenidos en las interfaces especificadas por los parámetros `I0` de plantilla con `I9`.|  
  
## Jerarquía de herencia  
 `I0`  
  
 `ChainInterfaces`  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Microsoft::WRL \(Espacio de nombres\)](../windows/microsoft-wrl-namespace.md)