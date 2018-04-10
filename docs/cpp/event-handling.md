---
title: Control de eventos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], event handling
- intrinsic functions [C++], event handling
- event handling [C++], Visual C++
ms.assetid: 82de3f9a-2d88-470c-9527-8a5b54c8ced4
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4167a76d3e301f76ebba09f78abcd7e64fc7f108
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="event-handling"></a>Control de eventos
Control de eventos se admite principalmente para las clases COM (clases de C++ que implementan objetos COM, normalmente mediante clases ATL o el [coclase](../windows/coclass.md) atributo).  Para obtener más información, consulte [control de eventos en COM](../cpp/event-handling-in-com.md).  
  
 El control de eventos también se admite para las clases de C++ nativo (clases de C++ que no implementan objetos COM); sin embargo, esa compatibilidad está en desuso y se quitará en futuras versiones.  Para obtener más información, consulte [control de eventos en C++ nativo](../cpp/event-handling-in-native-cpp.md).  
  
 El control de eventos admite el uso de único subproceso y multiproceso y protege los datos de acceso multiproceso simultáneo. También permite que se deriven subclases de clases del origen de eventos o del receptor y que se admita el suministro y la recepción de eventos extendidos en la clase derivada.  
  
 Visual C++ incluye atributos y palabras clave para declarar eventos y controladores de eventos. Los atributos y las palabras clave de eventos se pueden utilizar en programas de CLR y en programas de C++ nativo.  
  
|Tema|Descripción|  
|-----------|-----------------|  
|[event_source](../windows/event-source.md)|Crea un origen de eventos.|  
|[event_receiver](../windows/event-receiver.md)|Crea un receptor de eventos (receptor).|  
|[__event](../cpp/event.md)|Declara un evento.|  
|[__raise](../cpp/raise.md)|Resalta el sitio de llamada de un evento.|  
|[__hook](../cpp/hook.md)|Asocia un método de control a un evento.|  
|[__unhook](../cpp/unhook.md)|Disocia un método de control de un evento.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)   
 [Palabras clave](../cpp/keywords-cpp.md)   
 [Ejemplos de control de eventos](http://msdn.microsoft.com/en-us/cc0287d4-f92b-4da5-85fc-a0f186e16424)