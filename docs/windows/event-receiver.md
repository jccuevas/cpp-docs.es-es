---
title: "event_receiver | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.event_receiver"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "event_receiver attribute"
  - "event receivers"
  - "events [C++], event receivers (sinks)"
  - "event handling [C++], attributes"
  - "event handling [C++], creating receiver"
  - "event sinks, creating"
  - "event sinks"
ms.assetid: bf8fe770-3ea2-4128-b46b-166222ee4097
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# event_receiver
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Crea un receptor de eventos \(receptor\).  
  
## Sintaxis  
  
```  
  
      [ event_receiver(  
   type   
   [, layout_dependent=false]   
) ]  
```  
  
#### Parámetros  
 `type`  
 Una enumeración de uno de los siguientes valores:  
  
-   `native` para código no administrado de C\/C\+\+ \(valor predeterminado para las clases nativas\).  
  
-   `com` para código COM.  Este valor debe incluir los archivos de encabezado siguientes:  
  
    ```  
    #define _ATL_ATTRIBUTES  
    #include <atlbase.h>  
    #include <atlcom.h>  
    ```  
  
 **layout\_dependent**  
 Especifique *layout\_dependent* sólo si `type`\=**COM**.  *layout\_dependent* es un valor booleano:  
  
-   **TRUE** significa que la firma de los delegados en el receptor de eventos debe coincidir exactamente con los que se enlazan en el origen de evento.  Los nombres de controlador de receptor de eventos deben coincidir con los nombres especificados en la interfaz pertinente del origen de eventos.  Debe utilizar **CoClass** cuando *es layout\_dependent* es **TRUE**.  Es ligeramente más eficaz especificar **TRUE**.  
  
-   **Falso** \(valor predeterminado\) significa que la convención de llamada y la clase de almacenamiento \(virtual, estático, etc.\) no tienen que coincidir el método del evento y controladores; ni tampoco el controlador que los nombres deben coincidir con los nombres de interfaz del origen de eventos.  
  
## Comentarios  
 El atributo de **event\_receiver** C\+\+ especifica que la clase o la estructura a las que se aplica se receptor de eventos, mediante el modelo de eventos de Visual C\+\+.  
  
 **event\_receiver** se utiliza con el atributo de [event\_source](../windows/event-source.md) y palabras clave de [\_\_hook](../cpp/hook.md) y de [\_\_unhook](../cpp/unhook.md) .  uso **event\_source** de crear orígenes de eventos.  Utilice `__hook` dentro de los métodos de un receptor de eventos para asociar \(“enlazar”\) método de receptor de eventos a los eventos de un origen de eventos.  uso `__unhook` de disociarlos.  
  
 *layout\_dependent* solamente se especifica para los receptores de eventos COM \(`type`\=**COM**\).  El valor predeterminado para *layout\_dependent* es **Falso**.  
  
> [!NOTE]
>  Una clase o struct basada en plantilla no puede contener eventos.  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase**, `struct`|  
|**repetible**|No|  
|**Atributos necesarios**|**CoClass** cuando layout\_dependent\=**TRUE**|  
|**Atributos no válidos**|None|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [Compiler Attributes](../windows/compiler-attributes.md)   
 [event\_source](../windows/event-source.md)   
 [\_\_event](../cpp/event.md)   
 [\_\_hook](../cpp/hook.md)   
 [\_\_unhook](../cpp/unhook.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)