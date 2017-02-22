---
title: "SimpleClassFactory (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::SimpleClassFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SimpleClassFactory (clase)"
ms.assetid: 6edda1b2-4e44-4e14-9364-72f519249962
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# SimpleClassFactory (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Proporciona un mecanismo fundamental para crear una clase base.  
  
## Sintaxis  
  
```  
template<  
   typename Base  
>  
class SimpleClassFactory : public ClassFactory<>;  
```  
  
#### Parámetros  
 `Base`  
 Una clase base.  
  
## Comentarios  
 La clase base debe proporcionar un constructor predeterminado.  
  
 El ejemplo de código siguiente muestra cómo utilizar SimpleClassFactory con la macro de [ActivatableClassWithFactoryEx](../Topic/ActivatableClass%20Macros.md) .  
  
 `ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SimpleClassFactory::CreateInstance \(Método\)](../windows/simpleclassfactory-createinstance-method.md)|Crea una instancia de la interfaz especificada.|  
  
## Jerarquía de herencia  
 `I0`  
  
 `ChainInterfaces`  
  
 `I0`  
  
 `RuntimeClassBase`  
  
 `ImplementsHelper`  
  
 `DontUseNewUseMake`  
  
 `RuntimeClassFlags`  
  
 `RuntimeClassBaseT`  
  
 `RuntimeClass`  
  
 `ClassFactory`  
  
 `SimpleClassFactory`  
  
## Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Microsoft::WRL \(Espacio de nombres\)](../windows/microsoft-wrl-namespace.md)