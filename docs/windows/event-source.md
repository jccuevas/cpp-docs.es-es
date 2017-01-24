---
title: "event_source | Microsoft Docs"
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
  - "vc-attr.event_source"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "control de eventos, atributos"
  - "registros de eventos, origen del evento"
  - "orígenes del evento, crear"
  - "event_source (atributo)"
  - "orígenes del evento"
  - "control de eventos, crear un origen del evento"
ms.assetid: 0983e36a-6127-4fbb-8a22-8dfec6564c16
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# event_source
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Crea un origen de eventos.  
  
## Sintaxis  
  
```  
  
       [ event_source(  
       type,  
optimize=[speed | size],  
decorate=[true | false]) ]  
```  
  
#### Parámetros  
 `type`  
 Enumeración de uno de los valores siguientes:  
  
-   `native` para código de C\/C\+\+ no administrado \(valor predeterminado para las clases no administradas\).  
  
-   `com` para código COM. Debe usar `coclass` cuando `type`\=`com`. Este valor requiere que se incluyan los archivos de encabezado siguientes:  
  
    ```  
    #define _ATL_ATTRIBUTES  
    #include <atlbase.h>  
    #include <atlcom.h>  
    ```  
  
 **optimize**  
 Cuando `type` es **native**, puede especificar **optimize\=size** para indicar que hay 4 bytes de almacenamiento \(mínimo\) para todos los eventos de una clase u **optimize\=speed** \(valor predeterminado\) para indicar que hay 4 \* \(número de eventos\) bytes de almacenamiento.  
  
 **decorate**  
 Cuando `type` es **native**, puede especificar **decorate\=false** para indicar que el nombre expandido del archivo combinado \(.mrg\) no debe incluir el nombre de la clase envolvente.[\/Fx](../build/reference/fx-merge-injected-code.md) permite generar archivos .mrg.**decorate\=false**, que es el valor predeterminado, da lugar a nombres de tipo completo en el archivo combinado.  
  
## Comentarios  
 El atributo de C\+\+ **event\_source** especifica que la clase o estructura a la que se aplica será un origen del evento.  
  
 **event\_source** se usa junto con el atributo [event\_receiver](../windows/event-receiver.md) y la palabra clave [\_\_event](../cpp/event.md). Use **event\_receiver** para crear receptores de eventos. Use `__event` en métodos del origen del evento para especificar dichos métodos como eventos.  
  
> [!NOTE]
>  Una clase o struct basada en plantilla no puede contener eventos.  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**class**, `struct`|  
|**Reiterativo**|No|  
|**Atributos requeridos**|**coclass** cuando `type`\=**com**|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [Compiler Attributes](../windows/compiler-attributes.md)   
 [event\_receiver](../windows/event-receiver.md)   
 [\_\_event](../cpp/event.md)   
 [\_\_hook](../cpp/hook.md)   
 [\_\_unhook](../cpp/unhook.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)