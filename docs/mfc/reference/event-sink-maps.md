---
title: Mapas de receptor de eventos
ms.date: 11/04/2016
helpviewer_keywords:
- event sink maps [MFC]
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
ms.openlocfilehash: 731ed2403aae3332e81702673d1181e9e52399a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365729"
---
# <a name="event-sink-maps"></a>Mapas de receptor de eventos

Cuando un control OLE incrustado desencadena un evento, el contenedor del control recibe el evento mediante un mecanismo, denominado "mapa de receptores de eventos", proporcionado por MFC. Este mapa de receptor de eventos designa funciones de controlador para cada evento específico, así como parámetros de esos eventos. Para obtener más información sobre los mapas de receptores de eventos, vea el artículo Contenedores de [controles ActiveX](../../mfc/activex-control-containers.md).

### <a name="event-sink-maps"></a>Mapas de receptor de eventos

|||
|-|-|
|[BEGIN_EVENTSINK_MAP](#begin_eventsink_map)|Inicia la definición de un mapa de receptores de eventos.|
|[DECLARE_EVENTSINK_MAP](#declare_eventsink_map)|Declara un mapa de receptor es de eventos.|
|[END_EVENTSINK_MAP](#end_eventsink_map)|Finaliza la definición de un mapa de receptores de eventos.|
|[ON_EVENT](#on_event)|Define un controlador de eventos para un evento específico.|
|[ON_EVENT_RANGE](#on_event_range)|Define un controlador de eventos para un evento específico desencadenado desde un conjunto de controles OLE.|
|[ON_EVENT_REFLECT](#on_event_reflect)|Recibe eventos desencadenados por el control antes de que los controle el contenedor del control.|
|[ON_PROPNOTIFY](#on_propnotify)|Define un controlador para controlar las notificaciones de propiedad de un control OLE.|
|[ON_PROPNOTIFY_RANGE](#on_propnotify_range)|Define un controlador para controlar las notificaciones de propiedades de un conjunto de controles OLE.|
|[ON_PROPNOTIFY_REFLECT](#on_propnotify_reflect)|Recibe notificaciones de propiedad enviadas por el control antes de que las controle el contenedor del control.|

## <a name="begin_eventsink_map"></a><a name="begin_eventsink_map"></a>BEGIN_EVENTSINK_MAP

Comienza la definición del mapa del receptor de eventos.

```
BEGIN_EVENTSINK_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
Especifica el nombre de la clase de control cuyo mapa de receptor de eventos es.

*baseClass*<br/>
Especifica el nombre de la clase base de *theClass*.

### <a name="remarks"></a>Observaciones

En el archivo de implementación (.cpp) que define las funciones miembro de la clase, inicie el mapa del receptor de eventos con la macro BEGIN_EVENTSINK_MAP y, a continuación, agregue entradas de macro para cada evento que se notificará y complete el mapa del receptor de eventos con la macro END_EVENTSINK_MAP.

Para obtener más información sobre las asignaciones de receptores de eventos y los contenedores de controles OLE, vea el artículo Contenedores de [controles ActiveX](../../mfc/activex-control-containers.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="declare_eventsink_map"></a><a name="declare_eventsink_map"></a>DECLARE_EVENTSINK_MAP

Un contenedor OLE puede proporcionar un mapa de receptor de eventos para especificar los eventos de los que se notificará al contenedor.

```
DECLARE_EVENTSINK_MAP()
```

### <a name="remarks"></a>Observaciones

Utilice la macro DECLARE_EVENTSINK_MAP al final de la declaración de clase. Luego, en el archivo . CPP que define las funciones miembro para la clase, utilice la macro de BEGIN_EVENTSINK_MAP, entradas de macro para cada uno de los eventos que se notificarán y la macro END_EVENTSINK_MAP para declarar el final de la lista de receptores de eventos.

Para obtener más información sobre los mapas de receptores de eventos, vea el artículo Contenedores de [controles ActiveX](../../mfc/activex-control-containers.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

## <a name="end_eventsink_map"></a><a name="end_eventsink_map"></a>END_EVENTSINK_MAP

Finaliza la definición del mapa del receptor de eventos.

```
END_EVENTSINK_MAP()
```

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="on_event"></a><a name="on_event"></a>ON_EVENT

Utilice la macro ON_EVENT para definir una función de controlador de eventos para un evento desencadenado por un control OLE.

```
ON_EVENT(theClass, id, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
La clase a la que pertenece este mapa de receptores de eventos.

*id*<br/>
El identificador de control del control OLE.

*dispid*<br/>
El identificador de envío del evento desencadenado por el control.

*pfnHandler*<br/>
Puntero a una función miembro que controla el evento. Esta función debe tener un tipo de valor devuelto BOOL y tipos de parámetro que coincidan con los parámetros del evento (consulte *vtsParams*). La función debe devolver TRUE para indicar que se controló el evento; de lo contrario FALSO.

*vtsParams*<br/>
Secuencia de **VTS_** constantes que especifica los tipos de los parámetros del evento. Estas son las mismas constantes que se utilizan en las entradas del mapa de distribución, como DISP_FUNCTION.

### <a name="remarks"></a>Observaciones

El argumento *vtsParams* es una lista de valores separados por espacios de las constantes **VTS_.** Uno o varios de estos valores separados por espacios (no comas) especifican la lista de parámetros de la función. Por ejemplo:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

especifica una lista que contiene un entero corto seguido de un BOOL.

Para obtener una lista de las constantes **VTS_,** consulte [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="on_event_range"></a><a name="on_event_range"></a>ON_EVENT_RANGE

Utilice la macro ON_EVENT_RANGE para definir una función de controlador de eventos para un evento desencadenado por cualquier control OLE que tenga un identificador de control dentro de un intervalo contiguo de identificadores.

```
ON_EVENT_RANGE(theClass, idFirst, idLast, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
La clase a la que pertenece este mapa de receptores de eventos.

*idFirst*<br/>
El identificador de control del primer control OLE en el intervalo.

*idLast*<br/>
El identificador de control del último control OLE del intervalo.

*dispid*<br/>
El identificador de envío del evento desencadenado por el control.

*pfnHandler*<br/>
Puntero a una función miembro que controla el evento. Esta función debe tener un tipo de valor devuelto BOOL, un primer parámetro de tipo UINT (para el identificador de control) y tipos de parámetros adicionales que coincidan con los parámetros del evento (consulte *vtsParams*). La función debe devolver TRUE para indicar que se controló el evento; de lo contrario FALSO.

*vtsParams*<br/>
Secuencia de **VTS_** constantes que especifica los tipos de los parámetros del evento. La primera constante debe ser de tipo VTS_I4, para el identificador de control. Estas son las mismas constantes que se utilizan en las entradas del mapa de distribución, como DISP_FUNCTION.

### <a name="remarks"></a>Observaciones

El argumento *vtsParams* es una lista de valores separados por espacios de las constantes **VTS_.** Uno o varios de estos valores separados por espacios (no comas) especifican la lista de parámetros de la función. Por ejemplo:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

especifica una lista que contiene un entero corto seguido de un BOOL.

Para obtener una lista de las constantes **VTS_,** consulte [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un controlador de eventos, para el MouseDown eventos, implementado para tres controles (IDC_MYCTRL1 a través de IDC_MYCTRL3). La función `OnRangeMouseDown`de controlador de eventos, , se `CMyDlg`declara en el archivo de encabezado de la clase de cuadro de diálogo ( ) como:

[!code-cpp[NVC_MFCAutomation#12](../../mfc/codesnippet/cpp/event-sink-maps_2.h)]

El código siguiente se define en el archivo de implementación de la clase de cuadro de diálogo.

[!code-cpp[NVC_MFCAutomation#13](../../mfc/codesnippet/cpp/event-sink-maps_3.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="on_event_reflect"></a><a name="on_event_reflect"></a>ON_EVENT_REFLECT

El ON_EVENT_REFLECT macro, cuando se usa en el mapa del receptor de eventos de la clase contenedora de un control OLE, recibe eventos desencadenados por el control antes de que sean controlados por el contenedor del control.

```
ON_EVENT_REFLECT(theClass,  dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
La clase a la que pertenece este mapa de receptores de eventos.

*dispid*<br/>
El identificador de envío del evento desencadenado por el control.

*pfnHandler*<br/>
Puntero a una función miembro que controla el evento. Esta función debe tener un tipo de valor devuelto BOOL y tipos de parámetros que coincidan con los parámetros del evento (consulte *vtsParams*). La función debe devolver TRUE para indicar que se controló el evento; de lo contrario FALSO.

*vtsParams*<br/>
Secuencia de **VTS_** constantes que especifica los tipos de los parámetros del evento. Estas son las mismas constantes que se utilizan en las entradas del mapa de distribución, como DISP_FUNCTION.

### <a name="remarks"></a>Observaciones

El argumento *vtsParams* es una lista de valores separados por espacios de las constantes **VTS_.**

Uno o varios de estos valores separados por espacios (no comas) especifican la lista de parámetros de la función. Por ejemplo:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

especifica una lista que contiene un entero corto seguido de un BOOL.

Para obtener una lista de las constantes **VTS_,** consulte [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="on_propnotify"></a><a name="on_propnotify"></a>ON_PROPNOTIFY

Utilice la macro ON_PROPNOTIFY para definir una entrada de mapa de receptor de eventos para controlar las notificaciones de propiedades desde un control OLE.

```
ON_PROPNOTIFY(theClass, id, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
La clase a la que pertenece este mapa de receptores de eventos.

*id*<br/>
El identificador de control del control OLE.

*dispid*<br/>
El id de envío de la propiedad implicada en la notificación.

*pfnRequest*<br/>
Puntero a una función `OnRequestEdit` miembro que controla la notificación de esta propiedad. Esta función debe tener un tipo de valor devuelto BOOL y un parámetro **BOOL.** <strong>\*</strong> Esta función debe establecer el parámetro en TRUE para permitir que la propiedad cambie y FALSE para no permitir. La función debe devolver TRUE para indicar que se ha controlado la notificación; de lo contrario FALSO.

*pfnChanged*<br/>
Puntero a una función `OnChanged` miembro que controla la notificación de esta propiedad. La función debe tener un tipo de valor devuelto BOOL y un parámetro UINT. La función debe devolver TRUE para indicar que se controló la notificación; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

El argumento *vtsParams* es una lista de valores separados por espacios de las constantes **VTS_.** Uno o varios de estos valores separados por espacios (no comas) especifican la lista de parámetros de la función. Por ejemplo:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

especifica una lista que contiene un entero corto seguido de un BOOL.

Para obtener una lista de las constantes **VTS_,** consulte [EVENT_CUSTOM](event-maps.md#event_custom).

## <a name="on_propnotify_range"></a><a name="on_propnotify_range"></a>ON_PROPNOTIFY_RANGE

Utilice la macro ON_PROPNOTIFY_RANGE para definir una entrada de mapa de receptor de eventos para controlar las notificaciones de propiedad de cualquier control OLE que tenga un identificador de control dentro de un intervalo contiguo de identificadores.

```

ON_PROPNOTIFY_RANGE(theClass, idFirst, idLast, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
La clase a la que pertenece este mapa de receptores de eventos.

*idFirst*<br/>
El identificador de control del primer control OLE en el intervalo.

*idLast*<br/>
El identificador de control del último control OLE del intervalo.

*dispid*<br/>
El id de envío de la propiedad implicada en la notificación.

*pfnRequest*<br/>
Puntero a una función `OnRequestEdit` miembro que controla la notificación de esta propiedad. Esta función `BOOL` debe tener `UINT` `BOOL*` un tipo de valor devuelto y parámetros. La función debe establecer el parámetro en TRUE para permitir que la propiedad cambie y FALSE para no permitir. La función debe devolver TRUE para indicar que se controló la notificación; de lo contrario FALSO.

*pfnChanged*<br/>
Puntero a una función `OnChanged` miembro que controla la notificación de esta propiedad. La función `BOOL` debe tener `UINT` un tipo de valor devuelto y un parámetro. La función debe devolver TRUE para indicar que se controló la notificación; de lo contrario FALSO.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="on_propnotify_reflect"></a><a name="on_propnotify_reflect"></a>ON_PROPNOTIFY_REFLECT

La macro ON_PROPNOTIFY_REFLECT, cuando se usa en el mapa del receptor de eventos de la clase contenedora de un control OLE, recibe notificaciones de propiedad enviadas por el control antes de que las controle el contenedor del control.

```

ON_PROPNOTIFY_REFLECT(theClass, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
La clase a la que pertenece este mapa de receptores de eventos.

*dispid*<br/>
El id de envío de la propiedad implicada en la notificación.

*pfnRequest*<br/>
Puntero a una función `OnRequestEdit` miembro que controla la notificación de esta propiedad. Esta función debe tener un tipo de valor devuelto BOOL y un parámetro **BOOL.** <strong>\*</strong> Esta función debe establecer el parámetro en TRUE para permitir que la propiedad cambie y FALSE para no permitir. La función debe devolver TRUE para indicar que se ha controlado la notificación; de lo contrario FALSO.

*pfnChanged*<br/>
Puntero a una función `OnChanged` miembro que controla la notificación de esta propiedad. La función debe tener un tipo de valor devuelto BOOL y ningún parámetro. La función debe devolver TRUE para indicar que se ha controlado la notificación; de lo contrario FALSO.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
