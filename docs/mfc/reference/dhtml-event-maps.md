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
ms.openlocfilehash: 329b4176ad4d24651a41b5321c26318cf2af30e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547204"
---
# <a name="dhtml-event-maps"></a>DHTML (Mapas de eventos)

Las siguientes macros pueden usarse para controlar eventos DHTML.

## <a name="dhtml-event-map-macros"></a>Macros de mapa de eventos DHTML

Las siguientes macros que pueden usarse para controlar eventos DHTML en [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-las clases derivadas.

|||
|-|-|
|[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)|Marca el inicio de la asignación de eventos DHTML.|
|[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)|Marca el inicio de la asignación de eventos DHTML.|
|[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)|Declara el mapa de eventos DHTML.|
|[DHTML_EVENT](#dhtml_event)|Se utiliza para controlar un evento en el nivel de documento para un solo elemento HTML.|
|[DHTML_EVENT_AXCONTROL](#dhtml_event_axcontrol)|Se utiliza para controlar un evento desencadenado por un control ActiveX.|
|[DHTML_EVENT_CLASS](#dhtml_event_class)|Se utiliza para controlar un evento en el nivel de documento para todos los elementos HTML con una clase CSS determinada.|
|[DHTML_EVENT_ELEMENT](#dhtml_event_element)|Se utiliza para controlar un evento en el nivel de elemento.|
|[DHTML_EVENT_ONAFTERUPDATE](#dhtml_event_onafterupdate)|Utilizado para controlar la `onafterupdate` evento desde un elemento HTML.|
|[DHTML_EVENT_ONBEFOREUPDATE](#dhtml_event_onbeforeupdate)|Utilizado para controlar la `onbeforeupdate` evento desde un elemento HTML.|
|[DHTML_EVENT_ONBLUR](#dhtml_event_onblur)|Utilizado para controlar la `onblur` evento desde un elemento HTML.|
|[DHTML_EVENT_ONCHANGE](#dhtml_event_onchange)|Utilizado para controlar la `onchange` evento desde un elemento HTML.|
|[DHTML_EVENT_ONCLICK](#dhtml_event_onclick)|Utilizado para controlar la `onclick` evento desde un elemento HTML.|
|[DHTML_EVENT_ONDATAAVAILABLE](#dhtml_event_ondataavailable)|Utilizado para controlar la `ondataavailable` evento desde un elemento HTML.|
|[DHTML_EVENT_ONDATASETCHANGED](#dhtml_event_ondatasetchanged)|Utilizado para controlar la `ondatasetchanged` evento desde un elemento HTML.|
|[DHTML_EVENT_ONDATASETCOMPLETE](#dhtml_event_ondatasetcomplete)|Utilizado para controlar la `ondatasetcomplete` evento desde un elemento HTML.|
|[DHTML_EVENT_ONDBLCLICK](#dhtml_event_ondblclick)|Utilizado para controlar la `ondblclick` evento desde un elemento HTML.|
|[DHTML_EVENT_ONDRAGSTART](#dhtml_event_ondragstart)|Utilizado para controlar la `ondragstart` evento desde un elemento HTML.|
|[DHTML_EVENT_ONERRORUPDATE](#dhtml_event_onerrorupdate)|Utilizado para controlar la `onerrorupdate` evento desde un elemento HTML.|
|[DHTML_EVENT_ONFILTERCHANGE](#dhtml_event_onfilterchange)|Utilizado para controlar la `onfilterchange` evento desde un elemento HTML.|
|[DHTML_EVENT_ONFOCUS](#dhtml_event_onfocus)|Utilizado para controlar la `onfocus` evento desde un elemento HTML.|
|[DHTML_EVENT_ONHELP](#dhtml_event_onhelp)|Utilizado para controlar la `onhelp` evento desde un elemento HTML.|
|[DHTML_EVENT_ONKEYDOWN](#dhtml_event_onkeydown)|Utilizado para controlar la `onkeydown` evento desde un elemento HTML.|
|[DHTML_EVENT_ONKEYPRESS](#dhtml_event_onkeypress)|Utilizado para controlar la `onkeypress` evento desde un elemento HTML.|
|[DHTML_EVENT_ONKEYUP](#dhtml_event_onkeyup)|Utilizado para controlar la `onkeyup` evento desde un elemento HTML.|
|[DHTML_EVENT_ONMOUSEDOWN](#dhtml_event_onmousedown)|Utilizado para controlar la `onmousedown` evento desde un elemento HTML.|
|[DHTML_EVENT_ONMOUSEMOVE](#dhtml_event_onmousemove)|Utilizado para controlar la `onmousemove` evento desde un elemento HTML.|
|[DHTML_EVENT_ONMOUSEOUT](#dhtml_event_onmouseout)|Utilizado para controlar la `onmouseout` evento desde un elemento HTML.|
|[DHTML_EVENT_ONMOUSEOVER](#dhtml_event_onmouseover)|Utilizado para controlar la `onmouseover` evento desde un elemento HTML.|
|[DHTML_EVENT_ONMOUSEUP](#dhtml_event_onmouseup)|Utilizado para controlar la `onmouseup` evento desde un elemento HTML.|
|[DHTML_EVENT_ONRESIZE](#dhtml_event_onresize)|Utilizado para controlar la `onresize` evento desde un elemento HTML.|
|[DHTML_EVENT_ONROWENTER](#dhtml_event_onrowenter)|Utilizado para controlar la `onrowenter` evento desde un elemento HTML.|
|[DHTML_EVENT_ONROWEXIT](#dhtml_event_onrowexit)|Utilizado para controlar la `onrowexit` evento desde un elemento HTML.|
|[DHTML_EVENT_ONSELECTSTART](#dhtml_event_onselectstart)|Utilizado para controlar la `onselectstart` evento desde un elemento HTML.|
|[DHTML_EVENT_TAG](#dhtml_event_tag)|Se utiliza para controlar un evento en el nivel de documento para todos los elementos con una etiqueta HTML determinada.|
|[END_DHTML_EVENT_MAP](#end_dhtml_event_map)|Marca el final de la asignación de eventos DHTML.|
|[END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)|Marca el final de la asignación de eventos DHTML. |

## <a name="url-event-map-macros"></a>Macros de mapa de eventos de dirección URL

Las siguientes macros que pueden usarse para controlar eventos DHTML en [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-las clases derivadas.

|||
|-|-|
|[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)|Marca el inicio de la asignación de eventos DHTML y la dirección URL de varias páginas.|
|[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)|Marca el inicio de un mapa de eventos DHTML incrustado.|
|[BEGIN_URL_ENTRIES](#begin_url_entries)|Marca el inicio de una asignación de entrada de evento de dirección URL.|
|[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)|Declara el mapa de eventos DHTML y la dirección URL de varias páginas.|
|[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)|Marca el final de la asignación de eventos DHTML y la dirección URL de varias páginas.|
|[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)|Marca el final de un mapa de eventos DHTML incrustado.|
|[END_URL_ENTRIES](#end_url_entries)|Marca el final de una asignación de entrada de evento de dirección URL.|
|[URL_EVENT_ENTRY](#url_event_entry)|Asigna un recurso de dirección URL o HTML a una página en un cuadro de diálogo de varias páginas.|

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="begin_dhtml_event_map"></a>  BEGIN_DHTML_EVENT_MAP

Marca el principio de la asignación de eventos DHTML cuando se coloca en el archivo de origen para la clase identificada por `className`.

```
BEGIN_DHTML_EVENT_MAP(className)
```

### <a name="parameters"></a>Parámetros

*nombre de clase*<br/>
El nombre de la clase que contiene el mapa de eventos DHTML. Esta clase debe derivar directa o indirectamente de [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) e incluyen el [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) macro dentro de su definición de clase.

### <a name="remarks"></a>Comentarios

Agregar un mapa de eventos DHTML a la clase para proporcionar información a `CDHtmlDialog` que se puede utilizar para enrutar eventos desencadenados por los elementos HTML o controles ActiveX en una página web para funciones de controlador en la clase.

Coloque el begin_dhtml_event_map (macro) en el archivo de implementación (.cpp) de la clase seguido de macros DHTML_EVENT para los eventos de que la clase es controlar (por ejemplo, DHTML_EVENT_ONMOUSEOVER para eventos de mouseover). Use la [END_DHTML_EVENT_MAP](#end_dhtml_event_map) macro para marcar el final de la asignación de eventos. Estas macros implementan la función siguiente:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="begin_dhtml_event_map_inline"></a>  BEGIN_DHTML_EVENT_MAP_INLINE

Marca el principio de la asignación de eventos DHTML dentro de la definición de clase *className*.

```
BEGIN_DHTML_EVENT_MAP_INLINE(className)
```

### <a name="parameters"></a>Parámetros

*nombre de clase*<br/>
El nombre de la clase que contiene el mapa de eventos DHTML. Esta clase debe derivar directa o indirectamente de [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) e incluyen el [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) macro dentro de su definición de clase.

### <a name="remarks"></a>Comentarios

Agregar un mapa de eventos DHTML a la clase para proporcionar información a `CDHtmlDialog` que se puede utilizar para enrutar eventos desencadenados por los elementos HTML o controles ActiveX en una página web para funciones de controlador en la clase.

Coloque el begin_dhtml_event_map (macro) en el archivo de definición (. h) de la clase seguido de macros DHTML_EVENT para los eventos de que la clase es controlar (por ejemplo, DHTML_EVENT_ONMOUSEOVER para eventos de mouseover). Use la [END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline) macro para marcar el final de la asignación de eventos. Estas macros implementan la función siguiente:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="declare_dhtml_event_map"></a>  DECLARE_DHTML_EVENT_MAP

Declara un mapa de eventos DHTML en una definición de clase.

```
DECLARE_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>Comentarios

Esta macro es que se usará en la definición de [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-las clases derivadas.

Use [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map) o [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline) para implementar la asignación.

[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) declara la función siguiente:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap( );`

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event"></a>  DHTML_EVENT

Controla (en el nivel de documento), un evento identificado por *dispid* se originan en el elemento HTML identificado por *elemName*.

```
DHTML_EVENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parámetros

*DISPID*<br/>
El DISPID de controlar el evento.

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento, o NULL para controlar los eventos de documento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_axcontrol"></a>  DHTML_EVENT_AXCONTROL

Controla el evento identificado por *dispid* desencadenados por el control ActiveX identificado por *controlName*.

```
DHTML_EVENT_AXCONTROL(dispid, controlName,  memberFxn)
```

### <a name="parameters"></a>Parámetros

*DISPID*<br/>
Identificador de envío de controlar el evento.

*controlName*<br/>
Un LPCWSTR que contiene el identificador HTML del control desencadenando el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_class"></a>  DHTML_EVENT_CLASS

Controla (en el nivel de documento), un evento identificado por *dispid* se originan en cualquier elemento HTML con la clase CSS que se identifica mediante *elemName*.

```
DHTML_EVENT_CLASS(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parámetros

*DISPID*<br/>
Identificador de envío de controlar el evento.

*elemName*<br/>
Un LPCWSTR que contiene la clase CSS de los elementos HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_element"></a>  DHTML_EVENT_ELEMENT

Controla (en el elemento identificado por *elemName*) un evento identificado por *dispid*.

```
DHTML_EVENT_ELEMENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parámetros

*DISPID*<br/>
Identificador de envío de controlar el evento.

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

Si esta macro se usa para controlar los eventos nonbubbling, el origen del evento será el elemento identificado por *elemName*.

Si esta macro se usa para controlar los eventos de propagación, el elemento identificado por *elemName* no puede ser el origen del evento (el origen puede ser cualquier elemento incluido en *elemName*).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_onafterupdate"></a>  DHTML_EVENT_ONAFTERUPDATE

Controla (en el nivel de documento) la `onafterupdate` se originó el evento por el elemento HTML identificado por *elemName*.

```
DHTML_EVENT_ONAFTERUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_onbeforeupdate"></a>  DHTML_EVENT_ONBEFOREUPDATE

Controla (en el nivel de documento) la `onbeforeupdate` se originó el evento por el elemento HTML identificado por *elemName*.

```
DHTML_EVENT_ONBEFOREUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_onblur"></a>  DHTML_EVENT_ONBLUR

Controla (en el nivel de elemento) el `onblur` eventos. Se trata de un evento nonbubbling.

```
DHTML_EVENT_ONBLUR(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_onchange"></a>  DHTML_EVENT_ONCHANGE

Controla (en el nivel de elemento) el `onchange` eventos. Se trata de un evento nonbubbling.

```
DHTML_EVENT_ONCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_onclick"></a>  DHTML_EVENT_ONCLICK

Controla (en el nivel de documento) la `onclick` se originó el evento por el elemento HTML identificado por *elemName*.

```
DHTML_EVENT_ONCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_ondataavailable"></a>  DHTML_EVENT_ONDATAAVAILABLE

Controla (en el nivel de documento) la `ondataavailable` se originó el evento por el elemento HTML identificado por *elemName*.

```
DHTML_EVENT_ONDATAAVAILABLE(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_ondatasetchanged"></a>  DHTML_EVENT_ONDATASETCHANGED

Controla (en el nivel de documento) la `ondatasetchanged` se originó el evento por el elemento HTML identificado por *elemName*.

```
DHTML_EVENT_ONDATASETCHANGED(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_ondatasetcomplete"></a>  DHTML_EVENT_ONDATASETCOMPLETE

Controla (en el nivel de documento) la `ondatasetcomplete` se originó el evento por el elemento HTML identificado por `elemName`.

```
DHTML_EVENT_ONDATASETCOMPLETE(elemName, memberFxn)

```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_ondblclick"></a>  DHTML_EVENT_ONDBLCLICK

Controla (en el nivel de documento) la `ondblclick` se originó el evento por el elemento HTML identificado por *elemName*.

```
DHTML_EVENT_ONDBLCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_ondragstart"></a>  DHTML_EVENT_ONDRAGSTART

Controla (en el nivel de documento) la `ondragstart` se originó el evento por el elemento HTML identificado por *elemName*.

```
DHTML_EVENT_ONDRAGSTART(elemName, memberFxn)
```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_onerrorupdate"></a>  DHTML_EVENT_ONERRORUPDATE

Controla (en el nivel de documento) la `onerrorupdate` se originó el evento por el elemento HTML identificado por *elemName*.

```
DHTML_EVENT_ONERRORUPDATE(elemName, memberFxn)

```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_onfilterchange"></a>  DHTML_EVENT_ONFILTERCHANGE

Controla (en el nivel de documento) la `onfilterchange` se originó el evento por el elemento HTML identificado por *elemName*.

```

DHTML_EVENT_ONFILTERCHANGE(elemName, memberFxn)

```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_onfocus"></a>  DHTML_EVENT_ONFOCUS

Controla (en el nivel de elemento) el `onfocus` eventos. Se trata de un evento nonbubbling.

```

DHTML_EVENT_ONFOCUS(elemName, memberFxn)

```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_onhelp"></a>  DHTML_EVENT_ONHELP

Controla (en el nivel de documento) la `onhelp` se originó el evento por el elemento HTML identificado por *elemName*.

```

DHTML_EVENT_ONHELP(elemName, memberFxn)

```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_onkeydown"></a>  DHTML_EVENT_ONKEYDOWN

Controla (en el nivel de documento) la `onkeydown` se originó el evento por el elemento HTML identificado por *elemName*.

```

DHTML_EVENT_ONKEYDOWN(elemName, memberFxn)

```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_onkeypress"></a>  DHTML_EVENT_ONKEYPRESS

Controla (en el nivel de documento) la `onkeypress` se originó el evento por el elemento HTML identificado por *elemName*.

```

DHTML_EVENT_ONKEYPRESS(elemName, memberFxn)

```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_onkeyup"></a>  DHTML_EVENT_ONKEYUP

Controla (en el nivel de documento) la `onkeyup` se originó el evento por el elemento HTML identificado por *elemName*.

```

DHTML_EVENT_ONKEYUP(elemName, memberFxn)

```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_onmousedown"></a>  DHTML_EVENT_ONMOUSEDOWN

Controla (en el nivel de documento) la `onmousedown` se originó el evento por el elemento HTML identificado por *elemName*.

```

DHTML_EVENT_ONMOUSEDOWN(elemName, memberFxn)

```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_onmousemove"></a>  DHTML_EVENT_ONMOUSEMOVE

Controla (en el nivel de documento) la `onmousemove` se originó el evento por el elemento HTML identificado por *elemName*.

```

DHTML_EVENT_ONMOUSEMOVE(elemName, memberFxn)

```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_onmouseout"></a>  DHTML_EVENT_ONMOUSEOUT

Controla (en el nivel de documento) la `onmouseout` se originó el evento por el elemento HTML identificado por *elemName*.

```

DHTML_EVENT_ONMOUSEOUT(elemName, memberFxn)

```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_onmouseover"></a>  DHTML_EVENT_ONMOUSEOVER

Controla (en el nivel de documento) la `onmouseover` se originó el evento por el elemento HTML identificado por *elemName*.

```

DHTML_EVENT_ONMOUSEOVER(elemName, memberFxn)

```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_onmouseup"></a>  DHTML_EVENT_ONMOUSEUP

Controla (en el nivel de documento) la `onmouseup` se originó el evento por el elemento HTML identificado por *elemName*.

```

DHTML_EVENT_ONMOUSEUP(elemName, memberFxn)

```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_onresize"></a>  DHTML_EVENT_ONRESIZE

Controla (en el nivel de elemento) el `onresize` eventos. Se trata de un evento nonbubbling.

```

DHTML_EVENT_ONRESIZE(elemName, memberFxn)

```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_onrowenter"></a>  DHTML_EVENT_ONROWENTER

Controla (en el nivel de documento) la `onrowenter` se originó el evento por el elemento HTML identificado por *elemName*.

```

DHTML_EVENT_ONROWENTER(elemName, memberFxn)

```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_onrowexit"></a>  DHTML_EVENT_ONROWEXIT

Controla (en el nivel de documento) la `onrowexit` se originó el evento por el elemento HTML identificado por *elemName*.

```

DHTML_EVENT_ONROWEXIT(elemName, memberFxn)

```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_onselectstart"></a>  DHTML_EVENT_ONSELECTSTART

Controla (en el nivel de documento) la `onselectstart` se originó el evento por el elemento HTML identificado por *elemName*.

```

DHTML_EVENT_ONSELECTSTART(elemName, memberFxn)

```

### <a name="parameters"></a>Parámetros

*elemName*<br/>
Un LPCWSTR que contiene el identificador del elemento HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="dhtml_event_tag"></a>  DHTML_EVENT_TAG

Controla (en el nivel de documento), un evento identificado por `dispid` se originan en cualquier elemento HTML con la etiqueta HTML identificada por *elemName*.

```
DHTML_EVENT_TAG(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parámetros

*DISPID*<br/>
Identificador de envío de controlar el evento.

*elemName*<br/>
La etiqueta HTML de los elementos HTML abastecimiento el evento.

*memberFxn*<br/>
La función de controlador para el evento.

### <a name="remarks"></a>Comentarios

Use esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="end_dhtml_event_map"></a>  END_DHTML_EVENT_MAP

Marca el final de la asignación de eventos DHTML.

```
END_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>Comentarios

Debe usarse junto con [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="begin_dhtml_url_event_map"></a>  BEGIN_DHTML_URL_EVENT_MAP

Inicia la definición de un mapa de eventos DHTML y la dirección URL en un cuadro de diálogo de varias páginas.

```
BEGIN_DHTML_URL_EVENT_MAP()

```

### <a name="remarks"></a>Comentarios

Colocar BEGIN_DHTML_URL_EVENT_MAP en el archivo de implementación de su [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-clase derivada. Siga con [incrustar los mapas de eventos DHTML](#begin_embed_dhtml_event_map) y [entradas de dirección URL](#begin_url_entries)y, a continuación, ciérrelo con [END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map). Incluir el [DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map) macro dentro de la definición de clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#196](../../mfc/codesnippet/cpp/dhtml-event-maps_1.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="begin_embed_dhtml_event_map"></a>  BEGIN_EMBED_DHTML_EVENT_MAP

Inicia la definición de un mapa de eventos DHTML incrustado en un cuadro de diálogo de varias páginas.

```
BEGIN_EMBED_DHTML_EVENT_MAP(className, mapName)

```

### <a name="parameters"></a>Parámetros

*nombre de clase*<br/>
El nombre de la clase que contiene el mapa de eventos. Esta clase debe derivar directa o indirectamente de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). El mapa de eventos DHTML incrustado debe estar dentro de un [mapa de eventos DHTML y la dirección URL](#begin_dhtml_url_event_map)).

*Nombredemapa*<br/>
Especifica la página cuyo evento asignarlo. Esto coincide con *Nombredemapa* en el [URL_EVENT_ENTRY](#url_event_entry) macro definir realmente el recurso de dirección URL o HTML.

### <a name="remarks"></a>Comentarios

Porque un cuadro de diálogo de varias páginas DHTML consta de varias páginas HTML, cada uno de los cuales puede provocar eventos DHTML, mapas de eventos incrustados se usan para asignar los eventos a los controladores por página.

Mapas de eventos incrustado dentro de un mapa de eventos DHTML y la dirección URL constan de begin_embed_dhtml_event_map (macro) seguido por [DHTML_EVENT](#dhtml_event) macros y un [END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map) macro.

Cada mapa de eventos embedded requiere correspondiente [entrada de evento de la dirección URL](#url_event_entry) para asignar *Nombredemapa* (especificado en BEGIN_EMBED_DHTML_EVENT_MAP) a un recurso de dirección URL o HTML.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="begin_url_entries"></a>  BEGIN_URL_ENTRIES

Inicia la definición de una asignación de entrada de evento de dirección URL en un cuadro de diálogo de varias páginas.

```
BEGIN_URL_ENTRIES(className)

```

### <a name="parameters"></a>Parámetros

*nombre de clase*<br/>
El nombre de la clase que contiene la asignación de entrada de evento de dirección URL. Esta clase debe derivar directa o indirectamente de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Mapa de entrada de eventos de la dirección URL debe estar dentro de un [mapa de eventos DHTML y la dirección URL](#begin_dhtml_url_event_map)).

### <a name="remarks"></a>Comentarios

Dado que un cuadro de diálogo de varias páginas DHTML consta de varias páginas HTML, entradas de eventos de la dirección URL se usan para asignar las direcciones URL o HTML recursos a correspondientes [incrustar los mapas de eventos DHTML](#begin_embed_dhtml_event_map). Colocar macros URL_EVENT_ENTRY entre BEGIN_URL_ENTRIES y [END_URL_ENTRIES](#end_url_entries) macros.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="declare_dhtml_url_event_map"></a>  DECLARE_DHTML_URL_EVENT_MAP

Declara un mapa de eventos DHTML y la dirección URL en una definición de clase.

```
DECLARE_DHTML_URL_EVENT_MAP()

```

### <a name="remarks"></a>Comentarios

Esta macro es que se usará en la definición de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-las clases derivadas.

Contiene un mapa de eventos DHTML y la dirección URL [incrustar los mapas de eventos DHTML](#begin_embed_dhtml_event_map) y [entradas de eventos de la dirección URL](#begin_url_entries) a DHTML (eventos) se asignan a los controladores por página. Use [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) para implementar la asignación.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="end_dhtml_url_event_map"></a>  END_DHTML_URL_EVENT_MAP

Marca el final de un mapa de eventos DHTML y la dirección URL.

```
END_DHTML_URL_EVENT_MAP(className)

```

### <a name="parameters"></a>Parámetros

*nombre de clase*<br/>
El nombre de la clase que contiene el mapa de eventos. Esta clase debe derivar directa o indirectamente de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Debe coincidir con *className* en las correspondientes [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) macro.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="end_embed_dhtml_event_map"></a>  END_EMBED_DHTML_EVENT_MAP

Marca el final de un mapa de eventos DHTML incrustado.

```
END_EMBED_DHTML_EVENT_MAP()

```

### <a name="example"></a>Ejemplo

Vea el ejemplo de [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="end_url_entries"></a>  END_URL_ENTRIES

Marca el final de una asignación de entrada de evento de dirección URL.

```
END_URL_ENTRIES()

```

### <a name="example"></a>Ejemplo

Vea el ejemplo de [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="url_event_entry"></a>  URL_EVENT_ENTRY

Asigna un recurso de dirección URL o HTML a una página en un cuadro de diálogo de varias páginas.

```
URL_EVENT_ENTRY(className, url,  mapName)
```

### <a name="parameters"></a>Parámetros

*nombre de clase*<br/>
El nombre de la clase que contiene la asignación de entrada de evento de dirección URL. Esta clase debe derivar directa o indirectamente de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Mapa de entrada de eventos de la dirección URL debe estar dentro de un [mapa de eventos DHTML y la dirección URL](#begin_dhtml_url_event_map)).

*Dirección URL*<br/>
El recurso de dirección URL o HTML para la página.

*Nombredemapa*<br/>
Especifica la página cuya dirección URL es *url*. Esto coincide con *Nombredemapa* en el [BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map) macro que se asigna a los eventos de esta página.

### <a name="remarks"></a>Comentarios

Si la página es un recurso HTML, *url* debe ser la representación de cadena del número de Id. del recurso (es decir, "123", 123 no o ID_HTMLRES1).

El identificador de página, *Nombredemapa*, es un símbolo arbitrario que se utiliza para vincular incrustado mapas de eventos DHTML para asignaciones de entrada de evento de URL. Está limitada en el ámbito para el mapa de eventos DHTML y la dirección URL.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdhtml.h

##  <a name="end_dhtml_event_map_inline"></a>END_DHTML_EVENT_MAP_INLINE

Marca el final de la asignación de eventos DHTML.

### <a name="syntax"></a>Sintaxis

```
END_DHTML_EVENT_MAP_INLINE( )
```

### <a name="remarks"></a>Comentarios

Debe usarse junto con [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdhtml.h

### <a name="see-also"></a>Vea también

[Macros y funciones globales](mfc-macros-and-globals.md)
