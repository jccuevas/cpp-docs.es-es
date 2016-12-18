---
title: "Purpose of Attributes | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "attributes [C++], about attributes"
ms.assetid: 3aff8bfa-a2a3-4fcb-a2c6-1d96a2b4c68d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Purpose of Attributes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los atributos extienden C\+\+ en las direcciones no actualmente posibles sin interrumpir la estructura clásica del lenguaje.  Los atributos permiten que los proveedores \(archivos DLL independientes\) extienden la funcionalidad del lenguaje dinámicamente.  El objetivo principal de atributos es simplificar la creación de componentes COM, además de aumentar la productividad del programador de componentes.  Los atributos se pueden aplicar a casi cualquier construcción de C\+\+, como clases, miembros de datos, o funciones miembro.  A continuación se muestra un resaltado de las ventajas proporcionadas por esta nueva tecnología:  
  
-   Expone una convención de llamada familiarizado y simple.  
  
-   utiliza el código insertado, que, a diferencia de macros, es reconocido por el depurador.  
  
-   Permite la derivación fácil de clases base sin detalles de implementación pesados.  
  
-   Reemplaza una gran cantidad de código IDL requerido por un componente COM con algunos atributos concisos.  
  
 Por ejemplo, para implementar un receptor de eventos simple para una clase genérica ATL, puede aplicar el atributo de [event\_receiver](../windows/event-receiver.md) a una clase concreta como `CMyReceiver`.  El atributo de **event\_receiver** es a compilados por el compilador de Visual C\+\+, que inserta el código adecuado en el archivo objeto.  
  
```  
[event_receiver(com)]  
class CMyReceiver   
{  
   void handler1(int i) { ... }  
   void handler2(int i, float j) { ... }  
}  
```  
  
 Puede configurar los métodos `handler1` y `handler2` de **CMyReceiver** para controlar eventos \(mediante la función intrínseca [\_\_hook](../cpp/hook.md)\) de un origen de eventos, que puede crear utilizando [event\_source](../windows/event-source.md).  
  
## Vea también  
 [Concepts](../windows/attributed-programming-concepts.md)