---
title: "messages (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "messages"
  - "xlocmes/std::messages"
  - "std.messages"
  - "std::messages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "messages (clase)"
ms.assetid: c4c71f40-4f24-48ab-9f7c-daccd8d5bd83
caps.latest.revision: 18
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# messages (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un objeto que puede actuar como una faceta de configuración regional para recuperar mensajes traducidos y adaptados de un catálogo de mensajes internacionalizados para una configuración regional concreta.  
  
 Actualmente, mientras se implementa la clase messages, no hay mensajes.  
  
## Sintaxis  
  
```  
template <class CharType>  
   class messages : public messages_base;  
```  
  
#### Parámetros  
 `CharType`  
 Tipo usado dentro de un programa para codificar los caracteres de una configuración regional.  
  
## Comentarios  
 Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero. El primer intento para tener acceso a su valor almacenado almacena un valor positivo único en **identificador**  
  
 Básicamente esta faceta abre un catálogo de mensajes definidos en la clase base messages\_base, recupera la información necesaria y cierra el catálogo.  
  
### Constructores  
  
|||  
|-|-|  
|[mensajes](../Topic/messages::messages.md)|Función constructor de la faceta de mensajes.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[char\_type](../Topic/messages::char_type.md)|Tipo de carácter usado para mostrar mensajes.|  
|[string\_type](../Topic/messages::string_type.md)|Un tipo que describe una cadena de tipo `basic_string` que contiene caracteres de tipo `CharType`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[cerrar](../Topic/messages::close.md)|Cierra el catálogo de mensajes.|  
|[do\_close](../Topic/messages::do_close.md)|Una función virtual llamada para perder el catálogo de mensajes.|  
|[do\_get](../Topic/messages::do_get.md)|Una función virtual llamada para recuperar el catálogo de mensajes.|  
|[do\_open](../Topic/messages::do_open.md)|Una función virtual llamada para abrir el catálogo de mensajes.|  
|[obtener](../Topic/messages::get.md)|Recupera el catálogo de mensajes.|  
|[abrir](../Topic/messages::open.md)|Abre el catálogo de mensajes.|  
  
## Requisitos  
 **Encabezado:** \<locale\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<locale\>](../standard-library/locale.md)   
 [messages\_base \(Clase\)](../standard-library/messages-base-class.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)