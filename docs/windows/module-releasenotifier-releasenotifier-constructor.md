---
title: "Module::ReleaseNotifier::ReleaseNotifier (Constructor) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ReleaseNotifier, constructor"
ms.assetid: 889a3c9a-2366-44a1-ba7d-a59c1885e7f3
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# Module::ReleaseNotifier::ReleaseNotifier (Constructor)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Inicializa una nueva instancia de la clase de Module::ReleaseNotifier.  
  
## Sintaxis  
  
```cpp  
ReleaseNotifier(bool release) throw();  
```  
  
#### Parámetros  
 `release`  
 `true` para eliminar esta instancia cuando se llama al método release; `false` para no eliminar esta instancia.  
  
## Excepciones  
  
## Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Module::ReleaseNotifier \(Clase\)](../Topic/Module::ReleaseNotifier%20Class.md)