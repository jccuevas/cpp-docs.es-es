---
title: "RuntimeClass (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::RuntimeClass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RuntimeClass (clase)"
ms.assetid: d52f9d1a-98e5-41f2-a143-8fb629dd0727
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# RuntimeClass (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa una clase con instancias que hereda el número especificado de interfaces y proporciona compatibilidad especificada con [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)], COM clásico y referencia débil.  
  
 Normalmente deriva sus tipos de WRL desde `RuntimeClass` porque esta clase implementa `AddRef`, `Release` y `QueryInterface`, y ayuda a administrar el número de referencia total del módulo.  
  
## Sintaxis  
  
```  
template <  
   typename I0,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil,  
   typename I3 = Details::Nil,  
   typename I4 = Details::Nil,  
   typename I5 = Details::Nil,  
   typename I6 = Details::Nil,  
   typename I7 = Details::Nil,  
   typename I8 = Details::Nil,  
   typename I9 = Details::Nil  
>  
class RuntimeClass : public Details::RuntimeClass<typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8, I9>::TypeT, RuntimeClassFlags<WinRt>>;  
  
template <  
   unsigned int classFlags,  
   typename I0,  
   typename I1,  
   typename I2,  
   typename I3,  
   typename I4,  
   typename I5,  
   typename I6,  
   typename I7,  
   typename I8  
>  
class RuntimeClass<RuntimeClassFlags<classFlags>, I0, I1, I2, I3, I4, I5, I6, I7, I8> : public Details::RuntimeClass<typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8>::TypeT, RuntimeClassFlags<classFlags> >;  
```  
  
#### Parámetros  
 `I0`  
 El id. de interfaz de zeroth. \(Obligatorio\)  
  
 `I1`  
 El identificador de la primera interfaz. \(Opcional\)  
  
 `I2`  
 El segundo id. de interfaz. \(Opcional\)  
  
 `I3`  
 El tercer id. de interfaz. \(Opcional\)  
  
 `I4`  
 El cuarto id. de interfaz. \(Opcional\)  
  
 `I5`  
 El identificador de la quinta interfaz. \(Opcional\)  
  
 `I6`  
 El sexto id. de interfaz \(Opcional\)  
  
 `I7`  
 El séptimo id. de interfaz. \(Opcional\)  
  
 `I8`  
 El identificador de octava interfaz. \(Opcional\)  
  
 `I9`  
 El noveno id. de interfaz \(Opcional\)  
  
 `classFlags`  
 Combinación de uno o más valores de enumeración [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) .  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[RuntimeClass::RuntimeClass \(Constructor\)](../windows/runtimeclass-runtimeclass-constructor.md)|Inicializa la instancia actual de la clase RuntimeClass.|  
|[RuntimeClass::~RuntimeClass \(Destructor\)](../windows/runtimeclass-tilde-runtimeclass-destructor.md)|Cancela la inicialización de la instancia actual de la clase RuntimeClass.|  
  
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
  
 `RuntimeClass`  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Microsoft::WRL \(Espacio de nombres\)](../windows/microsoft-wrl-namespace.md)