---
title: Usar IDispEventSimpleImpl (ATL)
ms.date: 08/19/2019
helpviewer_keywords:
- IDispEventSimpleImpl class, using
ms.assetid: 8640ad1a-4bd0-40a5-b5e4-7322685d7aab
ms.openlocfilehash: 8a5e64093d2687efc6c6c5e9b0ce89402d2b99a4
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630586"
---
# <a name="using-idispeventsimpleimpl"></a>Usar IDispEventSimpleImpl

Al usar `IDispEventSimpleImpl` para controlar eventos, deberá:

- Derive la clase de [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md).

- Agregue una asignación de receptor de eventos a la clase.

- Defina las estructuras [_ATL_FUNC_INFO](../atl/reference/atl-func-info-structure.md) que describen los eventos.

- Agregue entradas a la asignación del receptor de eventos mediante la macro [SINK_ENTRY_INFO](reference/composite-control-macros.md#sink_entry_info) .

- Implemente los métodos que le interesa controlar.

- Aconseje y desaconseje el origen del evento.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo controlar el `DocumentChange` evento desencadenado por el objeto de **aplicación** de Word. Este evento se define como un método en la `ApplicationEvents` interfaz dispinterface.

El ejemplo es del [ejemplo ATLEventHandling](../overview/visual-cpp-samples.md).

```cpp
[ uuid(000209F7-0000-0000-C000-000000000046), hidden ]
dispinterface ApplicationEvents {
properties:
methods:
    [id(0x00000001), restricted, hidden]
    void Startup();

    [id(0x00000002)]
    void Quit();

    [id(0x00000003)]
    void DocumentChange();
};
```

En el ejemplo `#import` se usa para generar los archivos de encabezado necesarios de la biblioteca de tipos de Word. Si desea utilizar este ejemplo con otras versiones de Word, debe especificar el archivo dll MSO correcto. Por ejemplo, Office 2000 proporciona mso9. dll y OfficeXP proporciona mso. dll. Este código se simplifica de *PCH. h* (*stdafx. h* en Visual Studio 2017 y versiones anteriores):

[!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventsimpleimpl_1.h)]

La única información de la biblioteca de tipos que se usa realmente en este ejemplo es el CLSID `Application` del objeto de Word y el `ApplicationEvents` IID de la interfaz. Esta información solo se utiliza en tiempo de compilación.

El código siguiente aparece en simple. h. Los comentarios indican el código relevante:

[!code-cpp[NVC_ATL_EventHandlingSample#3](../atl/codesnippet/cpp/using-idispeventsimpleimpl_2.h)]

El código siguiente es de simple. cpp:

[!code-cpp[NVC_ATL_EventHandlingSample#4](../atl/codesnippet/cpp/using-idispeventsimpleimpl_3.cpp)]

## <a name="see-also"></a>Vea también

[Control de eventos](../atl/event-handling-and-atl.md)<br/>
[Ejemplo de ATLEventHandling](../overview/visual-cpp-samples.md)
