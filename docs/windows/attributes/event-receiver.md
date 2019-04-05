---
title: event_receiver (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.event_receiver
helpviewer_keywords:
- event_receiver attribute
- event receivers
- events [C++], event receivers (sinks)
- event handling [C++], attributes
- event handling [C++], creating receiver
- event sinks, creating
- event sinks
ms.assetid: bf8fe770-3ea2-4128-b46b-166222ee4097
ms.openlocfilehash: 81a3ec88c336ddeb550f133e657854b3b6f89d96
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023300"
---
# <a name="eventreceiver"></a>event_receiver

Crea un receptor de eventos (receptor).

## <a name="syntax"></a>Sintaxis

```cpp
[ event_receiver(type
   [, layout_dependent=false]) ]
```

### <a name="parameters"></a>Parámetros

*type*<br/>
Enumeración de uno de los valores siguientes:

- `native` para código de C o C++ administrado (valor predeterminado para las clases nativas).

- `com` para código COM. Este valor requiere que se incluyan los archivos de encabezado siguientes:

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*layout_dependent*<br/>
Especificar *layout_dependent* solo si `type` = **com**. *layout_dependent* es un valor booleano:

- **True** significa que la firma de los delegados en el receptor debe coincidir exactamente con aquellos a los que está enlazados en el evento origen de eventos. Los nombres de controlador de eventos receptor deben coincidir con los nombres especificados en la interfaz de origen de evento pertinente. Debe usar `coclass` cuando *layout_dependent* es **true**. Es ligeramente más eficaz especificar **true**.

- **false** (valor predeterminado) indica que la clase de almacenamiento y la convención de llamada (virtual, estática etc.) no es necesario para que coincida con el método de evento y los controladores; ni necesitan los nombres de controlador para que coincida con los nombres de método de interfaz de origen de eventos.

## <a name="remarks"></a>Comentarios

El **event_receiver** atributo de C++ especifica que la clase o estructura a la que se aplica será un receptor de eventos, mediante el modelo de evento unificado de Visual C++.

**event_receiver** se usa con el [event_source](event-source.md) atributo y el [__hook](../../cpp/hook.md) y [__unhook](../../cpp/unhook.md) palabras clave. Use `event_source` para crear orígenes de eventos. Use **__hook** dentro de los métodos de un receptor de eventos para asociar los métodos de receptor de eventos ("enlace") para los eventos de un origen de eventos. Use **__unhook** para desasociar de ellos.

*layout_dependent* solo se especifica para receptores de eventos COM (`type`=**com**). El valor predeterminado para *layout_dependent* es **false**.

> [!NOTE]
> Una clase o struct basada en plantilla no puede contener eventos.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**|
|**Reiterativo**|No|
|**Atributos requeridos**|`coclass` Cuando *layout_dependent*=**true**|
|**Atributos no válidos**|Ninguna|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos de compilador](compiler-attributes.md)<br/>
[event_source](event-source.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[Atributos de clase](class-attributes.md)