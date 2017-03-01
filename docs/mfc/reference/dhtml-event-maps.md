---
title: Mapas de eventos DHTML | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.macros.shared
dev_langs:
- C++
helpviewer_keywords:
- event map macros
- DHTML, event map macros
- macros, DHTML event map
- DHTML events, event map
- DHTML events
ms.assetid: 9a2c8ae7-7216-4a5e-bc60-6b98695be0c6
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 8be59b52e06241651a2f605ab949efffd0e010d3
ms.lasthandoff: 02/24/2017

---
# <a name="dhtml-event-maps"></a>DHTML (Mapas de eventos)
Las macros siguientes pueden utilizarse para controlar eventos DHTML.  
  
## <a name="dhtml-event-map-macros"></a>Macros de mapa de eventos DHTML  
 Las macros siguientes pueden utilizarse para controlar los eventos DHTML en [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-las clases derivadas.  
  
|||  
|-|-|  
|[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)|Marca el inicio del mapa de eventos DHTML.|  
|[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)|Marca el inicio del mapa de eventos DHTML.|  
|[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)|Declara el mapa de eventos DHTML.|  
|[DHTML_EVENT](#dhtml_event)|Se utiliza para controlar un evento en el nivel de documento para un único elemento HTML.|  
|[DHTML_EVENT_AXCONTROL](#dhtml_event_axcontrol)|Se utiliza para controlar un evento desencadenado por un control ActiveX.|  
|[DHTML_EVENT_CLASS](#dhtml_event_class)|Se utiliza para controlar un evento en el nivel de documento para todos los elementos HTML a una clase concreta de CSS.|  
|[DHTML_EVENT_ELEMENT](#dhtml_event_element)|Se utiliza para controlar un evento en el nivel de elemento.|  
|[DHTML_EVENT_ONAFTERUPDATE](#dhtml_event_onafterupdate)|Utilizado para controlar la **onafterupdate** evento desde un elemento HTML.|  
|[DHTML_EVENT_ONBEFOREUPDATE](#dhtml_event_onbeforeupdate)|Utilizado para controlar la **onbeforeupdate** evento desde un elemento HTML.|  
|[DHTML_EVENT_ONBLUR](#dhtml_event_onblur)|Utilizado para controlar la **onblur** evento desde un elemento HTML.|  
|[DHTML_EVENT_ONCHANGE](#dhtml_event_onchange)|Utilizado para controlar la `onchange` evento desde un elemento HTML.|  
|[DHTML_EVENT_ONCLICK](#dhtml_event_onclick)|Utilizado para controlar la **onclick** evento desde un elemento HTML.|  
|[DHTML_EVENT_ONDATAAVAILABLE](#dhtml_event_ondataavailable)|Utilizado para controlar la **ondataavailable** evento desde un elemento HTML.|  
|[DHTML_EVENT_ONDATASETCHANGED](#dhtml_event_ondatasetchanged)|Utilizado para controlar la **ondatasetchanged** evento desde un elemento HTML.|  
|[DHTML_EVENT_ONDATASETCOMPLETE](#dhtml_event_ondatasetcomplete)|Utilizado para controlar la **ondatasetcomplete** evento desde un elemento HTML.|  
|[DHTML_EVENT_ONDBLCLICK](#dhtml_event_ondblclick)|Utilizado para controlar la **ondblclick** evento desde un elemento HTML.|  
|[DHTML_EVENT_ONDRAGSTART](#dhtml_event_ondragstart)|Utilizado para controlar la **ondragstart** evento desde un elemento HTML.|  
|[DHTML_EVENT_ONERRORUPDATE](#dhtml_event_onerrorupdate)|Utilizado para controlar la **onerrorupdate** evento desde un elemento HTML.|  
|[DHTML_EVENT_ONFILTERCHANGE](#dhtml_event_onfilterchange)|Utilizado para controlar la **onfilterchange** evento desde un elemento HTML.|  
|[DHTML_EVENT_ONFOCUS](#dhtml_event_onfocus)|Utilizado para controlar la **onfocus** evento desde un elemento HTML.|  
|[DHTML_EVENT_ONHELP](#dhtml_event_onhelp)|Utilizado para controlar la `onhelp` evento desde un elemento HTML.|  
|[DHTML_EVENT_ONKEYDOWN](#dhtml_event_onkeydown)|Utilizado para controlar la **onkeydown** evento desde un elemento HTML.|  
|[DHTML_EVENT_ONKEYPRESS](#dhtml_event_onkeypress)|Utilizado para controlar la **onkeypress** evento desde un elemento HTML.|  
|[DHTML_EVENT_ONKEYUP](#dhtml_event_onkeyup)|Utilizado para controlar la **onkeyup** evento desde un elemento HTML.|  
|[DHTML_EVENT_ONMOUSEDOWN](#dhtml_event_onmousedown)|Utilizado para controlar la **onmousedown** evento desde un elemento HTML.|  
|[DHTML_EVENT_ONMOUSEMOVE](#dhtml_event_onmousemove)|Utilizado para controlar la `onmousemove` evento desde un elemento HTML.|  
|[DHTML_EVENT_ONMOUSEOUT](#dhtml_event_onmouseout)|Utilizado para controlar la **onmouseout** evento desde un elemento HTML.|  
|[DHTML_EVENT_ONMOUSEOVER](#dhtml_event_onmouseover)|Utilizado para controlar la **onmouseover** evento desde un elemento HTML.|  
|[DHTML_EVENT_ONMOUSEUP](#dhtml_event_onmouseup)|Utilizado para controlar la **onmouseup** evento desde un elemento HTML.|  
|[DHTML_EVENT_ONRESIZE](#dhtml_event_onresize)|Utilizado para controlar la **onresize** evento desde un elemento HTML.|  
|[DHTML_EVENT_ONROWENTER](#dhtml_event_onrowenter)|Utilizado para controlar la **onrowenter** evento desde un elemento HTML.|  
|[DHTML_EVENT_ONROWEXIT](#dhtml_event_onrowexit)|Utilizado para controlar la **onrowexit** evento desde un elemento HTML.|  
|[DHTML_EVENT_ONSELECTSTART](#dhtml_event_onselectstart)|Utilizado para controlar la **onselectstart** evento desde un elemento HTML.|  
|[DHTML_EVENT_TAG](#dhtml_event_tag)|Se utiliza para controlar un evento en el nivel de documento para todos los elementos con una etiqueta HTML determinada.|  
|[END_DHTML_EVENT_MAP](#end_dhtml_event_map)|Marca el final del mapa de eventos DHTML.|  
  
## <a name="url-event-map-macros"></a>Macros de mapa de eventos de dirección URL  
 Las macros siguientes pueden utilizarse para controlar los eventos DHTML en [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-las clases derivadas.  
  
|||  
|-|-|  
|[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)|Marca el inicio de la asignación de eventos DHTML y la dirección URL de varias páginas.|  
|[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)|Marca el inicio de un mapa de eventos DHTML incrustado.|  
|[BEGIN_URL_ENTRIES](#begin_url_entries)|Marca el inicio de un mapa de entrada de eventos de dirección URL.|  
|[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)|Declara el mapa de eventos DHTML y la dirección URL de varias páginas.|  
|[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)|Marca el final de la asignación de eventos DHTML y la dirección URL de varias páginas.|  
|[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)|Marca el final de un mapa de eventos DHTML incrustado.|  
|[END_URL_ENTRIES](#end_url_entries)|Marca el final de una asignación de entrada de eventos de dirección URL.|  
|[URL_EVENT_ENTRY](#url_event_entry)|Asigna un recurso de dirección URL o HTML a una página en un cuadro de diálogo de varias páginas.|  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namebegindhtmleventmapa--begindhtmleventmap"></a><a name="begin_dhtml_event_map"></a>BEGIN_DHTML_EVENT_MAP  
 Marca el principio del mapa de eventos DHTML cuando se coloca en el archivo de código fuente para la clase identificada por `className`.  
  
```   
BEGIN_DHTML_EVENT_MAP(className)   
```  
  
### <a name="parameters"></a>Parámetros  
 `className`  
 El nombre de la clase que contiene el mapa de eventos DHTML. Esta clase debe derivar directa o indirectamente de [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) e incluya el [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) macro dentro de su definición de clase.  
  
### <a name="remarks"></a>Comentarios  
 Agregar un mapa de eventos DHTML a la clase para proporcionar información a **CDHtmlDialog** que se puede utilizar para enrutar los eventos desencadenados por los elementos HTML o controles ActiveX en una página web a las funciones de controlador en su clase.  
  
 Colocar el `BEGIN_DHTML_EVENT_MAP` seguido de macro en el archivo de implementación (.cpp) de la clase `DHTML_EVENT` macros para los eventos de la clase es controlar (por ejemplo, `DHTML_EVENT_ONMOUSEOVER` para eventos de mouseover). Utilice la [END_DHTML_EVENT_MAP](#end_dhtml_event_map) macro para marcar el final de la asignación de eventos. Estas macros implementan la siguiente función:  
  
 `virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namebegindhtmleventmapinlinea--begindhtmleventmapinline"></a><a name="begin_dhtml_event_map_inline"></a>BEGIN_DHTML_EVENT_MAP_INLINE  
 Marca el principio del mapa de eventos DHTML en la definición de clase para `className`.  
  
```   
BEGIN_DHTML_EVENT_MAP_INLINE(className)   
```  
  
### <a name="parameters"></a>Parámetros  
 `className`  
 El nombre de la clase que contiene el mapa de eventos DHTML. Esta clase debe derivar directa o indirectamente de [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) e incluya el [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) macro dentro de su definición de clase.  
  
### <a name="remarks"></a>Comentarios  
 Agregar un mapa de eventos DHTML a la clase para proporcionar información a **CDHtmlDialog** que se puede utilizar para enrutar los eventos desencadenados por los elementos HTML o controles ActiveX en una página web a las funciones de controlador en su clase.  
  
 Colocar el `BEGIN_DHTML_EVENT_MAP` seguido de macro en el archivo de definición (. h) de la clase `DHTML_EVENT` macros para los eventos de la clase es controlar (por ejemplo, `DHTML_EVENT_ONMOUSEOVER` para eventos de mouseover). Utilice la [END_DHTML_EVENT_MAP_INLINE](http://msdn.microsoft.com/library/0cfec092-20ee-49f3-bc38-56d6a5572db2) macro para marcar el final de la asignación de eventos. Estas macros implementan la siguiente función:  
  
 `virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  

  
##  <a name="a-namedeclaredhtmleventmapa--declaredhtmleventmap"></a><a name="declare_dhtml_event_map"></a>DECLARE_DHTML_EVENT_MAP  
 Declara un mapa de eventos DHTML en una definición de clase.  
  
```   
DECLARE_DHTML_EVENT_MAP()   
```  
  
### <a name="remarks"></a>Comentarios  
 Esta macro es que se usará en la definición de [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-las clases derivadas.  
  
 Utilice [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map) o [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline) para implementar la asignación.  
  
 [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) declara la función siguiente:  
  
 `virtual const DHtmlEventMapEntry* GetDHtmlEventMap( );`  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventa--dhtmlevent"></a><a name="dhtml_event"></a>DHTML_EVENT  
 Controla (en el nivel de documento) un evento identificado por `dispid` originadas por el elemento HTML identificado por `elemName`.  
  
```   
DHTML_EVENT(dispid, elemName,  memberFxn)   
```  
  
### <a name="parameters"></a>Parámetros  
 `dispid`  
 El DISPID de controlar el evento.  
  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML de origen del evento, o **NULL** para controlar los eventos de documento.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventaxcontrola--dhtmleventaxcontrol"></a><a name="dhtml_event_axcontrol"></a>DHTML_EVENT_AXCONTROL  
 Controla el evento identificado por `dispid` desencadenados por el control ActiveX identificado por `controlName`.  
  
```   
DHTML_EVENT_AXCONTROL(dispid, controlName,  memberFxn)  
```  
  
### <a name="parameters"></a>Parámetros  
 `dispid`  
 El identificador de envío de controlar el evento.  
  
 `controlName`  
 Un `LPCWSTR` que contiene el identificador HTML del control desencadenando el evento.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventclassa--dhtmleventclass"></a><a name="dhtml_event_class"></a>DHTML_EVENT_CLASS  
 Controla (en el nivel de documento) un evento identificado por `dispid` originado por cualquier elemento HTML con la clase CSS que se identifica mediante `elemName`.  
  
```   
DHTML_EVENT_CLASS(dispid, elemName,  memberFxn)   
```  
  
### <a name="parameters"></a>Parámetros  
 `dispid`  
 El identificador de envío de controlar el evento.  
  
 `elemName`  
 Un `LPCWSTR` que contiene la clase CSS de los elementos HTML de origen del evento.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventelementa--dhtmleventelement"></a><a name="dhtml_event_element"></a>DHTML_EVENT_ELEMENT  
 Handles (en el elemento identificado por `elemName`) un evento identificado por `dispid`.  
  
```   
DHTML_EVENT_ELEMENT(dispid, elemName,  memberFxn) 
```  
  
### <a name="parameters"></a>Parámetros  
 `dispid`  
 El identificador de envío de controlar el evento.  
  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
 Si se utiliza esta macro para controlar los eventos nonbubbling, el origen del evento será el elemento identificado por `elemName`.  
  
 Si se utiliza esta macro para controlar los eventos de propagación, el elemento identificado por `elemName` no puede ser el origen del evento (el origen puede ser cualquier elemento incluido en `elemName`).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventonafterupdatea--dhtmleventonafterupdate"></a><a name="dhtml_event_onafterupdate"></a>DHTML_EVENT_ONAFTERUPDATE  
 Handles (en el nivel de documento) del **onafterupdate** eventos originaron por el elemento HTML identificado por `elemName`.  
  
```   
DHTML_EVENT_ONAFTERUPDATE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parámetros  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventonbeforeupdatea--dhtmleventonbeforeupdate"></a><a name="dhtml_event_onbeforeupdate"></a>DHTML_EVENT_ONBEFOREUPDATE  
 Handles (en el nivel de documento) del **onbeforeupdate** eventos originaron por el elemento HTML identificado por `elemName`.  
  
```   
DHTML_EVENT_ONBEFOREUPDATE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parámetros  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventonblura--dhtmleventonblur"></a><a name="dhtml_event_onblur"></a>DHTML_EVENT_ONBLUR  
 Handles (en el nivel de elemento) la **onblur** eventos. Se trata de un evento nonbubbling.  
  
```   
DHTML_EVENT_ONBLUR(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parámetros  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventonchangea--dhtmleventonchange"></a><a name="dhtml_event_onchange"></a>DHTML_EVENT_ONCHANGE  
 Handles (en el nivel de elemento) el `onchange` eventos. Se trata de un evento nonbubbling.  
  
```   
DHTML_EVENT_ONCHANGE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parámetros  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventonclicka--dhtmleventonclick"></a><a name="dhtml_event_onclick"></a>DHTML_EVENT_ONCLICK  
 Handles (en el nivel de documento) del **onclick** eventos originaron por el elemento HTML identificado por `elemName`.  
  
```   
DHTML_EVENT_ONCLICK(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parámetros  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventondataavailablea--dhtmleventondataavailable"></a><a name="dhtml_event_ondataavailable"></a>DHTML_EVENT_ONDATAAVAILABLE  
 Handles (en el nivel de documento) del **ondataavailable** eventos originaron por el elemento HTML identificado por `elemName`.  
  
```   
DHTML_EVENT_ONDATAAVAILABLE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parámetros  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventondatasetchangeda--dhtmleventondatasetchanged"></a><a name="dhtml_event_ondatasetchanged"></a>DHTML_EVENT_ONDATASETCHANGED  
 Handles (en el nivel de documento) del **ondatasetchanged** eventos originaron por el elemento HTML identificado por `elemName`.  
  
```   
DHTML_EVENT_ONDATASETCHANGED(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parámetros  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventondatasetcompletea--dhtmleventondatasetcomplete"></a><a name="dhtml_event_ondatasetcomplete"></a>DHTML_EVENT_ONDATASETCOMPLETE  
 Handles (en el nivel de documento) del **ondatasetcomplete** eventos originaron por el elemento HTML identificado por `elemName`.  
  
```   
DHTML_EVENT_ONDATASETCOMPLETE(elemName, memberFxn) 
 
```  
  
### <a name="parameters"></a>Parámetros  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventondblclicka--dhtmleventondblclick"></a><a name="dhtml_event_ondblclick"></a>DHTML_EVENT_ONDBLCLICK  
 Handles (en el nivel de documento) del **ondblclick** eventos originaron por el elemento HTML identificado por `elemName`.  
  
```   
DHTML_EVENT_ONDBLCLICK(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parámetros  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventondragstarta--dhtmleventondragstart"></a><a name="dhtml_event_ondragstart"></a>DHTML_EVENT_ONDRAGSTART  
 Handles (en el nivel de documento) del **ondragstart** eventos originaron por el elemento HTML identificado por `elemName`.  
  
```   
DHTML_EVENT_ONDRAGSTART(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parámetros  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventonerrorupdatea--dhtmleventonerrorupdate"></a><a name="dhtml_event_onerrorupdate"></a>DHTML_EVENT_ONERRORUPDATE  
 Handles (en el nivel de documento) del **onerrorupdate** eventos originaron por el elemento HTML identificado por `elemName`.  
  
```   
DHTML_EVENT_ONERRORUPDATE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parámetros  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventonfilterchangea--dhtmleventonfilterchange"></a><a name="dhtml_event_onfilterchange"></a>DHTML_EVENT_ONFILTERCHANGE  
 Handles (en el nivel de documento) del **onfilterchange** eventos originaron por el elemento HTML identificado por `elemName`.  
  
```  
 
DHTML_EVENT_ONFILTERCHANGE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parámetros  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventonfocusa--dhtmleventonfocus"></a><a name="dhtml_event_onfocus"></a>DHTML_EVENT_ONFOCUS  
 Handles (en el nivel de elemento) la **onfocus** eventos. Se trata de un evento nonbubbling.  
  
```  
 
DHTML_EVENT_ONFOCUS(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parámetros  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventonhelpa--dhtmleventonhelp"></a><a name="dhtml_event_onhelp"></a>DHTML_EVENT_ONHELP  
 Handles (en el nivel de documento) del `onhelp` eventos originaron por el elemento HTML identificado por `elemName`.  
  
```  
 
DHTML_EVENT_ONHELP(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parámetros  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventonkeydowna--dhtmleventonkeydown"></a><a name="dhtml_event_onkeydown"></a>DHTML_EVENT_ONKEYDOWN  
 Handles (en el nivel de documento) del **onkeydown** eventos originaron por el elemento HTML identificado por `elemName`.  
  
```  
 
DHTML_EVENT_ONKEYDOWN(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parámetros  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventonkeypressa--dhtmleventonkeypress"></a><a name="dhtml_event_onkeypress"></a>DHTML_EVENT_ONKEYPRESS  
 Handles (en el nivel de documento) del **onkeypress** eventos originaron por el elemento HTML identificado por `elemName`.  
  
```  
 
DHTML_EVENT_ONKEYPRESS(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parámetros  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventonkeyupa--dhtmleventonkeyup"></a><a name="dhtml_event_onkeyup"></a>DHTML_EVENT_ONKEYUP  
 Handles (en el nivel de documento) del **onkeyup** eventos originaron por el elemento HTML identificado por `elemName`.  
  
```  
 
DHTML_EVENT_ONKEYUP(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parámetros  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventonmousedowna--dhtmleventonmousedown"></a><a name="dhtml_event_onmousedown"></a>DHTML_EVENT_ONMOUSEDOWN  
 Handles (en el nivel de documento) del **onmousedown** eventos originaron por el elemento HTML identificado por `elemName`.  
  
```  
 
DHTML_EVENT_ONMOUSEDOWN(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parámetros  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventonmousemovea--dhtmleventonmousemove"></a><a name="dhtml_event_onmousemove"></a>DHTML_EVENT_ONMOUSEMOVE  
 Handles (en el nivel de documento) del `onmousemove` eventos originaron por el elemento HTML identificado por `elemName`.  
  
```  
 
DHTML_EVENT_ONMOUSEMOVE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parámetros  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventonmouseouta--dhtmleventonmouseout"></a><a name="dhtml_event_onmouseout"></a>DHTML_EVENT_ONMOUSEOUT  
 Handles (en el nivel de documento) del **onmouseout** eventos originaron por el elemento HTML identificado por `elemName`.  
  
```  
 
DHTML_EVENT_ONMOUSEOUT(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parámetros  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventonmouseovera--dhtmleventonmouseover"></a><a name="dhtml_event_onmouseover"></a>DHTML_EVENT_ONMOUSEOVER  
 Handles (en el nivel de documento) del **onmouseover** eventos originaron por el elemento HTML identificado por `elemName`.  
  
```  
 
DHTML_EVENT_ONMOUSEOVER(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parámetros  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventonmouseupa--dhtmleventonmouseup"></a><a name="dhtml_event_onmouseup"></a>DHTML_EVENT_ONMOUSEUP  
 Handles (en el nivel de documento) del **onmouseup** eventos originaron por el elemento HTML identificado por `elemName`.  
  
```  
 
DHTML_EVENT_ONMOUSEUP(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parámetros  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventonresizea--dhtmleventonresize"></a><a name="dhtml_event_onresize"></a>DHTML_EVENT_ONRESIZE  
 Handles (en el nivel de elemento) la **onresize** eventos. Se trata de un evento nonbubbling.  
  
```  
 
DHTML_EVENT_ONRESIZE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parámetros  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventonrowentera--dhtmleventonrowenter"></a><a name="dhtml_event_onrowenter"></a>DHTML_EVENT_ONROWENTER  
 Handles (en el nivel de documento) del **onrowenter** eventos originaron por el elemento HTML identificado por `elemName`.  
  
```  
 
DHTML_EVENT_ONROWENTER(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parámetros  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventonrowexita--dhtmleventonrowexit"></a><a name="dhtml_event_onrowexit"></a>DHTML_EVENT_ONROWEXIT  
 Handles (en el nivel de documento) del **onrowexit** eventos originaron por el elemento HTML identificado por `elemName`.  
  
```  
 
DHTML_EVENT_ONROWEXIT(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parámetros  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventonselectstarta--dhtmleventonselectstart"></a><a name="dhtml_event_onselectstart"></a>DHTML_EVENT_ONSELECTSTART  
 Handles (en el nivel de documento) del **onselectstart** eventos originaron por el elemento HTML identificado por `elemName`.  
  
```  
 
DHTML_EVENT_ONSELECTSTART(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parámetros  
 `elemName`  
 Un `LPCWSTR` que contiene el identificador del elemento HTML que el evento de origen.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedhtmleventtaga--dhtmleventtag"></a><a name="dhtml_event_tag"></a>DHTML_EVENT_TAG  
 Controla (en el nivel de documento) un evento identificado por `dispid` originado por cualquier elemento HTML con la etiqueta HTML identificada por `elemName`.  
  
```   
DHTML_EVENT_TAG(dispid, elemName,  memberFxn)   
```  
  
### <a name="parameters"></a>Parámetros  
 `dispid`  
 El identificador de envío de controlar el evento.  
  
 `elemName`  
 La etiqueta HTML de los elementos HTML de origen del evento.  
  
 `memberFxn`  
 La función de controlador para el evento.  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para agregar una entrada a la [mapa de eventos DHTML](#begin_dhtml_event_map_inline) en su clase.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-nameenddhtmleventmapa--enddhtmleventmap"></a><a name="end_dhtml_event_map"></a>END_DHTML_EVENT_MAP  
 Marca el final del mapa de eventos DHTML.  
  
```   
END_DHTML_EVENT_MAP()   
```  
  
### <a name="remarks"></a>Comentarios  
 Debe utilizarse junto con [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namebegindhtmlurleventmapa--begindhtmlurleventmap"></a><a name="begin_dhtml_url_event_map"></a>BEGIN_DHTML_URL_EVENT_MAP  
 Inicia la definición de un mapa de eventos DHTML y la dirección URL en un cuadro de diálogo de varias páginas.  
  
```  
BEGIN_DHTML_URL_EVENT_MAP()  
 
```  
  
### <a name="remarks"></a>Comentarios  
 Poner `BEGIN_DHTML_URL_EVENT_MAP` en el archivo de implementación de su [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-clase derivada. Siga con [incrustado mapas de eventos DHTML](#begin_embed_dhtml_event_map) y [entradas de dirección URL](#begin_url_entries)y, a continuación, cierre con [END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map). Incluir el [DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map) macro dentro de la definición de clase.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#196;](../../mfc/codesnippet/cpp/dhtml-event-maps_1.cpp)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namebeginembeddhtmleventmapa--beginembeddhtmleventmap"></a><a name="begin_embed_dhtml_event_map"></a>BEGIN_EMBED_DHTML_EVENT_MAP  
 Inicia la definición de un mapa de eventos DHTML incrustado en un cuadro de diálogo de varias páginas.  
  
```  
BEGIN_EMBED_DHTML_EVENT_MAP(className, mapName)  
 
```  
  
### <a name="parameters"></a>Parámetros  
 `className`  
 El nombre de la clase que contiene el mapa de eventos. Esta clase debe derivar directa o indirectamente de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). El mapa de eventos DHTML incrustado debe estar dentro de un [mapa de eventos DHTML y la dirección URL](#begin_dhtml_url_event_map)).  
  
 *Nombredemapa*  
 Especifica la página cuyo evento asignar todo esto. Esto coincide con *Nombredemapa* en el [URL_EVENT_ENTRY](#url_event_entry) macro definir realmente el recurso de dirección URL o HTML.  
  
### <a name="remarks"></a>Comentarios  
 Porque un cuadro de diálogo de varias páginas DHTML consta de varias páginas HTML, cada uno de ellos puede provocar eventos DHTML, mapas de eventos incrustados se utilizan para asignar los eventos a los controladores en función de la página.  
  
 Mapas de eventos incrustados dentro de un mapa de eventos DHTML y URL constan de un `BEGIN_EMBED_DHTML_EVENT_MAP` macro seguida por [DHTML_EVENT](dhtml-event-maps.md#dhtml_event) macros y un [END_EMBED_DHTML_EVENT_MAP](dhtml-event-maps.md#end_embed_dhtml_event_map) (macro).  
  
 Cada mapa de eventos embedded requiere correspondiente [entrada de eventos de la dirección URL](#url_event_entry) asignar *Nombredemapa* (especificado en `BEGIN_EMBED_DHTML_EVENT_MAP`) a un recurso de dirección URL o HTML.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namebeginurlentriesa--beginurlentries"></a><a name="begin_url_entries"></a>BEGIN_URL_ENTRIES  
 Inicia la definición de un mapa de entrada de eventos de dirección URL en un cuadro de diálogo de varias páginas.  
  
```  
BEGIN_URL_ENTRIES(className)  
 
```  
  
### <a name="parameters"></a>Parámetros  
 `className`  
 El nombre de la clase que contiene la asignación de entrada de eventos de dirección URL. Esta clase debe derivar directa o indirectamente de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Mapa de entrada de eventos de la dirección URL debe estar dentro de un [mapa de eventos DHTML y la dirección URL](#begin_dhtml_url_event_map)).  
  
### <a name="remarks"></a>Comentarios  
 Dado que un cuadro de diálogo de varias páginas DHTML consta de varias páginas HTML, entradas de eventos de la dirección URL se utilizan para asignar direcciones URL o HTML recursos correspondiente [incrustado mapas de eventos DHTML](#begin_embed_dhtml_event_map). Poner `URL_EVENT_ENTRY` macros entre `BEGIN_URL_ENTRIES` y [END_URL_ENTRIES](#end_url_entries) macros.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-namedeclaredhtmlurleventmapa--declaredhtmlurleventmap"></a><a name="declare_dhtml_url_event_map"></a>DECLARE_DHTML_URL_EVENT_MAP  
 Declara un mapa de eventos DHTML y la dirección URL en una definición de clase.  
  
```  
DECLARE_DHTML_URL_EVENT_MAP()  
 
```  
  
### <a name="remarks"></a>Comentarios  
 Esta macro es que se usará en la definición de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-las clases derivadas.  
  
 Un mapa de eventos DHTML y la dirección URL contiene [incrustado mapas de eventos DHTML](#begin_embed_dhtml_event_map) y [entradas de eventos de la dirección URL](#begin_url_entries) asignar eventos DHTML a controladores en función de la página. Utilice [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) para implementar la asignación.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-nameenddhtmlurleventmapa--enddhtmlurleventmap"></a><a name="end_dhtml_url_event_map"></a>END_DHTML_URL_EVENT_MAP  
 Marca el final de un mapa de eventos DHTML y la dirección URL.  
  
```  
END_DHTML_URL_EVENT_MAP(className)  
 
```  
  
### <a name="parameters"></a>Parámetros  
 `className`  
 El nombre de la clase que contiene el mapa de eventos. Esta clase debe derivar directa o indirectamente de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Debe coincidir con `className` en el correspondiente [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) (macro).  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-nameendembeddhtmleventmapa--endembeddhtmleventmap"></a><a name="end_embed_dhtml_event_map"></a>END_EMBED_DHTML_EVENT_MAP  
 Marca el final de un mapa de eventos DHTML incrustado.  
  
```  
END_EMBED_DHTML_EVENT_MAP()  
 
```  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-nameendurlentriesa--endurlentries"></a><a name="end_url_entries"></a>END_URL_ENTRIES  
 Marca el final de una asignación de entrada de eventos de dirección URL.  
  
```  
END_URL_ENTRIES()  
 
```  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
  
##  <a name="a-nameurlevententrya--urlevententry"></a><a name="url_event_entry"></a>URL_EVENT_ENTRY  
 Asigna un recurso de dirección URL o HTML a una página en un cuadro de diálogo de varias páginas.  
  
```  
URL_EVENT_ENTRY(className, url,  mapName)   
```  
  
### <a name="parameters"></a>Parámetros  
 `className`  
 El nombre de la clase que contiene la asignación de entrada de eventos de dirección URL. Esta clase debe derivar directa o indirectamente de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Mapa de entrada de eventos de la dirección URL debe estar dentro de un [mapa de eventos DHTML y la dirección URL](#begin_dhtml_url_event_map)).  
  
 *dirección URL*  
 El recurso de dirección URL o HTML para la página.  
  
 *Nombredemapa*  
 Especifica la página cuya dirección URL es *url*. Esto coincide con *Nombredemapa* en el [BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map) macro que asigna los eventos de esta página.  
  
### <a name="remarks"></a>Comentarios  
 Si la página es un recurso HTML, *url* debe ser la representación de cadena del número de identificación del recurso (es decir, "123", 123 no o ID_HTMLRES1).  
  
 El identificador de la página, *Nombredemapa*, es un símbolo arbitrario que se utiliza para vincular incrustado mapas de eventos DHTML a mapas de entrada de eventos de dirección URL. Está limitado en el ámbito del mapa de eventos DHTML y la dirección URL.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).  

  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdhtml.h  
    
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)

