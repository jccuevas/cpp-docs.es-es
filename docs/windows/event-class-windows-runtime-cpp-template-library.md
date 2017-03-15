---
title: "Event (Clase) (Biblioteca de plantillas C++ de Windows en tiempo de ejecuci&#243;n) | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Event"
dev_langs: 
  - "C++"
ms.assetid: 55dfc9fc-62d4-4bb2-9d85-5b6dd88569e8
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Event (Clase) (Biblioteca de plantillas C++ de Windows en tiempo de ejecuci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa un evento.  
  
## Sintaxis  
  
```  
class Event : public HandleT<HandleTraits::EventTraits>;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Event::Event Constructor \(Biblioteca de plantillas C\+\+ de Windows en tiempo de ejecución\)](../windows/event-event-constructor-windows-runtime-cpp-template-library.md)|Inicializa una nueva instancia de la clase Event.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Event::operator\= \(Operador\)](../windows/event-operator-assign-operator.md)|Asigna la referencia de evento especificada a la instancia de evento actual.|  
  
## Jerarquía de herencia  
 `HandleT`  
  
 `Event`  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers  
  
## Vea también  
 [Microsoft::WRL::Wrappers \(Espacio de nombres\)](../Topic/Microsoft::WRL::Wrappers%20Namespace.md)