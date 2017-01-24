---
title: "CreateClassFactory (Funci&#243;n) | Microsoft Docs"
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
  - "module/Microsoft::WRL::Details::CreateClassFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateClassFactory (función)"
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CreateClassFactory (Funci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Crea un generador que genera instancias de la clase especificada.  
  
## Sintaxis  
  
```cpp  
  
template<typename Factory>  
inline HRESULT STDMETHODCALLTYPE CreateClassFactory(  
   _In_ unsigned int *flags,   
   _In_ const CreatorMap* entry,   
   REFIID riid,   
   _Outptr_ IUnknown **ppFactory  
) throw();  
  
```  
  
#### Parámetros  
 `flags`  
 Combinación de uno o más valores de enumeración [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) .  
  
 `entry`  
 Puntero a [CreatorMap](../windows/creatormap-structure.md) que contiene la inicialización y la información de registro sobre el parámetro `riid`.  
  
 `riid`  
 Referencia a un identificador de interfaz  
  
 `ppFactory`  
 Si esta operación finaliza correctamente, un puntero a un generador de clases.  
  
## Valor devuelto  
 S\_OK si correctamente; si no, un HRESULT que indica el error.  
  
## Comentarios  
 Se produce un error validar si el parámetro `Factory` de plantilla no se deriva de la interfaz IClassFactory.  
  
## Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Microsoft::WRL::Wrappers::Details \(Espacio de nombres\)](../windows/microsoft-wrl-wrappers-details-namespace.md)