---
title: "ClassFactory (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::ClassFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ClassFactory (clase)"
ms.assetid: f13e6bce-722b-4f18-b7cf-3ffa6345c1db
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# ClassFactory (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Implementa la funcionalidad básica de la interfaz IClassFactory.  
  
## Sintaxis  
  
```  
template <  
   typename I0 = Details::Nil,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil  
>  
class ClassFactory : public Details::RuntimeClass<  
   typename Details::InterfaceListHelper<IClassFactory,   
   I0,   
   I1,   
   I2,   
   Details::Nil>::TypeT,   
   RuntimeClassFlags<ClassicCom | InhibitWeakReference>,   
      false>;  
```  
  
#### Parámetros  
 `I0`  
 La interfaz de zeroth.  
  
 `I1`  
 La primera interfaz.  
  
 `I2`  
 La segunda interfaz.  
  
## Comentarios  
 Utilice `ClassFactory` para proporcionar una implementación definido por el usuario del generador.  
  
 El modelo de programación siguiente muestra cómo utilizar la estructura de [Implementa](../Topic/Implements%20Structure.md) para especificar más de tres interfaces en un generador de clases.  
  
 `struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ClassFactory::ClassFactory \(Constructor\)](../Topic/ClassFactory::ClassFactory%20Constructor.md)||  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ClassFactory::AddRef \(Método\)](../Topic/ClassFactory::AddRef%20Method.md)|Incrementa el recuento de referencias para el objeto actual de ClassFactory.|  
|[ClassFactory::LockServer \(Método\)](../windows/classfactory-lockserver-method.md)|Aumenta o disminuye el número de objetos subyacentes que son seguido del objeto actual de ClassFactory.|  
|[ClassFactory::QueryInterface \(Método\)](../windows/classfactory-queryinterface-method.md)|Recupera un puntero a la interfaz especificada por parámetro.|  
|[ClassFactory::Release \(Método\)](../windows/classfactory-release-method.md)|Disminuye el recuento de referencias para el objeto actual de ClassFactory.|  
  
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
  
## Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Microsoft::WRL \(Espacio de nombres\)](../windows/microsoft-wrl-namespace.md)   
 [RuntimeClassType \(Enumeración\)](../windows/runtimeclasstype-enumeration.md)