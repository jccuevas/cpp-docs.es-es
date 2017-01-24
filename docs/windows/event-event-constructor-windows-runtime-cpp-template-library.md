---
title: "Event::Event Constructor (Biblioteca de plantillas C++ de Windows en tiempo de ejecuci&#243;n) | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Event::Event"
dev_langs: 
  - "C++"
ms.assetid: 21495297-9612-4095-9256-16e168cc0021
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Event::Event Constructor (Biblioteca de plantillas C++ de Windows en tiempo de ejecuci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Inicializa una nueva instancia de la clase Event.  
  
## Sintaxis  
  
```  
explicit Event(  
   HANDLE h = HandleT::Traits::GetInvalidValue()  
);  
WRL_NOTHROW Event(  
   _Inout_ Event&& h  
);  
```  
  
#### Parámetros  
 `h`  
 Identificador para un evento.  De forma predeterminada, `h` se inicializa como `nullptr`.  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers  
  
## Vea también  
 [Event \(Clase\) \(Biblioteca de plantillas C\+\+ de Windows en tiempo de ejecución\)](../windows/event-class-windows-runtime-cpp-template-library.md)