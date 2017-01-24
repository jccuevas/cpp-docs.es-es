---
title: "SimpleActivationFactory (Clase) | Microsoft Docs"
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
  - "module/Microsoft::WRL::SimpleActivationFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SimpleActivationFactory (clase)"
ms.assetid: aff768e0-0038-4fd7-95d2-ad7d308da41c
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SimpleActivationFactory (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Proporciona un mecanismo fundamental para crear un tiempo de ejecución de Windows o una clase base de COM del trabajo clásica.  
  
## Sintaxis  
  
```  
template<  
   typename Base  
>  
class SimpleActivationFactory : public ActivationFactory<>;  
```  
  
#### Parámetros  
 `Base`  
 Una clase base.  
  
## Comentarios  
 La clase base debe proporcionar un constructor predeterminado.  
  
 El ejemplo de código siguiente muestra cómo utilizar SimpleActivationFactory con la macro de [ActivatableClassWithFactoryEx](../Topic/ActivatableClass%20Macros.md) .  
  
 `ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SimpleActivationFactory::ActivateInstance \(Método\)](../windows/simpleactivationfactory-activateinstance-method.md)|Crea una instancia de la interfaz especificada.|  
|[SimpleActivationFactory::GetRuntimeClassName \(Método\)](../windows/simpleactivationfactory-getruntimeclassname-method.md)|Obtiene el nombre de clase en tiempo de ejecución de una instancia de la clase especificada por el parámetro de plantilla de clase de `Base` .|  
|[SimpleActivationFactory::GetTrustLevel \(Método\)](../Topic/SimpleActivationFactory::GetTrustLevel%20Method.md)|Obtiene el nivel de confianza de una instancia de la clase especificada por el parámetro de plantilla de clase de `Base` .|  
  
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
  
 `ActivationFactory`  
  
 `SimpleActivationFactory`  
  
## Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Microsoft::WRL \(Espacio de nombres\)](../windows/microsoft-wrl-namespace.md)