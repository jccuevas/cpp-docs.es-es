---
title: "Module::MethodReleaseNotifier::MethodReleaseNotifier (Constructor) | Microsoft Docs"
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
  - "module/Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MethodReleaseNotifier, constructor"
ms.assetid: 762e2ca4-0a92-49de-9ff5-d3efa0f067c0
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Module::MethodReleaseNotifier::MethodReleaseNotifier (Constructor)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Inicializa una nueva instancia de la clase de Module::MethodReleaseNotifier.  
  
## Sintaxis  
  
```  
  
MethodReleaseNotifier(  
   _In_ T* object,   
   _In_ void (T::* method)(),   
   bool release) throw() :  
            ReleaseNotifier(release), object_(object),   
            method_(method);  
```  
  
#### Parámetros  
 `object`  
 Un objeto cuya función miembro es un controlador de eventos.  
  
 `method`  
 La función miembro de parámetro `object` que es el controlador de eventos.  
  
 `release`  
 Especifique `true` para habilitar llamar al método subyacente de [Module::ReleaseNotifier:: Release\(\)](../windows/module-releasenotifier-release.md) ; si no, especifique `false`.  
  
## Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Module::MethodReleaseNotifier \(Clase\)](../Topic/Module::MethodReleaseNotifier%20Class.md)