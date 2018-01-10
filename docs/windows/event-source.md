---
title: event_source | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.event_source
dev_langs: C++
helpviewer_keywords:
- event handling, attributes
- event logs, event source
- event sources, creating
- event_source attribute
- event sources
- event handling, creating event source
ms.assetid: 0983e36a-6127-4fbb-8a22-8dfec6564c16
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 05371b5c2d9acd091adcbdf81d2994f205e36ef7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="eventsource"></a>event_source
Crea un origen de eventos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ event_source(  
   type,  
   optimize=[speed | size],  
   decorate=[true | false]  
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `type`  
 Enumeración de uno de los valores siguientes:  
  
-   `native` para código de C/C++ no administrado (valor predeterminado para las clases no administradas).  
  
-   `com` para código COM. Debe usar `coclass` cuando `type`=`com`. Este valor requiere que se incluyan los archivos de encabezado siguientes:  
  
    ```  
    #define _ATL_ATTRIBUTES  
    #include <atlbase.h>  
    #include <atlcom.h>  
    ```  
  
 **optimize**  
 Cuando `type` es **native**, puede especificar **optimize=size**para indicar que hay 4 bytes de almacenamiento (mínimo) para todos los eventos de una clase u **optimize=speed** (valor predeterminado) para indicar que hay 4 * (número de eventos) bytes de almacenamiento.  
  
 **decorate**  
 Cuando `type` es **native**, puede especificar **decorate=false**para indicar que el nombre expandido del archivo combinado (.mrg) no debe incluir el nombre de la clase envolvente. [/Fx](../build/reference/fx-merge-injected-code.md) permite generar archivos .mrg. **decorate=false**, que es el valor predeterminado, da lugar a nombres de tipo completo en el archivo combinado.  
  
## <a name="remarks"></a>Comentarios  
 El atributo de C++ **event_source** especifica que la clase o estructura a la que se aplica será un origen del evento.  
  
 **event_source** se usa junto con el atributo [event_receiver](../windows/event-receiver.md) y la palabra clave [__event](../cpp/event.md) . Use **event_receiver** para crear receptores de eventos. Use `__event` en métodos del origen del evento para especificar dichos métodos como eventos.  
  
> [!NOTE]
>  Una clase o struct basada en plantilla no puede contener eventos.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**class**, `struct`|  
|**Reiterativo**|No|  
|**Atributos requeridos**|**coclass** cuando `type`=**com**|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos de compilador](../windows/compiler-attributes.md)   
 [event_receiver](../windows/event-receiver.md)   
 [__event](../cpp/event.md)   
 [__hook](../cpp/hook.md)   
 [__unhook](../cpp/unhook.md)   
 [Atributos de clase](../windows/class-attributes.md)   
