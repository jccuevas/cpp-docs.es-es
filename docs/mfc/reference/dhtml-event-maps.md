---
title: DHTML (Mapas de eventos)
ms.date: 11/04/2016
f1_keywords:
- vc.macros.shared
helpviewer_keywords:
- event map macros [MFC]
- DHTML [MFC], event map macros
- macros [MFC], DHTML event map
- DHTML events [MFC], event map
- DHTML events [MFC]
ms.assetid: 9a2c8ae7-7216-4a5e-bc60-6b98695be0c6
ms.openlocfilehash: 30c755b2901374cffab3ce91d0683811ef6624b6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365806"
---
# <a name="dhtml-event-maps"></a>DHTML (Mapas de eventos)

Las siguientes macros se pueden utilizar para controlar eventos DHTML.

## <a name="dhtml-event-map-macros"></a>Macros de mapa de eventos DHTML

Las siguientes macros se pueden utilizar para controlar eventos DHTML en clases derivadas [de CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md).

|||
|-|-|
|[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)|Marca el inicio del mapa de eventos DHTML.|
|[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)|Marca el inicio del mapa de eventos DHTML.|
|[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)|Declara el mapa de eventos DHTML.|
|[DHTML_EVENT](#dhtml_event)|Se utiliza para controlar un evento en el nivel de documento para un único elemento HTML.|
|[DHTML_EVENT_AXCONTROL](#dhtml_event_axcontrol)|Se utiliza para controlar un evento desencadenado por un control ActiveX.|
|[DHTML_EVENT_CLASS](#dhtml_event_class)|Se utiliza para controlar un evento en el nivel de documento para todos los elementos HTML con una clase CSS determinada.|
|[DHTML_EVENT_ELEMENT](#dhtml_event_element)|Se utiliza para controlar un evento en el nivel de elemento.|
|[DHTML_EVENT_ONAFTERUPDATE](#dhtml_event_onafterupdate)|Se utiliza `onafterupdate` para controlar el evento desde un elemento HTML.|
|[DHTML_EVENT_ONBEFOREUPDATE](#dhtml_event_onbeforeupdate)|Se utiliza `onbeforeupdate` para controlar el evento desde un elemento HTML.|
|[DHTML_EVENT_ONBLUR](#dhtml_event_onblur)|Se utiliza `onblur` para controlar el evento desde un elemento HTML.|
|[DHTML_EVENT_ONCHANGE](#dhtml_event_onchange)|Se utiliza `onchange` para controlar el evento desde un elemento HTML.|
|[DHTML_EVENT_ONCLICK](#dhtml_event_onclick)|Se utiliza `onclick` para controlar el evento desde un elemento HTML.|
|[DHTML_EVENT_ONDATAAVAILABLE](#dhtml_event_ondataavailable)|Se utiliza `ondataavailable` para controlar el evento desde un elemento HTML.|
|[DHTML_EVENT_ONDATASETCHANGED](#dhtml_event_ondatasetchanged)|Se utiliza `ondatasetchanged` para controlar el evento desde un elemento HTML.|
|[DHTML_EVENT_ONDATASETCOMPLETE](#dhtml_event_ondatasetcomplete)|Se utiliza `ondatasetcomplete` para controlar el evento desde un elemento HTML.|
|[DHTML_EVENT_ONDBLCLICK](#dhtml_event_ondblclick)|Se utiliza `ondblclick` para controlar el evento desde un elemento HTML.|
|[DHTML_EVENT_ONDRAGSTART](#dhtml_event_ondragstart)|Se utiliza `ondragstart` para controlar el evento desde un elemento HTML.|
|[DHTML_EVENT_ONERRORUPDATE](#dhtml_event_onerrorupdate)|Se utiliza `onerrorupdate` para controlar el evento desde un elemento HTML.|
|[DHTML_EVENT_ONFILTERCHANGE](#dhtml_event_onfilterchange)|Se utiliza `onfilterchange` para controlar el evento desde un elemento HTML.|
|[DHTML_EVENT_ONFOCUS](#dhtml_event_onfocus)|Se utiliza `onfocus` para controlar el evento desde un elemento HTML.|
|[DHTML_EVENT_ONHELP](#dhtml_event_onhelp)|Se utiliza `onhelp` para controlar el evento desde un elemento HTML.|
|[DHTML_EVENT_ONKEYDOWN](#dhtml_event_onkeydown)|Se utiliza `onkeydown` para controlar el evento desde un elemento HTML.|
|[DHTML_EVENT_ONKEYPRESS](#dhtml_event_onkeypress)|Se utiliza `onkeypress` para controlar el evento desde un elemento HTML.|
|[DHTML_EVENT_ONKEYUP](#dhtml_event_onkeyup)|Se utiliza `onkeyup` para controlar el evento desde un elemento HTML.|
|[DHTML_EVENT_ONMOUSEDOWN](#dhtml_event_onmousedown)|Se utiliza `onmousedown` para controlar el evento desde un elemento HTML.|
|[DHTML_EVENT_ONMOUSEMOVE](#dhtml_event_onmousemove)|Se utiliza `onmousemove` para controlar el evento desde un elemento HTML.|
|[DHTML_EVENT_ONMOUSEOUT](#dhtml_event_onmouseout)|Se utiliza `onmouseout` para controlar el evento desde un elemento HTML.|
|[DHTML_EVENT_ONMOUSEOVER](#dhtml_event_onmouseover)|Se utiliza `onmouseover` para controlar el evento desde un elemento HTML.|
|[DHTML_EVENT_ONMOUSEUP](#dhtml_event_onmouseup)|Se utiliza `onmouseup` para controlar el evento desde un elemento HTML.|
|[DHTML_EVENT_ONRESIZE](#dhtml_event_onresize)|Se utiliza `onresize` para controlar el evento desde un elemento HTML.|
|[DHTML_EVENT_ONROWENTER](#dhtml_event_onrowenter)|Se utiliza `onrowenter` para controlar el evento desde un elemento HTML.|
|[DHTML_EVENT_ONROWEXIT](#dhtml_event_onrowexit)|Se utiliza `onrowexit` para controlar el evento desde un elemento HTML.|
|[DHTML_EVENT_ONSELECTSTART](#dhtml_event_onselectstart)|Se utiliza `onselectstart` para controlar el evento desde un elemento HTML.|
|[DHTML_EVENT_TAG](#dhtml_event_tag)|Se utiliza para controlar un evento en el nivel de documento para todos los elementos con una etiqueta HTML determinada.|
|[END_DHTML_EVENT_MAP](#end_dhtml_event_map)|Marca el final del mapa de eventos DHTML.|
|[END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)|Marca el final del mapa de eventos DHTML. |

## <a name="url-event-map-macros"></a>Macros de mapa de eventos URL

Las macros siguientes se pueden usar para controlar eventos DHTML en [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-clases derivadas.

|||
|-|-|
|[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)|Marca el inicio del mapa de eventos DHTML y URL de varias páginas.|
|[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)|Marca el inicio de un mapa de eventos DHTML incrustado.|
|[BEGIN_URL_ENTRIES](#begin_url_entries)|Marca el inicio de un mapa de entrada de eventos de URL.|
|[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)|Declara el mapa de eventos DHTML y URL de varias páginas.|
|[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)|Marca el final del mapa de eventos DHTML y URL de varias páginas.|
|[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)|Marca el final de un mapa de eventos DHTML incrustado.|
|[END_URL_ENTRIES](#end_url_entries)|Marca el final de un mapa de entrada de eventos de URL.|
|[URL_EVENT_ENTRY](#url_event_entry)|Asigna una dirección URL o un recurso HTML a una página de un cuadro de diálogo de varias páginas.|

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="begin_dhtml_event_map"></a><a name="begin_dhtml_event_map"></a>BEGIN_DHTML_EVENT_MAP

Marca el principio del mapa de eventos DHTML cuando se `className`coloca en el archivo de origen para la clase identificada por .

```cpp
BEGIN_DHTML_EVENT_MAP(className)
```

### <a name="parameters"></a>Parámetros

*className*<br/>
El nombre de la clase que contiene el mapa de eventos DHTML. Esta clase debe derivar directa o indirectamente de [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) e incluir la [macro DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) dentro de su definición de clase.

### <a name="remarks"></a>Observaciones

Agregue un mapa de eventos DHTML `CDHtmlDialog` a la clase para proporcionar información que se puede usar para enrutar eventos desencadenados por elementos HTML o controles ActiveX en una página web a funciones de controlador de la clase.

Coloque la macro BEGIN_DHTML_EVENT_MAP en el archivo de implementación de la clase (.cpp) seguido de macros DHTML_EVENT para los eventos que la clase debe controlar (por ejemplo, DHTML_EVENT_ONMOUSEOVER para eventos de mouseover). Utilice la macro [END_DHTML_EVENT_MAP](#end_dhtml_event_map) para marcar el final del mapa de eventos. Estas macros implementan la siguiente función:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="begin_dhtml_event_map_inline"></a><a name="begin_dhtml_event_map_inline"></a>BEGIN_DHTML_EVENT_MAP_INLINE

Marca el principio del mapa de eventos DHTML dentro de la definición de clase para *className*.

```cpp
BEGIN_DHTML_EVENT_MAP_INLINE(className)
```

### <a name="parameters"></a>Parámetros

*className*<br/>
El nombre de la clase que contiene el mapa de eventos DHTML. Esta clase debe derivar directa o indirectamente de [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) e incluir la [macro DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) dentro de su definición de clase.

### <a name="remarks"></a>Observaciones

Agregue un mapa de eventos DHTML `CDHtmlDialog` a la clase para proporcionar información que se puede usar para enrutar eventos desencadenados por elementos HTML o controles ActiveX en una página web a funciones de controlador de la clase.

Coloque la macro BEGIN_DHTML_EVENT_MAP en el archivo de definición (.h) de la clase seguido de macros de DHTML_EVENT para los eventos que la clase debe controlar (por ejemplo, DHTML_EVENT_ONMOUSEOVER para eventos de mouseover). Utilice la macro [END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline) para marcar el final del mapa de eventos. Estas macros implementan la siguiente función:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="declare_dhtml_event_map"></a><a name="declare_dhtml_event_map"></a>DECLARE_DHTML_EVENT_MAP

Declara un mapa de eventos DHTML en una definición de clase.

```cpp
DECLARE_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>Observaciones

Esta macro se va a utilizar en la definición de [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-clases derivadas.

Utilice [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map) o [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline) para implementar el mapa.

[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) declara la siguiente función:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap( );`

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event"></a><a name="dhtml_event"></a>DHTML_EVENT

Controla (en el nivel de documento) un evento identificado por *dispid* originado por el elemento HTML identificado por *elemName*.

```cpp
DHTML_EVENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parámetros

*dispid*<br/>
El DISPID del evento que se va a controlar.

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento, o NULL para controlar los eventos de documento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_axcontrol"></a><a name="dhtml_event_axcontrol"></a>DHTML_EVENT_AXCONTROL

Controla el evento identificado por *dispid* desencadenado por el control ActiveX identificado por *controlName*.

```cpp
DHTML_EVENT_AXCONTROL(dispid, controlName,  memberFxn)
```

### <a name="parameters"></a>Parámetros

*dispid*<br/>
El id de envío del evento que se va a controlar.

*controlName*<br/>
Un LPCWSTR que contiene el identificador HTML del control que desencadena el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_class"></a><a name="dhtml_event_class"></a>DHTML_EVENT_CLASS

Controla (en el nivel de documento) un evento identificado por *dispid* originado por cualquier elemento HTML con la clase CSS identificada por *elemName*.

```cpp
DHTML_EVENT_CLASS(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parámetros

*dispid*<br/>
El id de envío del evento que se va a controlar.

*elemName*<br/>
Un LPCWSTR que contiene la clase CSS de los elementos HTML que abastecen el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_element"></a><a name="dhtml_event_element"></a>DHTML_EVENT_ELEMENT

Controla (en el elemento identificado por *elemName*) un evento identificado por *dispid*.

```cpp
DHTML_EVENT_ELEMENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parámetros

*dispid*<br/>
El id de envío del evento que se va a controlar.

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

Si esta macro se utiliza para controlar eventos no burbujbling, el origen del evento será el elemento identificado por *elemName*.

Si esta macro se utiliza para controlar eventos de propagación, el elemento identificado por *elemName* puede no ser el origen del evento (el origen podría ser cualquier elemento contenido por *elemName*).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_onafterupdate"></a><a name="dhtml_event_onafterupdate"></a>DHTML_EVENT_ONAFTERUPDATE

Controla (en el `onafterupdate` nivel de documento) el evento originado por el elemento HTML identificado por *elemName*.

```cpp
DHTML_EVENT_ONAFTERUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_onbeforeupdate"></a><a name="dhtml_event_onbeforeupdate"></a>DHTML_EVENT_ONBEFOREUPDATE

Controla (en el `onbeforeupdate` nivel de documento) el evento originado por el elemento HTML identificado por *elemName*.

```cpp
DHTML_EVENT_ONBEFOREUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_onblur"></a><a name="dhtml_event_onblur"></a>DHTML_EVENT_ONBLUR

Controla (en el `onblur` nivel de elemento) el evento. Este es un evento que no se burbujea.

```cpp
DHTML_EVENT_ONBLUR(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_onchange"></a><a name="dhtml_event_onchange"></a>DHTML_EVENT_ONCHANGE

Controla (en el `onchange` nivel de elemento) el evento. Este es un evento que no se burbujea.

```cpp
DHTML_EVENT_ONCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_onclick"></a><a name="dhtml_event_onclick"></a>DHTML_EVENT_ONCLICK

Controla (en el `onclick` nivel de documento) el evento originado por el elemento HTML identificado por *elemName*.

```cpp
DHTML_EVENT_ONCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_ondataavailable"></a><a name="dhtml_event_ondataavailable"></a>DHTML_EVENT_ONDATAAVAILABLE

Controla (en el `ondataavailable` nivel de documento) el evento originado por el elemento HTML identificado por *elemName*.

```cpp
DHTML_EVENT_ONDATAAVAILABLE(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_ondatasetchanged"></a><a name="dhtml_event_ondatasetchanged"></a>DHTML_EVENT_ONDATASETCHANGED

Controla (en el `ondatasetchanged` nivel de documento) el evento originado por el elemento HTML identificado por *elemName*.

```cpp
DHTML_EVENT_ONDATASETCHANGED(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_ondatasetcomplete"></a><a name="dhtml_event_ondatasetcomplete"></a>DHTML_EVENT_ONDATASETCOMPLETE

Controla (en el `ondatasetcomplete` nivel de documento) el `elemName`evento originado por el elemento HTML identificado por .

```cpp
DHTML_EVENT_ONDATASETCOMPLETE(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_ondblclick"></a><a name="dhtml_event_ondblclick"></a>DHTML_EVENT_ONDBLCLICK

Controla (en el `ondblclick` nivel de documento) el evento originado por el elemento HTML identificado por *elemName*.

```cpp
DHTML_EVENT_ONDBLCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_ondragstart"></a><a name="dhtml_event_ondragstart"></a>DHTML_EVENT_ONDRAGSTART

Controla (en el `ondragstart` nivel de documento) el evento originado por el elemento HTML identificado por *elemName*.

```cpp
DHTML_EVENT_ONDRAGSTART(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_onerrorupdate"></a><a name="dhtml_event_onerrorupdate"></a>DHTML_EVENT_ONERRORUPDATE

Controla (en el `onerrorupdate` nivel de documento) el evento originado por el elemento HTML identificado por *elemName*.

```cpp
DHTML_EVENT_ONERRORUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_onfilterchange"></a><a name="dhtml_event_onfilterchange"></a>DHTML_EVENT_ONFILTERCHANGE

Controla (en el `onfilterchange` nivel de documento) el evento originado por el elemento HTML identificado por *elemName*.

```cpp
DHTML_EVENT_ONFILTERCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_onfocus"></a><a name="dhtml_event_onfocus"></a>DHTML_EVENT_ONFOCUS

Controla (en el `onfocus` nivel de elemento) el evento. Este es un evento que no se burbujea.

```cpp
DHTML_EVENT_ONFOCUS(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_onhelp"></a><a name="dhtml_event_onhelp"></a>DHTML_EVENT_ONHELP

Controla (en el `onhelp` nivel de documento) el evento originado por el elemento HTML identificado por *elemName*.

```cpp
DHTML_EVENT_ONHELP(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_onkeydown"></a><a name="dhtml_event_onkeydown"></a>DHTML_EVENT_ONKEYDOWN

Controla (en el `onkeydown` nivel de documento) el evento originado por el elemento HTML identificado por *elemName*.

```cpp
DHTML_EVENT_ONKEYDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_onkeypress"></a><a name="dhtml_event_onkeypress"></a>DHTML_EVENT_ONKEYPRESS

Controla (en el `onkeypress` nivel de documento) el evento originado por el elemento HTML identificado por *elemName*.

```cpp
DHTML_EVENT_ONKEYPRESS(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_onkeyup"></a><a name="dhtml_event_onkeyup"></a>DHTML_EVENT_ONKEYUP

Controla (en el `onkeyup` nivel de documento) el evento originado por el elemento HTML identificado por *elemName*.

```cpp
DHTML_EVENT_ONKEYUP(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_onmousedown"></a><a name="dhtml_event_onmousedown"></a>DHTML_EVENT_ONMOUSEDOWN

Controla (en el `onmousedown` nivel de documento) el evento originado por el elemento HTML identificado por *elemName*.

```cpp
DHTML_EVENT_ONMOUSEDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_onmousemove"></a><a name="dhtml_event_onmousemove"></a>DHTML_EVENT_ONMOUSEMOVE

Controla (en el `onmousemove` nivel de documento) el evento originado por el elemento HTML identificado por *elemName*.

```cpp
DHTML_EVENT_ONMOUSEMOVE(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_onmouseout"></a><a name="dhtml_event_onmouseout"></a>DHTML_EVENT_ONMOUSEOUT

Controla (en el `onmouseout` nivel de documento) el evento originado por el elemento HTML identificado por *elemName*.

```cpp
DHTML_EVENT_ONMOUSEOUT(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_onmouseover"></a><a name="dhtml_event_onmouseover"></a>DHTML_EVENT_ONMOUSEOVER

Controla (en el `onmouseover` nivel de documento) el evento originado por el elemento HTML identificado por *elemName*.

```cpp
DHTML_EVENT_ONMOUSEOVER(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_onmouseup"></a><a name="dhtml_event_onmouseup"></a>DHTML_EVENT_ONMOUSEUP

Controla (en el `onmouseup` nivel de documento) el evento originado por el elemento HTML identificado por *elemName*.

```cpp
DHTML_EVENT_ONMOUSEUP(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_onresize"></a><a name="dhtml_event_onresize"></a>DHTML_EVENT_ONRESIZE

Controla (en el `onresize` nivel de elemento) el evento. Este es un evento que no se burbujea.

```cpp
DHTML_EVENT_ONRESIZE(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_onrowenter"></a><a name="dhtml_event_onrowenter"></a>DHTML_EVENT_ONROWENTER

Controla (en el `onrowenter` nivel de documento) el evento originado por el elemento HTML identificado por *elemName*.

```cpp
DHTML_EVENT_ONROWENTER(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_onrowexit"></a><a name="dhtml_event_onrowexit"></a>DHTML_EVENT_ONROWEXIT

Controla (en el `onrowexit` nivel de documento) el evento originado por el elemento HTML identificado por *elemName*.

```cpp
DHTML_EVENT_ONROWEXIT(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_onselectstart"></a><a name="dhtml_event_onselectstart"></a>DHTML_EVENT_ONSELECTSTART

Controla (en el `onselectstart` nivel de documento) el evento originado por el elemento HTML identificado por *elemName*.

```cpp
DHTML_EVENT_ONSELECTSTART(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML que obtiene el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="dhtml_event_tag"></a><a name="dhtml_event_tag"></a>DHTML_EVENT_TAG

Controla (en el nivel de `dispid` documento) un evento identificado por originado por cualquier elemento HTML con la etiqueta HTML identificada por *elemName*.

```cpp
DHTML_EVENT_TAG(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parámetros

*dispid*<br/>
El id de envío del evento que se va a controlar.

*elemName*<br/>
La etiqueta HTML de los elementos HTML que abastecen el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Observaciones

Utilice esta macro para agregar una entrada al mapa de [eventos DHTML](#begin_dhtml_event_map_inline) de la clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="end_dhtml_event_map"></a><a name="end_dhtml_event_map"></a>END_DHTML_EVENT_MAP

Marca el final del mapa de eventos DHTML.

```cpp
END_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>Observaciones

Debe utilizarse junto con [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="begin_dhtml_url_event_map"></a><a name="begin_dhtml_url_event_map"></a>BEGIN_DHTML_URL_EVENT_MAP

Inicia la definición de un mapa de eventos DHTML y URL en un cuadro de diálogo de varias páginas.

```cpp
BEGIN_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>Observaciones

Coloque BEGIN_DHTML_URL_EVENT_MAP en el archivo de implementación de la [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-clase derivada. Síguelo con mapas de [eventos DHTML incrustados](#begin_embed_dhtml_event_map) y entradas de [URL](#begin_url_entries)y, a continuación, ciérrelo con [END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map). Incluya la macro [DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map) dentro de la definición de clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#196](../../mfc/codesnippet/cpp/dhtml-event-maps_1.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="begin_embed_dhtml_event_map"></a><a name="begin_embed_dhtml_event_map"></a>BEGIN_EMBED_DHTML_EVENT_MAP

Inicia la definición de un mapa de eventos DHTML incrustado en un cuadro de diálogo de varias páginas.

```cpp
BEGIN_EMBED_DHTML_EVENT_MAP(className, mapName)
```

### <a name="parameters"></a>Parámetros

*className*<br/>
El nombre de la clase que contiene el mapa de eventos. Esta clase debe derivar directa o indirectamente de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). El mapa de eventos DHTML incrustado debe estar dentro de un mapa de [eventos DHTML y URL](#begin_dhtml_url_event_map)).

*mapName*<br/>
Especifica la página cuyo mapa de eventos es este. Esto coincide con *mapName* en la [macro URL_EVENT_ENTRY](#url_event_entry) que define realmente la dirección URL o el recurso HTML.

### <a name="remarks"></a>Observaciones

Dado que un cuadro de diálogo DHTML de varias páginas consta de varias páginas HTML, cada una de las cuales puede generar eventos DHTML, los mapas de eventos incrustados se usan para asignar eventos a controladores por página.

Los mapas de eventos incrustados dentro de un mapa de eventos DHTML y URL constan de una macro de BEGIN_EMBED_DHTML_EVENT_MAP seguida de macros [de DHTML_EVENT](#dhtml_event) y una macro [de END_EMBED_DHTML_EVENT_MAP.](#end_embed_dhtml_event_map)

Cada mapa de eventos incrustado requiere una entrada de [evento de dirección URL](#url_event_entry) correspondiente para asignar *mapName* (especificado en BEGIN_EMBED_DHTML_EVENT_MAP) a una dirección URL o un recurso HTML.

### <a name="example"></a>Ejemplo

Vea el ejemplo en [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="begin_url_entries"></a><a name="begin_url_entries"></a>BEGIN_URL_ENTRIES

Inicia la definición de un mapa de entrada de eventos URL en un cuadro de diálogo de varias páginas.

```cpp
BEGIN_URL_ENTRIES(className)
```

### <a name="parameters"></a>Parámetros

*className*<br/>
El nombre de la clase que contiene el mapa de entrada de eventos URL. Esta clase debe derivar directa o indirectamente de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). El mapa de entrada de eventos URL debe estar dentro de un mapa de eventos [DHTML y URL](#begin_dhtml_url_event_map)).

### <a name="remarks"></a>Observaciones

Dado que un cuadro de diálogo DHTML de varias páginas consta de varias páginas HTML, las entradas de eventos URL se utilizan para asignar direcciones URL o recursos HTML a los correspondientes mapas de [eventos DHTML incrustados.](#begin_embed_dhtml_event_map) Coloque URL_EVENT_ENTRY macros entre BEGIN_URL_ENTRIES y [END_URL_ENTRIES](#end_url_entries) macros.

### <a name="example"></a>Ejemplo

Vea el ejemplo en [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="declare_dhtml_url_event_map"></a><a name="declare_dhtml_url_event_map"></a>DECLARE_DHTML_URL_EVENT_MAP

Declara un mapa de eventos DHTML y URL en una definición de clase.

```cpp
DECLARE_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>Observaciones

Esta macro se va a utilizar en la definición de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-clases derivadas.

Un mapa de eventos DHTML y URL contiene mapas de [eventos DHTML incrustados](#begin_embed_dhtml_event_map) y entradas de [eventos DE dirección URL](#begin_url_entries) para asignar eventos DHTML a controladores por página. Utilice [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) para implementar el mapa.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="end_dhtml_url_event_map"></a><a name="end_dhtml_url_event_map"></a>END_DHTML_URL_EVENT_MAP

Marca el final de un mapa de eventos DHTML y URL.

```cpp
END_DHTML_URL_EVENT_MAP(className)
```

### <a name="parameters"></a>Parámetros

*className*<br/>
El nombre de la clase que contiene el mapa de eventos. Esta clase debe derivar directa o indirectamente de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Esto debe coincidir con *className* en la macro [de BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) correspondiente.

### <a name="example"></a>Ejemplo

Vea el ejemplo en [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="end_embed_dhtml_event_map"></a><a name="end_embed_dhtml_event_map"></a>END_EMBED_DHTML_EVENT_MAP

Marca el final de un mapa de eventos DHTML incrustado.

```cpp
END_EMBED_DHTML_EVENT_MAP()
```

### <a name="example"></a>Ejemplo

Vea el ejemplo en [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="end_url_entries"></a><a name="end_url_entries"></a>END_URL_ENTRIES

Marca el final de un mapa de entrada de eventos de URL.

```cpp
END_URL_ENTRIES()
```

### <a name="example"></a>Ejemplo

Vea el ejemplo en [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="url_event_entry"></a><a name="url_event_entry"></a>URL_EVENT_ENTRY

Asigna una dirección URL o un recurso HTML a una página de un cuadro de diálogo de varias páginas.

```cpp
URL_EVENT_ENTRY(className, url,  mapName)
```

### <a name="parameters"></a>Parámetros

*className*<br/>
El nombre de la clase que contiene el mapa de entrada de eventos URL. Esta clase debe derivar directa o indirectamente de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). El mapa de entrada de eventos URL debe estar dentro de un mapa de eventos [DHTML y URL](#begin_dhtml_url_event_map)).

*url*<br/>
La dirección URL o el recurso HTML de la página.

*mapName*<br/>
Especifica la página cuya dirección URL es *url*. Esto coincide con *mapName* en la [macro de BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map) que asigna eventos de esta página.

### <a name="remarks"></a>Observaciones

Si la página es un recurso HTML, *url* debe ser la representación de cadena del número de ID del recurso (es decir, "123", no 123 o ID_HTMLRES1).

El identificador de página, *mapName*, es un símbolo arbitrario que se utiliza para vincular mapas de eventos DHTML incrustados a mapas de entrada de eventos URL. Está limitado en el ámbito al mapa de eventos DHTML y URL.

### <a name="example"></a>Ejemplo

Vea el ejemplo en [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

## <a name="end_dhtml_event_map_inline"></a><a name="end_dhtml_event_map_inline"></a>END_DHTML_EVENT_MAP_INLINE

Marca el final del mapa de eventos DHTML.

### <a name="syntax"></a>Sintaxis

```cpp
END_DHTML_EVENT_MAP_INLINE( )
```

### <a name="remarks"></a>Observaciones

Debe utilizarse junto con [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdhtml.h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](mfc-macros-and-globals.md)
