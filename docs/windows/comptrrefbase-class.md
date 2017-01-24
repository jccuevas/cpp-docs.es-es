---
title: "ComPtrRefBase (Clase) | Microsoft Docs"
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
  - "client/Microsoft::WRL::Details::ComPtrRefBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ComPtrRefBase (clase)"
ms.assetid: 6d344c1a-cc13-4a3f-8a0d-f167ccb9348f
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtrRefBase (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
template <  
   typename T  
>  
class ComPtrRefBase;  
```  
  
#### Parámetros  
 `T`  
 Un tipo de [ComPtr\<T\>](../windows/comptr-class.md) o un tipo derivado de, no simplemente la interfaz representada por el ComPtr.  
  
## Comentarios  
 Representa la clase base para la clase de [ComPtrRef](../Topic/ComPtrRef%20Class.md) .  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`InterfaceType`|Un sinónimo para el tipo de parámetro `T`de la plantilla.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ComPtrRefBase::operator IInspectable\*\* \(Operador\)](../windows/comptrrefbase-operator-iinspectable-star-star-operator.md)|Convierte el miembro de datos actual de [ptr\_](../windows/comptrrefbase-ptr-data-member.md) a puntero\-a\-uno\-puntero\- a la interfaz de IInspectable.|  
|[ComPtrRefBase::operator IUnknown\*\* \(Operador\)](../windows/comptrrefbase-operator-iunknown-star-star-operator.md)|Convierte el miembro de datos actual de [ptr\_](../windows/comptrrefbase-ptr-data-member.md) a puntero\-a\-uno\-puntero\- a la interfaz IUnknown.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ComPtrRefBase::ptr\_ \(Miembro de datos\)](../windows/comptrrefbase-ptr-data-member.md)|Puntero al tipo especificado por el parámetro actual de la plantilla.|  
  
## Jerarquía de herencia  
 `ComPtrRefBase`  
  
## Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)