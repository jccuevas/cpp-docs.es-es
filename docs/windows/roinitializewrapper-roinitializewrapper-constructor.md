---
title: "RoInitializeWrapper::RoInitializeWrapper (Constructor) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper"
dev_langs: 
  - "C++"
ms.assetid: c6f7fb07-14af-4574-9135-cea164607f30
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RoInitializeWrapper::RoInitializeWrapper (Constructor)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Inicializa una nueva instancia de la clase de RoInitializeWrapper.  
  
## Sintaxis  
  
```cpp  
RoInitializeWrapper(  
   RO_INIT_TYPE flags)  
  
```  
  
#### Parámetros  
 `flags`  
 Una de las enumeraciones de RO\_INIT\_TYPE, que especifica la compatibilidad proporcionada por [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)].  
  
## Comentarios  
 La clase de RoInitializeWrapper invoca Windows::Foundation::Initialize \(*flags*\).  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers  
  
## Vea también  
 [HandleT \(Clase\)](../Topic/HandleT%20Class.md)