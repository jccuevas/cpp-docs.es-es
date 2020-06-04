---
title: Mapas de eventos
ms.date: 09/07/2019
helpviewer_keywords:
- event maps [MFC]
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
ms.openlocfilehash: c79d2fb1ac73947ddb13adcbd444ff7b5d50bdb4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365738"
---
# <a name="event-maps"></a>Mapas de eventos

Cada vez que un control desea notificar a su contenedor que alguna acción (determinada por el desarrollador del control) ha ocurrido (como una pulsación de tecla, un clic del mouse o un cambio en el estado del control) llama a una función de disparo de eventos. Esta función notifica al contenedor de control que se ha producido alguna acción importante desencadenando el evento relacionado.

La biblioteca Microsoft Foundation Class ofrece un modelo de programación optimizado para desencadenar eventos. En este modelo, se utilizan "mapas de eventos" para designar qué funciones desencadenan qué eventos para un control determinado. Los mapas de eventos contienen una macro para cada evento. Por ejemplo, un mapa de eventos que activa un evento Click de stock podría tener este aspecto:

[!code-cpp[NVC_MFCAxCtl#16](../../mfc/reference/codesnippet/cpp/event-maps_1.cpp)]

La `EVENT_STOCK_CLICK` macro indica que el control activará un evento Click de stock cada vez que detecte un clic del ratón. Para obtener una lista más detallada de otros eventos de stock, consulte el artículo [Controles ActiveX: Eventos](../../mfc/mfc-activex-controls-events.md). Las macros también están disponibles para indicar eventos personalizados.

Aunque las macros de mapa de eventos son importantes, generalmente no se insertan directamente. Esto se debe a que la ventana **Propiedades** (en **la**vista de clases ) crea automáticamente entradas de mapa de eventos en los archivos de origen cuando se utiliza para asociar funciones de activación de eventos con eventos. Cada vez que desee editar o agregar una entrada de mapa de eventos, puede utilizar la ventana **Propiedades.**

Para admitir mapas de eventos, MFC proporciona las siguientes macros:

## <a name="event-map-macros"></a>Macros del mapa de eventos

### <a name="event-map-declaration-and-demarcation"></a>Declaración y demarcación del mapa de eventos

|||
|-|-|
|[DECLARE_EVENT_MAP](#declare_event_map)|Declara que se usará un mapa de eventos en una clase para asignar eventos a funciones de desencadenamiento de eventos (debe utilizarse en la declaración de clase).|
|[BEGIN_EVENT_MAP](#begin_event_map)|Comienza la definición de un mapa de eventos (debe usarse en la implementación de la clase).|
|[END_EVENT_MAP](#end_event_map)|Finaliza la definición de un mapa de eventos (debe utilizarse en la implementación de la clase).|

### <a name="event-mapping-macros"></a>Macros de asignación de eventos

|||
|-|-|
|[EVENT_CUSTOM](#event_custom)|Indica qué función de activación de eventos activará el evento especificado.|
|[EVENT_CUSTOM_ID](#event_custom_id)|Indica qué función de activación de eventos activará el evento especificado, con un ID de envío designado.|

### <a name="message-mapping-macros"></a>Macros de asignación de mensajes

|||
|-|-|
|[ON_OLEVERB](#on_oleverb)|Indica un verbo personalizado controlado por el control OLE.|
|[ON_STDOLEVERB](#on_stdoleverb)|Reemplaza una asignación de verbo estándar del control OLE.|

## <a name="declare_event_map"></a><a name="declare_event_map"></a>DECLARE_EVENT_MAP

Cada `COleControl`clase derivada del programa puede proporcionar un mapa de eventos para especificar los eventos que se activará el control.

```cpp
DECLARE_EVENT_MAP()
```

### <a name="remarks"></a>Observaciones

Utilice la macro DECLARE_EVENT_MAP al final de la declaración de clase. A continuación, en el archivo .cpp que define las funciones miembro de la clase, use la macro BEGIN_EVENT_MAP, las entradas de macro para cada uno de los eventos del control y la END_EVENT_MAP macro para declarar el final de la lista de eventos.

Para obtener más información sobre los mapas de eventos, consulte el artículo [Controles ActiveX: Eventos](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Requisitos

**Encabezado** afxctl.h

## <a name="begin_event_map"></a><a name="begin_event_map"></a>BEGIN_EVENT_MAP

Comienza la definición del mapa de eventos.

```cpp
BEGIN_EVENT_MAP(theClass,  baseClass)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
Especifica el nombre de la clase de control cuyo mapa de eventos es.

*baseClass*<br/>
Especifica el nombre de la clase base de *theClass*.

### <a name="remarks"></a>Observaciones

En el archivo de implementación (.cpp) que define las funciones miembro de la clase, inicie el mapa de eventos con la macro BEGIN_EVENT_MAP, agregue entradas de macro para cada uno de los eventos y complete el mapa de eventos con la macro END_EVENT_MAP.

Para obtener más información sobre los mapas de eventos y la macro de BEGIN_EVENT_MAP, consulte el artículo [Controles ActiveX: Eventos](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Requisitos

**Encabezado** afxctl.h

## <a name="end_event_map"></a><a name="end_event_map"></a>END_EVENT_MAP

Utilice la macro END_EVENT_MAP para finalizar la definición del mapa de eventos.

```cpp
END_EVENT_MAP()
```

### <a name="requirements"></a>Requisitos

**Encabezado** afxctl.h

## <a name="event_custom"></a><a name="event_custom"></a>EVENT_CUSTOM

Define una entrada de mapa de eventos para un evento personalizado.

```cpp
EVENT_CUSTOM(pszName, pfnFire,  vtsParams)
```

### <a name="parameters"></a>Parámetros

*pszName*<br/>
Nombre del evento.

*pfnFire*<br/>
El nombre de la función de activación del evento.

*vtsParams*<br/>
Una lista separada por espacios de una o más constantes que especifican la lista de parámetros de la función.

### <a name="remarks"></a>Observaciones

El parámetro *vtsParams* es una lista de `VTS_` valores separados por espacios de las constantes. Uno o varios de estos valores separados por espacios (no comas) especifican la lista de parámetros de la función. Por ejemplo:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

especifica una lista que contiene un entero de 32 bits que `IFontDisp` representa un valor de color RGB, seguido de un puntero a la interfaz de un objeto de fuente OLE.

Las `VTS_` constantes y sus significados son los siguientes:

|Símbolo|Tipo de parámetro|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**Largo**|
|VTS_R4|**Flotador**|
|VTS_R8|**double**|
|VTS_COLOR|OLE_COLOR|
|VTS_CY|Moneda|
|VTS_DATE|DATE|
|VTS_BSTR|**const** __\* char__|
|VTS_DISPATCH|LPDISPATCH|
|VTS_FONT|`IFontDispatch*`|
|VTS_HANDLE|HANDLE|
|VTS_SCODE|SCODE|
|VTS_BOOL|BOOL|
|VTS_VARIANT|`const VARIANT*`|
|VTS_PVARIANT|`VARIANT*`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_OPTEXCLUSIVE|OLE_OPTEXCLUSIVE|
|VTS_PICTURE|`IPictureDisp*`|
|VTS_TRISTATE|OLE_TRISTATE|
|VTS_XPOS_PIXELS|OLE_XPOS_PIXELS|
|VTS_YPOS_PIXELS|OLE_YPOS_PIXELS|
|VTS_XSIZE_PIXELS|OLE_XSIZE_PIXELS|
|VTS_YSIZE_PIXELS|OLE_YSIZE_PIXELS|
|TS_XPOS_HIMETRIC|OLE_XPOS_HIMETRIC|
|VTS_YPOS_HIMETRIC|OLE_YPOS_HIMETRIC|
|VTS_XSIZE_HIMETRIC|OLE_XSIZE_HIMETRIC|
|VTS_YSIZE_HIMETRIC|OLE_YSIZE_HIMETRIC|

> [!NOTE]
> Se han definido constantes de variante adicionales para todos los tipos de variante, con la excepción de VTS_FONT y VTS_PICTURE, que proporcionan un puntero a la constante de datos de variante. Estas constantes se `VTS_Pconstantname` denominan mediante la convención. Por ejemplo, VTS_PCOLOR es un puntero a una constante VTS_COLOR.

### <a name="requirements"></a>Requisitos

**Encabezado** afxctl.h

## <a name="event_custom_id"></a><a name="event_custom_id"></a>EVENT_CUSTOM_ID

Define una función de activación de eventos para un evento personalizado que pertenece al identificador de envío especificado por *dispid*.

```cpp
EVENT_CUSTOM_ID(
    pszName,
    dispid,
    pfnFire,
    vtsParams)
```

### <a name="parameters"></a>Parámetros

*pszName*<br/>
Nombre del evento.

*dispid*<br/>
El identificador de envío utilizado por el control al desencadenar el evento.

*pfnFire*<br/>
El nombre de la función de activación del evento.

*vtsParams*<br/>
Una lista de variables de parámetros pasados al contenedor de control cuando se desencadena el evento.

### <a name="remarks"></a>Observaciones

El argumento *vtsParams* es una lista de `VTS_` valores separados por espacios de las constantes. Uno o varios de estos valores separados por espacios, no comas, especifica la lista de parámetros de la función. Por ejemplo:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

especifica una lista que contiene un entero de 32 bits que `IFontDisp` representa un valor de color RGB, seguido de un puntero a la interfaz de un objeto de fuente OLE.

Para obtener una `VTS_` lista de las constantes, consulte [EVENT_CUSTOM](#event_custom).

### <a name="requirements"></a>Requisitos

**Encabezado** afxctl.h

## <a name="on_oleverb"></a><a name="on_oleverb"></a>ON_OLEVERB

Esta macro define una entrada de mapa de mensajes que asigna un verbo personalizado a una función miembro específica del control.

```cpp
ON_OLEVERB(idsVerbName,  memberFxn)
```

### <a name="parameters"></a>Parámetros

*idsVerbName*<br/>
El identificador de recurso de cadena del nombre del verbo.

*memberFxn*<br/>
La función a la que llama el marco de trabajo cuando se invoca el verbo.

### <a name="remarks"></a>Observaciones

El editor de recursos se puede usar para crear nombres de verbo personalizados que se agregan a la tabla de cadenas.

El prototipo de función para *memberFxn* es:

```cpp
BOOL memberFxn(
   LPMSG    lpMsg,
   HWND     hWndParent,
   LPCRECT  lpRect);
```

Los valores de los parámetros *lpMsg*, *hWndParent*y *lpRect* se toman de los parámetros correspondientes de la `IOleObject::DoVerb` función miembro.

### <a name="requirements"></a>Requisitos

**Encabezado** afxole.h

## <a name="on_stdoleverb"></a><a name="on_stdoleverb"></a>ON_STDOLEVERB

Utilice esta macro para invalidar el comportamiento predeterminado de un verbo estándar.

```cpp
ON_STDOLEVERB(iVerb, memberFxn)
```

### <a name="parameters"></a>Parámetros

*iVerb*<br/>
El índice de verbo estándar para el verbo que se va a reemplazar.

*memberFxn*<br/>
La función a la que llama el marco de trabajo cuando se invoca el verbo.

### <a name="remarks"></a>Observaciones

El índice de verbo `OLEIVERB_`estándar es de la forma, seguido de una acción. OLEIVERB_SHOW, OLEIVERB_HIDE y OLEIVERB_UIACTIVATE son algunos ejemplos de verbos estándar.

Consulte [ON_OLEVERB](#on_oleverb) para obtener una descripción del prototipo de función que se utilizará como parámetro *memberFxn.*

### <a name="requirements"></a>Requisitos

**Encabezado** afxole.h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
