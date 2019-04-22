---
title: Usar IDispEventSimpleImpl (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- IDispEventSimpleImpl class, using
ms.assetid: 8640ad1a-4bd0-40a5-b5e4-7322685d7aab
ms.openlocfilehash: 40edca3a99fb6e9d57d617e79d0bd37ebbfcd4ad
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58768569"
---
# <a name="using-idispeventsimpleimpl"></a>Usar IDispEventSimpleImpl

Cuando se usa `IDispEventSimpleImpl` para controlar eventos, tendrá que:

- Derive la clase de [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md).

- Agregar un mapa de receptores de eventos a la clase.

- Definir [_ATL_FUNC_INFO](../atl/reference/atl-func-info-structure.md) estructuras que describen los eventos.

- Agregar entradas en el mapa de receptor de eventos mediante el [macro SINK_ENTRY_INFO](reference/composite-control-macros.md#sink_entry_info) macro.

- Implemente los métodos que le interesa en el control.

- Aconsejar y desaconsejar el origen del evento.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo controlar el `DocumentChange` eventos desencadenados por la palabra **aplicación** objeto. Este evento se define como un método en el `ApplicationEvents` dispinterface.

El ejemplo proviene del [ejemplo ATLEventHandling](../overview/visual-cpp-samples.md).

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

El ejemplo se utiliza `#import` para generar los archivos de encabezado requeridos desde la biblioteca de tipos de Word. Si desea usar este ejemplo con otras versiones de Word, debe especificar el archivo dll de mso correcto. Por ejemplo, Office 2000 proporciona mso9.dll y OfficeXP proporciona mso.dll. Este código se ha simplificado de stdafx.h:

[!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventsimpleimpl_1.h)]

La única información de la biblioteca de tipos que se usa realmente en este ejemplo es el CLSID de la palabra `Application` objeto y el IID de la `ApplicationEvents` interfaz. Esta información solo se usa en tiempo de compilación.

Aparece el siguiente código en Simple.h. El código relevante se anota mediante comentarios:

[!code-cpp[NVC_ATL_EventHandlingSample#3](../atl/codesnippet/cpp/using-idispeventsimpleimpl_2.h)]

El código siguiente procede de Simple.cpp:

[!code-cpp[NVC_ATL_EventHandlingSample#4](../atl/codesnippet/cpp/using-idispeventsimpleimpl_3.cpp)]

## <a name="see-also"></a>Vea también

[Control de eventos](../atl/event-handling-and-atl.md)<br/>
[Ejemplo ATLEventHandling](../overview/visual-cpp-samples.md)
