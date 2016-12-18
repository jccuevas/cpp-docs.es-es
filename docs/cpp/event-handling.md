---
title: "Control de eventos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "atributos [C++], control de eventos"
  - "control de eventos, Visual C++"
  - "funciones intrínsecas, control de eventos"
ms.assetid: 82de3f9a-2d88-470c-9527-8a5b54c8ced4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Control de eventos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El control de eventos se admite principalmente para las clases COM \(las clases de C\+\+ que implementan objetos COM, normalmente mediante clases ATL o el atributo [coclass](../windows/coclass.md)\).  Para obtener más información, vea [Control de eventos en COM](../cpp/event-handling-in-com.md).  
  
 El control de eventos también se admite para las clases de C\+\+ nativo \(clases de C\+\+ que no implementan objetos COM\); sin embargo, esa compatibilidad está desusada y se quitará en futuras versiones.  Para obtener más información, vea [Control de eventos en C\+\+ nativo](../cpp/event-handling-in-native-cpp.md).  
  
 El control de eventos admite el uso de único subproceso y multiproceso y protege los datos de acceso multiproceso simultáneo.  También permite que se deriven subclases de clases del origen de eventos o del receptor y que se admita el suministro y la recepción de eventos extendidos en la clase derivada.  
  
 Visual C\+\+ incluye atributos y palabras clave para declarar eventos y controladores de eventos.  Los atributos y las palabras clave de eventos se pueden utilizar en programas de CLR y en programas de C\+\+ nativo.  
  
|Tema|Descripción|  
|----------|-----------------|  
|[event\_source](../windows/event-source.md)|Crea un origen de eventos.|  
|[event\_receiver](../windows/event-receiver.md)|Crea un receptor de eventos \(receptor\).|  
|[\_\_event](../cpp/event.md)|Declara un evento.|  
|[\_\_raise](../cpp/raise.md)|Resalta el sitio de llamada de un evento.|  
|[\_\_hook](../cpp/hook.md)|Asocia un método de control a un evento.|  
|[\_\_unhook](../cpp/unhook.md)|Disocia un método de control de un evento.|  
  
## Vea también  
 [Referencia de lenguaje C\+\+](../cpp/cpp-language-reference.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [Event Handling Samples](http://msdn.microsoft.com/es-es/cc0287d4-f92b-4da5-85fc-a0f186e16424)