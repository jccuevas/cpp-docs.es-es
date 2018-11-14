---
title: Mapas de receptor de eventos
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.maps
helpviewer_keywords:
- event sink maps [MFC]
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
ms.openlocfilehash: 3e75f1d880ce767b6fdbb61b4877f0748ba779f4
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518936"
---
# <a name="event-sink-maps"></a>Mapas de receptor de eventos

Cuando un control OLE incrustado desencadena un evento, el contenedor del control recibe el evento mediante un mecanismo, denominado un "receptor mapa de eventos," proporcionado por MFC. Este mapa de receptores de eventos designa las funciones de controlador para cada evento específico, así como los parámetros de esos eventos. Para obtener más información sobre los mapas de receptor de eventos, vea el artículo [contenedores de controles ActiveX](../../mfc/activex-control-containers.md).

### <a name="event-sink-maps"></a>Mapas de receptor de eventos

|||
|-|-|
|[BEGIN_EVENTSINK_MAP](#begin_eventsink_map)|Inicia la definición de un mapa de receptores de eventos.|
|[DECLARE_EVENTSINK_MAP](#declare_eventsink_map)|Declara un mapa de receptores de eventos.|
|[END_EVENTSINK_MAP](#end_eventsink_map)|Termina la definición de un mapa de receptores de eventos.|
|[ON_EVENT](#on_event)|Define un controlador de eventos para un evento concreto.|
|[ON_EVENT_RANGE](#on_event_range)|Define un controlador de eventos para un evento concreto que se activa desde un conjunto de controles OLE.|
|[ON_EVENT_REFLECT](#on_event_reflect)|Recibe eventos desencadenados por el control antes de que están controlados por el contenedor del control.|
|[ON_PROPNOTIFY](#on_propnotify)|Define un controlador para controlar las notificaciones de la propiedad de un control OLE.|
|[ON_PROPNOTIFY_RANGE](#on_propnotify_range)|Define un controlador para controlar las notificaciones de la propiedad de un conjunto de controles OLE.|
|[ON_PROPNOTIFY_REFLECT](#on_propnotify_reflect)|Recibe notificaciones de propiedad enviadas por el control antes de que están controlados por el contenedor del control.|

##  <a name="begin_eventsink_map"></a>  BEGIN_EVENTSINK_MAP

Inicia la definición de la asignación de receptor de eventos.

```
BEGIN_EVENTSINK_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
Especifica el nombre de la clase control asignarlo cuyo receptor de eventos.

*baseClass*<br/>
Especifica el nombre de la clase base de *theClass*.

### <a name="remarks"></a>Comentarios

En el archivo de implementación (.cpp) que define las funciones de miembro para la clase, iniciar la asignación de receptor de eventos con el begin_eventsink_map (macro), a continuación, agregue entradas de macro para cada evento recibir una notificación de y completar la asignación de receptor de eventos con el END_EVENTSINK_MAP (macro).

Para obtener más información sobre los mapas de receptor de eventos y los contenedores de controles OLE, vea el artículo [contenedores de controles ActiveX](../../mfc/activex-control-containers.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

##  <a name="declare_eventsink_map"></a>  DECLARE_EVENTSINK_MAP

Un contenedor OLE puede proporcionar un mapa de receptores de eventos para especificar los eventos que se notificará el contenedor.

```
DECLARE_EVENTSINK_MAP()
```

### <a name="remarks"></a>Comentarios

Utilice el declare_eventsink_map (macro) al final de la declaración de clase. A continuación, en el. Archivo CPP que define las funciones miembro de la clase, use el begin_eventsink_map (macro), las entradas de la macro para cada uno de los eventos para recibir una notificación de y la END_EVENTSINK_MAP (macro) para declarar el final de la lista de receptores de eventos.

Para obtener más información sobre los mapas de receptor de eventos, vea el artículo [contenedores de controles ActiveX](../../mfc/activex-control-containers.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

##  <a name="end_eventsink_map"></a>  END_EVENTSINK_MAP

Termina la definición de la asignación de receptor de eventos.

```
END_EVENTSINK_MAP()
```

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

##  <a name="on_event"></a>  ON_EVENT

Utilice la macro ON_EVENT para definir una función de controlador de eventos para un evento desencadenado por un control OLE.

```
ON_EVENT(theClass, id, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
La clase a la que pertenece este mapa de receptores de eventos.

*identificador*<br/>
El identificador de control del control OLE.

*DISPID*<br/>
Identificador de envío de los eventos desencadenados por el control.

*pfnHandler*<br/>
Puntero a una función miembro que controla el evento. Esta función debe tener un tipo BOOL devolver el tipo y los tipos de parámetro que coinciden con los parámetros del evento (consulte *vtsParams*). La función debe devolver TRUE para indicar que se controló el evento; en caso contrario, FALSE.

*vtsParams*<br/>
Una secuencia de **VTS_** constantes que especifica los tipos de los parámetros para el evento. Estos son la mismas constantes que se usan en las entradas de mapa de envío como DISP_FUNCTION.

### <a name="remarks"></a>Comentarios

El *vtsParams* argumento es una lista separada por espacios de los valores de la **VTS_** constantes. Uno o varios de estos valores separados por espacios (no por comas) especifican la lista de parámetros de la función. Por ejemplo:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

Especifica una lista que contiene un entero corto seguido por un valor booleano.

Para obtener una lista de los **VTS_** constantes, vea [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

##  <a name="on_event_range"></a>  ON_EVENT_RANGE

Use el on_event_range (macro) para definir una función de controlador de eventos para un evento desencadenado por cualquier control OLE tener un identificador de control dentro de un intervalo contiguo de identificadores.

```
ON_EVENT_RANGE(theClass, idFirst, idLast, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
La clase a la que pertenece este mapa de receptores de eventos.

*idFirst*<br/>
El identificador de control del primer control OLE en el intervalo.

*idLast*<br/>
El identificador de control del último control OLE en el intervalo.

*DISPID*<br/>
Identificador de envío de los eventos desencadenados por el control.

*pfnHandler*<br/>
Puntero a una función miembro que controla el evento. Esta función debe tener un valor booleano de valor devuelto tipo, un primer parámetro de tipo UINT (para el Id. de control) y los tipos de parámetro adicional que coinciden con los parámetros del evento (consulte *vtsParams*). La función debe devolver TRUE para indicar que se controló el evento; en caso contrario, FALSE.

*vtsParams*<br/>
Una secuencia de **VTS_** constantes que especifica los tipos de los parámetros para el evento. La primera constante debe ser de tipo VTS_I4, para el identificador de control. Estos son la mismas constantes que se usan en las entradas de mapa de envío como DISP_FUNCTION.

### <a name="remarks"></a>Comentarios

El *vtsParams* argumento es una lista separada por espacios de los valores de la **VTS_** constantes. Uno o varios de estos valores separados por espacios (no por comas) especifican la lista de parámetros de la función. Por ejemplo:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

Especifica una lista que contiene un entero corto seguido por un valor booleano.

Para obtener una lista de los **VTS_** constantes, vea [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un controlador de eventos para el evento MouseDown, implementado para tres controles (IDC_MYCTRL1 a través de IDC_MYCTRL3). La función de controlador de eventos, `OnRangeMouseDown`, se declara en el archivo de encabezado de la clase de cuadro de diálogo ( `CMyDlg`) como:

[!code-cpp[NVC_MFCAutomation#12](../../mfc/codesnippet/cpp/event-sink-maps_2.h)]

El código siguiente se define en el archivo de implementación de la clase de cuadro de diálogo.

[!code-cpp[NVC_MFCAutomation#13](../../mfc/codesnippet/cpp/event-sink-maps_3.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

##  <a name="on_event_reflect"></a>  ON_EVENT_REFLECT

El on_event_reflect (macro), cuando se usa en el evento mapa de receptores de la clase de contenedor de un control OLE, recibe los eventos desencadenados por el control antes de que están controlados por el contenedor del control.

```
ON_EVENT_REFLECT(theClass,  dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
La clase a la que pertenece este mapa de receptores de eventos.

*DISPID*<br/>
Identificador de envío de los eventos desencadenados por el control.

*pfnHandler*<br/>
Puntero a una función miembro que controla el evento. Esta función debe tener un tipo BOOL devuelven los tipos de parámetro que coinciden con los parámetros del evento y el tipo (vea *vtsParams*). La función debe devolver TRUE para indicar que se controló el evento; en caso contrario, FALSE.

*vtsParams*<br/>
Una secuencia de **VTS_** constantes que especifica los tipos de los parámetros para el evento. Estos son la mismas constantes que se usan en las entradas de mapa de envío como DISP_FUNCTION.

### <a name="remarks"></a>Comentarios

El *vtsParams* argumento es una lista separada por espacios de los valores de la **VTS_** constantes.

Uno o varios de estos valores separados por espacios (no por comas) especifican la lista de parámetros de la función. Por ejemplo:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

Especifica una lista que contiene un entero corto seguido por un valor booleano.

Para obtener una lista de los **VTS_** constantes, vea [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

##  <a name="on_propnotify"></a>  ON_PROPNOTIFY

Use el on_propnotify (macro) para definir una entrada de mapa de receptor de eventos para controlar las notificaciones de la propiedad de un control OLE.

```
ON_PROPNOTIFY(theClass, id, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
La clase a la que pertenece este mapa de receptores de eventos.

*identificador*<br/>
El identificador de control del control OLE.

*DISPID*<br/>
El identificador de envío de la propiedad implicada en la notificación.

*pfnRequest*<br/>
Puntero a una función miembro que controla la `OnRequestEdit` notificación para esta propiedad. Esta función debe tener un tipo BOOL tipo de valor devuelto y un **BOOL** <strong>\*</strong> parámetro. Esta función debe establecer el parámetro en TRUE para permitir que cambie la propiedad y FALSE para no permitir. La función debe devolver TRUE para indicar que la notificación se ha controlado; en caso contrario, FALSE.

*pfnChanged*<br/>
Puntero a una función miembro que controla la `OnChanged` notificación para esta propiedad. La función debe tener un valor booleano y devuelven el tipo y un parámetro UINT. La función debe devolver TRUE para indicar que la notificación se ha controlado; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

El *vtsParams* argumento es una lista separada por espacios de los valores de la **VTS_** constantes. Uno o varios de estos valores separados por espacios (no por comas) especifican la lista de parámetros de la función. Por ejemplo:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

Especifica una lista que contiene un entero corto seguido por un valor booleano.

Para obtener una lista de los **VTS_** constantes, vea [EVENT_CUSTOM](event-maps.md#event_custom).

##  <a name="on_propnotify_range"></a>  ON_PROPNOTIFY_RANGE

Use el on_propnotify_range (macro) para definir una entrada de mapa de receptor de eventos para controlar las notificaciones de la propiedad de cualquier control OLE tener un identificador de control dentro de un intervalo contiguo de identificadores.

```

ON_PROPNOTIFY_RANGE(theClass, idFirst, idLast, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
La clase a la que pertenece este mapa de receptores de eventos.

*idFirst*<br/>
El identificador de control del primer control OLE en el intervalo.

*idLast*<br/>
El identificador de control del último control OLE en el intervalo.

*DISPID*<br/>
El identificador de envío de la propiedad implicada en la notificación.

*pfnRequest*<br/>
Puntero a una función miembro que controla la `OnRequestEdit` notificación para esta propiedad. Esta función debe tener un `BOOL` tipo de valor devuelto y `UINT` y `BOOL*` parámetros. La función debe establecer el parámetro en TRUE para permitir que cambie la propiedad y FALSE para no permitir. La función debe devolver TRUE para indicar que la notificación se ha controlado; en caso contrario, FALSE.

*pfnChanged*<br/>
Puntero a una función miembro que controla la `OnChanged` notificación para esta propiedad. La función debe tener un `BOOL` tipo de valor devuelto y un `UINT` parámetro. La función debe devolver TRUE para indicar que la notificación se ha controlado; en caso contrario, FALSE.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

##  <a name="on_propnotify_reflect"></a>  ON_PROPNOTIFY_REFLECT

El on_propnotify_reflect (macro), cuando se usa en el evento mapa de receptores de la clase de contenedor de un control OLE, recibe notificaciones de propiedad enviadas por el control antes de que están controlados por el contenedor del control.

```

ON_PROPNOTIFY_REFLECT(theClass, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
La clase a la que pertenece este mapa de receptores de eventos.

*DISPID*<br/>
El identificador de envío de la propiedad implicada en la notificación.

*pfnRequest*<br/>
Puntero a una función miembro que controla la `OnRequestEdit` notificación para esta propiedad. Esta función debe tener un tipo BOOL tipo de valor devuelto y un **BOOL** <strong>\*</strong> parámetro. Esta función debe establecer el parámetro en TRUE para permitir que cambie la propiedad y FALSE para no permitir. La función debe devolver TRUE para indicar que la notificación se ha controlado; en caso contrario, FALSE.

*pfnChanged*<br/>
Puntero a una función miembro que controla la `OnChanged` notificación para esta propiedad. La función debe tener un valor booleano y devuelven el tipo y sin parámetros. La función debe devolver TRUE para indicar que la notificación se ha controlado; en caso contrario, FALSE.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="see-also"></a>Vea también

[Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
