---
title: Mapas de eventos | Microsoft Docs
ms.custom: ''
ms.date: 06/20/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- event maps [MFC]
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f937c2cdaa4bb7f31b39b8a28c657274830fc36
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446613"
---
# <a name="event-maps"></a>Mapas de eventos

Cada vez que un control que desea notificar a su contenedor que ha sucedido alguna acción (determinado por el desarrollador del control) (por ejemplo, una pulsación de tecla, clic del mouse o un cambio en el estado del control) llama a una función de activación del evento. Esta función notifica al contenedor de control que se ha producido alguna acción importante desencadenando el evento relacionado.

La biblioteca Microsoft Foundation Class ofrece un modelo de programación optimizado para desencadenar eventos. En este modelo, "mapas de eventos" se utilizan para designar qué funciones activan los eventos para un control determinado. Mapas de eventos contienen una macro para cada evento. Por ejemplo, un mapa de eventos que desencadena una acción, haga clic en eventos tendrá este aspecto:

[!code-cpp[NVC_MFCAxCtl#16](../../mfc/reference/codesnippet/cpp/event-maps_1.cpp)]

El `EVENT_STOCK_CLICK` macro indica que el control activará una acción, haga clic en evento cada vez que detecta un mouse. Para obtener una lista más detallada de otros eventos estándar, consulte el artículo [controles ActiveX: eventos](../../mfc/mfc-activex-controls-events.md). Macros también están disponibles para indicar eventos personalizados.

Aunque las macros de mapa de eventos son importantes, por lo general no insertarlos directamente. Esto es porque la ventana Propiedades crea automáticamente las entradas de mapa de eventos en los archivos de origen cuando se usa para asociar las funciones de activación de eventos con eventos. Siempre que desee editar o agregar una entrada de mapa de eventos, puede usar la ventana Propiedades.

Para que admita mapas de eventos, MFC proporciona las siguientes macros:

## <a name="event-map-macros"></a>Macros de mapa de eventos

### <a name="event-map-declaration-and-demarcation"></a>Delimitación y declaración de evento de asignación

|||
|-|-|
|[DECLARE_EVENT_MAP](#declare_event_map)|Declara que se utilizará un mapa de eventos en una clase para los eventos se asignan a las funciones de activación de eventos (debe usarse en la declaración de clase).|
|[BEGIN_EVENT_MAP](#begin_event_map)|Inicia la definición de un mapa de eventos (debe usarse en la implementación de la clase).|
|[END_EVENT_MAP](#end_event_map)|Termina la definición de un mapa de eventos (debe usarse en la implementación de la clase).|

### <a name="event-mapping-macros"></a>Macros de asignación de eventos

|||
|-|-|
|[EVENT_CUSTOM](#event_custom)|Indica qué función de activación del evento desencadenará el evento especificado.|
|[EVENT_CUSTOM_ID](#event_custom_id)|Indica qué función de activación del evento desencadenará el evento especificado, con un identificador de envío designado.|

### <a name="message-mapping-macros"></a>Macros de asignación de mensajes

|||
|-|-|
|[ON_OLEVERB](#on_oleverb)|Indica un verbo personalizado que se controla mediante el control OLE.|
|[ON_STDOLEVERB](#on_stdoleverb)|Anula una asignación de un verbo estándar del control OLE.|

##  <a name="declare_event_map"></a>  DECLARE_EVENT_MAP

Cada `COleControl`-clase derivada en el programa puede proporcionar un mapa de eventos para especificar los eventos que se activará el control.

```cpp
DECLARE_EVENT_MAP()
```

### <a name="remarks"></a>Comentarios

Utilice el declare_event_map (macro) al final de la declaración de clase. A continuación, en el archivo .cpp que define las funciones miembro de la clase, utilice el BEGIN_EVENT_MAP (macro), las entradas de la macro para cada uno de los eventos del control y la end_event_map (macro) para declarar el final de la lista de eventos.

Para obtener más información sobre los mapas de eventos, vea el artículo [controles ActiveX: eventos](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Requisitos

**Encabezado** afxctl.h

## <a name="begin_event_map"></a>  BEGIN_EVENT_MAP

Inicia la definición de la asignación de eventos.

```cpp
BEGIN_EVENT_MAP(theClass,  baseClass)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
Especifica el nombre de la clase control cuyo evento asignarlo.

*baseClass*<br/>
Especifica el nombre de la clase base de *theClass*.

### <a name="remarks"></a>Comentarios

En el archivo de implementación (.cpp) que define las funciones de miembro para la clase, inicie el mapa de eventos con el BEGIN_EVENT_MAP (macro), a continuación, agregue entradas de macro para cada uno de los eventos y completar la asignación de eventos con el end_event_map (macro).

Para obtener más información sobre los mapas de eventos y el BEGIN_EVENT_MAP (macro), consulte el artículo [controles ActiveX: eventos](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Requisitos

**Encabezado** afxctl.h

##  <a name="end_event_map"></a>  END_EVENT_MAP

Utilice el end_event_map (macro) para finalizar la definición de la asignación de eventos.

```cpp
END_EVENT_MAP()
```

### <a name="requirements"></a>Requisitos

**Encabezado** afxctl.h

## <a name="event_custom"></a>  EVENT_CUSTOM

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
Una lista separada por espacios de una o varias constantes que especifica la lista de parámetros de la función.

### <a name="remarks"></a>Comentarios

El *vtsParams* parámetro es una lista separada por espacios de los valores de la `VTS_` constantes. Uno o varios de estos valores separados por espacios (no por comas) especifican la lista de parámetros de la función. Por ejemplo:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

Especifica el color de una lista que contiene un entero de 32 bits que representa una RGB valor, seguido de un puntero a la `IFontDisp` interfaz de un objeto de fuente OLE.

El `VTS_` constantes y sus significados son los siguientes:

|Símbolo|Tipo de parámetro|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**long**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_COLOR|OLE_COLOR|
|VTS_CY|MONEDA|
|VTS_DATE|DATE|
|VTS_BSTR|**Const** __char\*__|
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
> Constantes de tipo variant adicionales se han definido para todos los tipos variantes, a excepción de VTS_FONT y VTS_PICTURE, que proporcionan un puntero a la constante de datos variant. Estas constantes se denominan mediante el `VTS_Pconstantname` convención. Por ejemplo, VTS_PCOLOR es un puntero a un VTS_COLOR (constante).

### <a name="requirements"></a>Requisitos

**Encabezado** afxctl.h

## <a name="event_custom_id"></a>  EVENT_CUSTOM_ID

Define un evento de activación de función para un evento personalizado que pertenecen a la especificada por el identificador de envío *dispid*.

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

*DISPID*<br/>
El identificador de envío utilizado por el control al activar el evento.

*pfnFire*<br/>
El nombre de la función de activación del evento.

*vtsParams*<br/>
Una lista de variables de parámetros se pasa al contenedor del control cuando se desencadena el evento.

### <a name="remarks"></a>Comentarios

El *vtsParams* argumento es una lista separada por espacios de los valores de la `VTS_` constantes. Uno o varios de estos valores separados por espacios, no por comas, especifican la lista de parámetros de la función. Por ejemplo:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

Especifica el color de una lista que contiene un entero de 32 bits que representa una RGB valor, seguido de un puntero a la `IFontDisp` interfaz de un objeto de fuente OLE.

Para obtener una lista de los `VTS_` constantes, vea [EVENT_CUSTOM](#event_custom).

### <a name="requirements"></a>Requisitos

**Encabezado** afxctl.h

## <a name="on_oleverb"></a>  ON_OLEVERB

Esta macro define una entrada de asignación de mensaje que se asigna un verbo personalizado a una función miembro específico del control.

```cpp
ON_OLEVERB(idsVerbName,  memberFxn)
```

### <a name="parameters"></a>Parámetros

*idsVerbName*<br/>
El identificador de recurso de cadena del nombre del verbo.

*memberFxn*<br/>
La función que llama el marco de trabajo cuando se invoca el verbo.

### <a name="remarks"></a>Comentarios

El editor de recursos puede usarse para crear nombres de verbo personalizados que se agregan a la tabla de cadenas.

El prototipo de función *memberFxn* es:

```cpp
BOOL memberFxn(
   LPMSG    lpMsg,
   HWND     hWndParent,
   LPCRECT  lpRect);
```

Los valores de la *lpMsg*, *hWndParent*, y *lpRect* parámetros se toman de los parámetros correspondientes de la `IOleObject::DoVerb` función miembro.

### <a name="requirements"></a>Requisitos

**Encabezado** afxole.h

## <a name="on_stdoleverb"></a>  ON_STDOLEVERB

Use esta macro para invalidar el comportamiento predeterminado de un verbo estándar.

```cpp
ON_STDOLEVERB(iVerb, memberFxn)
```

### <a name="parameters"></a>Parámetros

*iVerb*<br/>
El índice del verbo estándar para el verbo que se va a invalidar.

*memberFxn*<br/>
La función que llama el marco de trabajo cuando se invoca el verbo.

### <a name="remarks"></a>Comentarios

El índice del verbo estándar tiene el formato `OLEIVERB_`, seguido de una acción. OLEIVERB_SHOW OLEIVERB_HIDE y OLEIVERB_UIACTIVATE son algunos ejemplos de verbos estándar.

Consulte [ON_OLEVERB](#on_oleverb) para obtener una descripción del prototipo de función que se usará como el *memberFxn* parámetro.


### <a name="requirements"></a>Requisitos

**Encabezado** afxole.h

## <a name="see-also"></a>Vea también

[Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
