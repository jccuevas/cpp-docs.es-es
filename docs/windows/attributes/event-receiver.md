---
title: event_receiver (C++ atributo com)
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
ms.openlocfilehash: 9653a0b5c756857d92914496b9c5c6f8aee56ebb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167087"
---
# <a name="event_receiver"></a>event_receiver

Crea un receptor de eventos (receptor).

## <a name="syntax"></a>Sintaxis

```cpp
[ event_receiver(type
   [, layout_dependent=false]) ]
```

### <a name="parameters"></a>Parámetros

*type*<br/>
Enumeración de uno de los valores siguientes:

- `native` para C/C++ Code no administrado (valor predeterminado para las clases nativas).

- `com` para código COM. Este valor requiere que se incluyan los archivos de encabezado siguientes:

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*layout_dependent*<br/>
Especifique *layout_dependent* solo si `type`=**com**. *layout_dependent* es un valor booleano:

- **true** significa que la firma de los delegados del receptor de eventos debe coincidir exactamente con la que están enlazados en el origen del evento. Los nombres de controlador del receptor de eventos deben coincidir con los nombres especificados en la interfaz de origen de eventos correspondiente. Debe utilizar `coclass` cuando *layout_dependent* sea **true**. Es ligeramente más eficaz especificar **true**.

- **false** (valor predeterminado) significa que la Convención de llamada y la clase de almacenamiento (virtual, estática y otras) no tienen que coincidir con el método de evento y los controladores. tampoco es necesario que los nombres de controlador coincidan con los nombres de método de la interfaz de origen de eventos.

## <a name="remarks"></a>Observaciones

El atributo **event_receiver** C++ especifica que la clase o estructura a la que se aplica será un receptor de eventos, utilizando el modelo C++ de eventos unificado visual.

**event_receiver** se utiliza con el atributo [event_source](event-source.md) y las palabras clave [__hook](../../cpp/hook.md) y [__unhook](../../cpp/unhook.md) . Use `event_source` para crear orígenes de eventos. Utilice **__hook** dentro de los métodos de un receptor de eventos para asociar ("enlazar") los métodos del receptor de eventos a los eventos de un origen de eventos. Utilice **__unhook** para desasociarlos.

*layout_dependent* solo se especifica para los receptores de eventos com (`type`=**com**). El valor predeterminado para *layout_dependent* es **false**.

> [!NOTE]
> Una clase o struct basada en plantilla no puede contener eventos.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**|
|**Reiterativo**|No|
|**Atributos requeridos**|`coclass` cuando *layout_dependent*=**true**|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos de compilador](compiler-attributes.md)<br/>
[event_source](event-source.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[Atributos de clase](class-attributes.md)
