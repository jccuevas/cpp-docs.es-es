---
title: Mapas de eventos
ms.date: 06/20/2018
helpviewer_keywords:
- event maps [MFC]
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
ms.openlocfilehash: ef730574b26a4c3619df886b72770ce7e035a40e
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916466"
---
# <a name="event-maps"></a>Mapas de eventos

Cada vez que un control desea notificar a su contenedor que se ha producido alguna acción (determinada por el desarrollador del control) (por ejemplo, una pulsación de tecla, un clic del mouse o un cambio en el estado del control), llama a una función de activación de eventos. Esta función notifica al contenedor de controles que se ha producido alguna acción importante mediante la activación del evento relacionado.

El biblioteca MFC ofrece un modelo de programación optimizado para desencadenar eventos. En este modelo, se usan "mapas de eventos" para designar qué funciones activan los eventos de un control determinado. Los mapas de eventos contienen una macro para cada evento. Por ejemplo, un mapa de eventos que desencadena un evento de clic en existencias podría ser similar al siguiente:

[!code-cpp[NVC_MFCAxCtl#16](../../mfc/reference/codesnippet/cpp/event-maps_1.cpp)]

La `EVENT_STOCK_CLICK` macro indica que el control activará un evento de clic en existencias cada vez que detecte un clic del mouse. Para obtener una lista más detallada de otros eventos bursátiles, consulte [el artículo controles ActiveX: Eventos](../../mfc/mfc-activex-controls-events.md). También hay macros disponibles para indicar eventos personalizados.

Aunque las macros de mapa de eventos son importantes, normalmente no se insertan directamente. Esto se debe a que el ventana Propiedades crea automáticamente entradas de mapa de eventos en los archivos de código fuente cuando se usa para asociar funciones de activación de eventos con eventos. Siempre que desee editar o agregar una entrada de mapa de eventos, puede usar el ventana Propiedades.

Para admitir mapas de eventos, MFC proporciona las siguientes macros:

## <a name="event-map-macros"></a>Macros de mapa de eventos

### <a name="event-map-declaration-and-demarcation"></a>Declaración y demarcación del mapa de eventos

|||
|-|-|
|[DECLARE_EVENT_MAP](#declare_event_map)|Declara que se usará un mapa de eventos en una clase para asignar eventos a las funciones de desencadenamiento de eventos (se debe usar en la declaración de clase).|
|[BEGIN_EVENT_MAP](#begin_event_map)|Comienza la definición de un mapa de eventos (debe usarse en la implementación de la clase).|
|[END_EVENT_MAP](#end_event_map)|Finaliza la definición de un mapa de eventos (debe usarse en la implementación de la clase).|

### <a name="event-mapping-macros"></a>Macros de asignación de eventos

|||
|-|-|
|[EVENT_CUSTOM](#event_custom)|Indica qué función de activación de eventos desencadenará el evento especificado.|
|[EVENT_CUSTOM_ID](#event_custom_id)|Indica qué función de activación de eventos desencadenará el evento especificado, con un identificador de envío designado.|

### <a name="message-mapping-macros"></a>Macros de asignación de mensajes

|||
|-|-|
|[ON_OLEVERB](#on_oleverb)|Indica un verbo personalizado controlado por el control OLE.|
|[ON_STDOLEVERB](#on_stdoleverb)|Invalida una asignación de verbo estándar del control OLE.|

##  <a name="declare_event_map"></a>  DECLARE_EVENT_MAP

Cada `COleControl`clase derivada de en el programa puede proporcionar un mapa de eventos para especificar los eventos que el control activará.

```cpp
DECLARE_EVENT_MAP()
```

### <a name="remarks"></a>Comentarios

Use la macro DECLARE_EVENT_MAP al final de la declaración de clase. A continuación, en el archivo. cpp que define las funciones miembro de la clase, utilice la macro BEGIN_EVENT_MAP, las entradas de macro para cada uno de los eventos del control y la macro END_EVENT_MAP para declarar el final de la lista de eventos.

Para obtener más información sobre los mapas de eventos, [vea el artículo controles ActiveX: Eventos](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Requisitos

**Encabezado** afxctl. h

## <a name="begin_event_map"></a>  BEGIN_EVENT_MAP

Comienza la definición del mapa de eventos.

```cpp
BEGIN_EVENT_MAP(theClass,  baseClass)
```

### <a name="parameters"></a>Parámetros

*Clase*<br/>
Especifica el nombre de la clase de control cuya asignación de eventos es.

*baseClass*<br/>
Especifica el nombre de la clase base de la *clase*.

### <a name="remarks"></a>Comentarios

En el archivo de implementación (. cpp) que define las funciones miembro de la clase, inicie el mapa de eventos con la macro BEGIN_EVENT_MAP, agregue las entradas de macro para cada uno de los eventos y complete el mapa de eventos con la macro END_EVENT_MAP.

Para obtener más información sobre los mapas de eventos y la macro BEGIN_EVENT_MAP, [vea el artículo controles ActiveX: Eventos](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Requisitos

**Encabezado** afxctl. h

##  <a name="end_event_map"></a>  END_EVENT_MAP

Use la macro END_EVENT_MAP para finalizar la definición del mapa de eventos.

```cpp
END_EVENT_MAP()
```

### <a name="requirements"></a>Requisitos

**Encabezado** afxctl. h

## <a name="event_custom"></a>EVENT_CUSTOM

Define una entrada de mapa de eventos para un evento personalizado.

```cpp
EVENT_CUSTOM(pszName, pfnFire,  vtsParams)
```

### <a name="parameters"></a>Parámetros

*pszName*<br/>
Nombre del evento.

*pfnFire*<br/>
Nombre de la función de activación de eventos.

*vtsParams*<br/>
Lista separada por espacios de una o más constantes que especifican la lista de parámetros de la función.

### <a name="remarks"></a>Comentarios

El parámetro *vtsParams* es una lista de valores separados por espacios de las `VTS_` constantes. Uno o varios de estos valores separados por espacios (no comas) especifica la lista de parámetros de la función. Por ejemplo:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

especifica una lista que contiene un entero de 32 bits que representa un valor de color RGB, seguido de un puntero `IFontDisp` a la interfaz de un objeto de fuente OLE.

Las `VTS_` constantes y sus significados son los siguientes:

|Símbolo|Tipo de parámetro|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**long**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_COLOR|OLE_COLOR|
|VTS_CY|MONETARIA|
|VTS_DATE|DATE|
|VTS_BSTR|**const** __carácter\*__|
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
> Se han definido constantes variantes adicionales para todos los tipos Variant, con la excepción de VTS_FONT y VTS_PICTURE, que proporcionan un puntero a la constante de datos Variant. Estas constantes se denominan mediante la `VTS_Pconstantname` Convención. Por ejemplo, VTS_PCOLOR es un puntero a una constante VTS_COLOR.

### <a name="requirements"></a>Requisitos

**Encabezado** afxctl. h

## <a name="event_custom_id"></a>EVENT_CUSTOM_ID

Define una función de activación de eventos para un evento personalizado que pertenece al identificador deenvío especificado por DispId.

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
El identificador de envío utilizado por el control al activar el evento.

*pfnFire*<br/>
Nombre de la función de activación de eventos.

*vtsParams*<br/>
Lista de variables de los parámetros pasados al contenedor de controles cuando se desencadena el evento.

### <a name="remarks"></a>Comentarios

El argumento *vtsParams* es una lista de valores separados por espacios de las `VTS_` constantes. Uno o varios de estos valores separados por espacios, no por comas, especifica la lista de parámetros de la función. Por ejemplo:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

especifica una lista que contiene un entero de 32 bits que representa un valor de color RGB, seguido de un puntero `IFontDisp` a la interfaz de un objeto de fuente OLE.

Para obtener una lista de `VTS_` las constantes, vea [EVENT_CUSTOM](#event_custom).

### <a name="requirements"></a>Requisitos

**Encabezado** afxctl. h

## <a name="on_oleverb"></a>ON_OLEVERB

Esta macro define una entrada de mapa de mensajes que asigna un verbo personalizado a una función miembro específica del control.

```cpp
ON_OLEVERB(idsVerbName,  memberFxn)
```

### <a name="parameters"></a>Parámetros

*idsVerbName*<br/>
IDENTIFICADOR de recurso de cadena del nombre del verbo.

*memberFxn*<br/>
Función a la que llama el marco de trabajo cuando se invoca el verbo.

### <a name="remarks"></a>Comentarios

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

**Encabezado** afxole. h

## <a name="on_stdoleverb"></a>ON_STDOLEVERB

Use esta macro para invalidar el comportamiento predeterminado de un verbo estándar.

```cpp
ON_STDOLEVERB(iVerb, memberFxn)
```

### <a name="parameters"></a>Parámetros

*iVerb*<br/>
Índice del verbo estándar para el verbo que se va a reemplazar.

*memberFxn*<br/>
Función a la que llama el marco de trabajo cuando se invoca el verbo.

### <a name="remarks"></a>Comentarios

El índice del verbo estándar tiene el formato `OLEIVERB_`, seguido de una acción. OLEIVERB_SHOW, OLEIVERB_HIDE y OLEIVERB_UIACTIVATE son algunos ejemplos de verbos estándar.

Vea [ON_OLEVERB](#on_oleverb) para obtener una descripción del prototipo de función que se va a usar como parámetro *memberFxn* .

### <a name="requirements"></a>Requisitos

**Encabezado** afxole. h

## <a name="see-also"></a>Vea también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
