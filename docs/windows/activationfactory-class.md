---
title: "ActivationFactory (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::ActivationFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActivationFactory (clase)"
ms.assetid: 5faddf1f-43b6-4f8a-97de-8c9d3ae1e1ff
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# ActivationFactory (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Habilita una o más clases que se inicien en el tiempo de ejecución de Windows.  
  
## Sintaxis  
  
```  
template <  
   typename I0 = Details::Nil,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil  
>  
class ActivationFactory : public Details::RuntimeClass<typename Details::InterfaceListHelper<IActivationFactory, I0, I1, I2, Details::Nil>::TypeT, RuntimeClassFlags<WinRt | InhibitWeakReference>, false>;  
```  
  
#### Parámetros  
 `I0`  
 La interfaz de zeroth.  
  
 `I1`  
 La primera interfaz.  
  
 `I2`  
 La segunda interfaz.  
  
## Comentarios  
 ActivationFactory proporciona métodos de registro y la funcionalidad básica para la interfaz de IActivationFactory.  De ActivationFactory también permite proporcionar una implementación personalizada del generador.  
  
 El fragmento de código siguiente muestra simbólicamente cómo utilizar ActivationFactory.  
  
 [!code-cpp[wrl-microsoft__wrl__activationfactory#1](../windows/codesnippet/CPP/activationfactory-class_1.cpp)]  
  
 El siguiente fragmento de código se muestra cómo utilizar la estructura de [Implementa](../Topic/Implements%20Structure.md) para especificar más de tres id. de la interfaz.  
  
 `struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ActivationFactory::ActivationFactory \(Constructor\)](../windows/activationfactory-activationfactory-constructor.md)|Inicializa la clase de ActivationFactory.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ActivationFactory::AddRef \(Método\)](../windows/activationfactory-addref-method.md)|Incrementa el recuento de referencias del objeto actual de ActivationFactory.|  
|[ActivationFactory::GetIids \(Método\)](../windows/activationfactory-getiids-method.md)|Recupera una matriz de id. implementados de la interfaz.|  
|[ActivationFactory::GetRuntimeClassName \(Método\)](../windows/activationfactory-getruntimeclassname-method.md)|Obtiene el nombre de clase del objeto en tiempo de ejecución que el ActivationFactory actual crea instancias.|  
|[ActivationFactory::GetTrustLevel \(Método\)](../windows/activationfactory-gettrustlevel-method.md)|Obtiene el nivel de confianza del objeto que el ActivationFactory actual crea instancias.|  
|[ActivationFactory::QueryInterface \(Método\)](../windows/activationfactory-queryinterface-method.md)|Recupera un puntero a la interfaz especificada.|  
|[ActivationFactory::Release \(Método\)](../windows/activationfactory-release-method.md)|Disminuye el recuento de referencias del objeto actual de ActivationFactory.|  
  
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
  
## Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Microsoft::WRL \(Espacio de nombres\)](../windows/microsoft-wrl-namespace.md)