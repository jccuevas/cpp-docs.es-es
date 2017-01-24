---
title: "HandleT::HandleT (Constructor) | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HandleT::HandleT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "HandleT, constructor"
ms.assetid: 4def6891-7e53-46f1-a197-a80e10744dd5
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HandleT::HandleT (Constructor)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Inicializa una nueva instancia de la clase de HandleT.  
  
## Sintaxis  
  
```  
explicit HandleT(  
   typename HandleTraits::Type h =   
      HandleTraits::GetInvalidValue()  
);  
  
HandleT(  
   _Inout_ HandleT&& h  
);  
```  
  
#### Parámetros  
 `h`  
 Un identificador.  
  
## Comentarios  
 El primer constructor inicializa un objeto de HandleT que no es un identificador válido a un objeto.  El segundo constructor crea un nuevo objeto de HandleT de parámetro `h`.  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers  
  
## Vea también  
 [HandleT \(Clase\)](../Topic/HandleT%20Class.md)