---
title: Usar IDispEventImpl (ATL)
ms.date: 08/19/2019
helpviewer_keywords:
- IDispEventImpl class, using
ms.assetid: 82d53b61-9d0d-45c5-aff9-2fafa468a9ca
ms.openlocfilehash: 9684781ba99d96e2c58d450ee0ff892374e33aef
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630595"
---
# <a name="using-idispeventimpl"></a>Usar IDispEventImpl

Al usar `IDispEventImpl` para controlar eventos, deberá:

- Derive la clase de [IDispEventImpl](../atl/reference/idispeventimpl-class.md).

- Agregue una asignación de receptor de eventos a la clase.

- Agregue entradas a la asignación del receptor de eventos mediante la macro [SINK_ENTRY](reference/composite-control-macros.md#sink_entry) o [SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex) .

- Implemente los métodos que le interesa controlar.

- Aconseje y desaconseje el origen del evento.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo controlar `DocumentChange` el evento desencadenado por el objeto de **aplicación** de Word. Este evento se define como un método en la `ApplicationEvents` interfaz dispinterface.

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

[!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventimpl_1.h)]

El código siguiente aparece en NotSoSimple. h. Los comentarios indican el código relevante:

[!code-cpp[NVC_ATL_EventHandlingSample#2](../atl/codesnippet/cpp/using-idispeventimpl_2.h)]

## <a name="see-also"></a>Vea también

[Control de eventos](../atl/event-handling-and-atl.md)<br/>
[Ejemplo de ATLEventHandling](../overview/visual-cpp-samples.md)
