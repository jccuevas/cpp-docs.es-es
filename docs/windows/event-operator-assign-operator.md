---
title: "Event::operator= (Operador) | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Event::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator= (operador)"
ms.assetid: d8fe9820-8856-4899-9553-56226bdc4945
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Event::operator= (Operador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Asigna la referencia de evento especificada a la instancia de evento actual.  
  
## Sintaxis  
  
```  
WRL_NOTHROW Event& operator=(  
   _Inout_ Event&& h  
);  
```  
  
#### Parámetros  
 `h`  
 Una rvalue\- referencia a una instancia de evento.  
  
## Valor devuelto  
 Un puntero a la instancia de suceso actual.  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers  
  
## Vea también  
 [Event \(Clase\) \(Biblioteca de plantillas C\+\+ de Windows en tiempo de ejecución\)](../windows/event-class-windows-runtime-cpp-template-library.md)