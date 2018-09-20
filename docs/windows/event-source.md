---
title: event_source | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.event_source
dev_langs:
- C++
helpviewer_keywords:
- event handling, attributes
- event logs, event source
- event sources, creating
- event_source attribute
- event sources
- event handling, creating event source
ms.assetid: 0983e36a-6127-4fbb-8a22-8dfec6564c16
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d2dfcf61ced958519e7255bd241d3c0ea911824e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408926"
---
# <a name="eventsource"></a>event_source

Crea un origen de eventos.

## <a name="syntax"></a>Sintaxis

```cpp
[ event_source(
   type,
   optimize=[speed | size],
   decorate=[true | false]
) ]
```

### <a name="parameters"></a>Parámetros

*type*<br/>
Enumeración de uno de los valores siguientes:

- `native` para código de C/C++ no administrado (valor predeterminado para las clases no administradas).

- `com` para código COM. Debe usar `coclass` cuando `type`=`com`. Este valor requiere que se incluyan los archivos de encabezado siguientes:

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*optimize*<br/>
Cuando *tipo* es `native`, puede especificar `optimize=size`para indicar que hay 4 bytes de almacenamiento (mínimo) para todos los eventos en una clase o `optimize=speed` (predeterminado) para indicar que hay 4 * (número de eventos) bytes de almacenamiento.

*Decore*<br/>
Cuando *tipo* es `native`, puede especificar `decorate=false`para indicar que el nombre expandido en el archivo combinado (.mrg) no debe incluir el nombre de la clase envolvente. [/Fx](../build/reference/fx-merge-injected-code.md) permite generar archivos .mrg. `decorate=false`, que es el valor predeterminado, se crean nombres de tipo completo en el archivo combinado.

## <a name="remarks"></a>Comentarios

El atributo de C++ **event_source** especifica que la clase o estructura a la que se aplica será un origen del evento.

**event_source** se usa junto con el atributo [event_receiver](../windows/event-receiver.md) y la palabra clave [__event](../cpp/event.md) . Use `event_receiver` en crear receptores de eventos. Use **__event** en métodos dentro del origen de eventos para especificar dichos métodos como eventos.

> [!NOTE]
> Una clase o struct basada en plantilla no puede contener eventos.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**|
|**Reiterativo**|No|
|**Atributos requeridos**|**coclase** cuando `type`=`com`|
|**Atributos no válidos**|Ninguna|

Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos de compilador](../windows/compiler-attributes.md)<br/>
[event_receiver](../windows/event-receiver.md)<br/>
[__event](../cpp/event.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__unhook](../cpp/unhook.md)<br/>
[Atributos de clase](../windows/class-attributes.md)  