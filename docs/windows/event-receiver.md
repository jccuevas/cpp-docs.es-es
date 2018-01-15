---
title: event_receiver | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.event_receiver
dev_langs: C++
helpviewer_keywords:
- event_receiver attribute
- event receivers
- events [C++], event receivers (sinks)
- event handling [C++], attributes
- event handling [C++], creating receiver
- event sinks, creating
- event sinks
ms.assetid: bf8fe770-3ea2-4128-b46b-166222ee4097
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 50ea26172e2f5112e760aa02d9247d07afbead2b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="eventreceiver"></a>event_receiver
Crea un receptor de eventos (receptor).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ event_receiver(  
   type   
   [, layout_dependent=false]   
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `type`  
 Enumeración de uno de los valores siguientes:  
  
-   `native`para código de C o C++ no administrado (valor predeterminado para las clases nativo).  
  
-   `com` para código COM. Este valor requiere que se incluyan los archivos de encabezado siguientes:  
  
    ```  
    #define _ATL_ATTRIBUTES  
    #include <atlbase.h>  
    #include <atlcom.h>  
    ```  
  
 **layout_dependent**  
 Especifique *layout_dependent* solo si `type` = **com**. *layout_dependent* es un valor booleano:  
  
-   **True** significa que la firma de los delegados en el receptor debe coincidir exactamente con los que está enlazados en el evento origen de eventos. Los nombres de controlador de receptor de eventos deben coincidir con los nombres especificados en la interfaz de origen de eventos importantes. Debe usar **coclase** cuando *layout_dependent* es **true**. Es ligeramente más eficaz especificar **true**.  
  
-   **false** (valor predeterminado) indica que la clase de almacenamiento y la convención de llamada (virtual, estática etc.) no tiene que coincidir con el método de evento y los controladores; ni ¿los nombres de controlador deben coincidir con los nombres de método de interfaz de origen de eventos.  
  
## <a name="remarks"></a>Comentarios  
 El **event_receiver** atributo C++ especifica que la clase o estructura a la que se aplica será un receptor de eventos, mediante el modelo unificado de eventos de Visual C++.  
  
 **event_receiver** se utiliza con la [event_source](../windows/event-source.md) atributo y el [__hook](../cpp/hook.md) y [__unhook](../cpp/unhook.md) palabras clave. Use **event_source** para crear orígenes de eventos. Use `__hook` dentro de los métodos de un receptor de eventos para asociar los métodos de receptor de eventos ("enlace") a los eventos de un origen de eventos. Use `__unhook` para anular la asociación de ellos.  
  
 *layout_dependent* sólo se especifica para los receptores de eventos COM (`type`=**com**). El valor predeterminado de *layout_dependent* es **false**.  
  
> [!NOTE]
>  Una clase o struct basada en plantilla no puede contener eventos.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**class**, `struct`|  
|**Reiterativo**|No|  
|**Atributos requeridos**|**coclase** cuando *layout_dependent*=**true**|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos de compilador](../windows/compiler-attributes.md)   
 [event_source](../windows/event-source.md)   
 [__event](../cpp/event.md)   
 [__hook](../cpp/hook.md)   
 [__unhook](../cpp/unhook.md)   
 [Atributos de clase](../windows/class-attributes.md)   
