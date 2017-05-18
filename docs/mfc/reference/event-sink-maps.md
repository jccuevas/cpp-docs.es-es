---
title: Mapas de receptor de eventos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- event sink maps
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 33bf66d18b499787a34b2da501bb3e8ead255459
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="event-sink-maps"></a>Mapas de receptor de eventos
Cuando un control OLE incrustado desencadena un evento, el contenedor del control recibe el evento mediante un mecanismo, denominado "receptor mapa de eventos," proporcionado por MFC. Este mapa de receptores de eventos designa las funciones de controlador para cada evento específico, así como parámetros de esos eventos. Para obtener más información sobre mapas de receptor de eventos, vea el artículo [contenedores de controles ActiveX](../../mfc/activex-control-containers.md).  
  
### <a name="event-sink-maps"></a>Mapas de receptor de eventos  
  
|||  
|-|-|  
|[BEGIN_EVENTSINK_MAP](#begin_eventsink_map)|Inicia la definición de un mapa de receptores de eventos.|  
|[DECLARE_EVENTSINK_MAP](#declare_eventsink_map)|Declara un mapa de receptores de eventos.|  
|[END_EVENTSINK_MAP](#end_eventsink_map)|Termina la definición de un mapa de receptores de eventos.|  
|[ON_EVENT](#on_event)|Define un controlador de eventos para un evento específico.|  
|[ON_EVENT_RANGE](#on_event_range)|Define un controlador de eventos para un evento específico desencadenado desde un conjunto de controles OLE.|  
|[ON_EVENT_REFLECT](#on_event_reflect)|Recibe los eventos desencadenados por el control antes de que están controlados por el contenedor del control.|  
|[ON_PROPNOTIFY](#on_propnotify)|Define un controlador para controlar las notificaciones de la propiedad de un control OLE.|  
|[ON_PROPNOTIFY_RANGE](#on_propnotify_range)|Define un controlador para controlar las notificaciones de propiedades de un conjunto de controles OLE.|  
|[ON_PROPNOTIFY_REFLECT](#on_propnotify_reflect)|Recibe notificaciones de propiedad enviadas por el control antes de que están controlados por el contenedor del control.|  
  
##  <a name="begin_eventsink_map"></a>BEGIN_EVENTSINK_MAP  
 Inicia la definición de la asignación de receptor de eventos.  
  
```   
BEGIN_EVENTSINK_MAP(theClass, baseClass)  
```  
  
### <a name="parameters"></a>Parámetros  
 `theClass`  
 Especifica el nombre de la clase control asignarlas cuyo receptor de eventos.  
  
 `baseClass`  
 Especifica el nombre de la clase base de `theClass`.  
  
### <a name="remarks"></a>Comentarios  
 En el archivo de implementación (.cpp) que define las funciones de miembro para la clase, iniciar el mapa de receptores de eventos con el `BEGIN_EVENTSINK_MAP` (macro), a continuación, agregue entradas de macro para cada evento se le notifiquen y completar el mapa de receptores de eventos con el `END_EVENTSINK_MAP` (macro).  
  
 Para obtener más información sobre mapas de receptor de eventos y los contenedores de controles OLE, vea el artículo [contenedores de controles ActiveX](../../mfc/activex-control-containers.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="declare_eventsink_map"></a>DECLARE_EVENTSINK_MAP  
 Un contenedor OLE puede proporcionar un mapa de receptores de eventos para especificar los eventos que se le notificará el contenedor.  
  
```   
DECLARE_EVENTSINK_MAP()   
```  
  
### <a name="remarks"></a>Comentarios  
 Utilice la `DECLARE_EVENTSINK_MAP` macro al final de la declaración de clase. A continuación, en el. Archivo CPP que define el miembro de las funciones de la clase, use la `BEGIN_EVENTSINK_MAP` (macro), las entradas de macro para cada uno de los eventos que se le notifique y el `END_EVENTSINK_MAP` macro para declarar el final de la lista de receptores de eventos.  
  
 Para obtener más información sobre mapas de receptor de eventos, vea el artículo [contenedores de controles ActiveX](../../mfc/activex-control-containers.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxwin.h  
  
##  <a name="end_eventsink_map"></a>END_EVENTSINK_MAP  
 Termina la definición de la asignación de receptor de eventos.  
  
```   
END_EVENTSINK_MAP()   
```  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="on_event"></a>ON_EVENT  
 Utilice la `ON_EVENT` macro para definir una función de controlador de eventos para un evento desencadenado por un control OLE.  
  
```   
ON_EVENT(theClass, id, dispid, pfnHandler,  vtsParams) 
```  
  
### <a name="parameters"></a>Parámetros  
 `theClass`  
 La clase a la que pertenece este mapa de receptores de eventos.  
  
 `id`  
 El identificador del control del control OLE.  
  
 `dispid`  
 El identificador de envío de los eventos desencadenados por el control.  
  
 `pfnHandler`  
 Puntero a una función miembro que controla el evento. Esta función debe tener un **BOOL** devolver el tipo y los tipos de parámetro que coinciden con los parámetros del evento (consulte `vtsParams`). La función debe devolver **TRUE** para indicar que el evento se ha controlado; en caso contrario **FALSE**.  
  
 `vtsParams`  
 Una secuencia de **VTS_** constantes que especifica los tipos de los parámetros para el evento. Éstas son las constantes mismas que se usan en las entradas del mapa de envíos como `DISP_FUNCTION`.  
  
### <a name="remarks"></a>Comentarios  
 El `vtsParams` argumento es una lista separada por espacios de valores de la **VTS_** constantes. Uno o varios de estos valores separados por espacios (no por comas) especifican la lista de parámetros de la función. Por ejemplo:  
  
 [!code-cpp[NVC_MFCAutomation&#11;](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 Especifica una lista que contiene un entero corto seguido por un **BOOL**.  
  
 Para obtener una lista de los **VTS_** constantes, vea [EVENT_CUSTOM](event-maps.md#event_custom).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="on_event_range"></a>ON_EVENT_RANGE  
 Utilice la `ON_EVENT_RANGE` macro para definir una función de controlador de eventos para un evento desencadenado por cualquier control OLE con un identificador de control dentro de un intervalo contiguo de identificadores.  
  
```   
ON_EVENT_RANGE(theClass, idFirst, idLast, dispid, pfnHandler,  vtsParams)   
```  
  
### <a name="parameters"></a>Parámetros  
 `theClass`  
 La clase a la que pertenece este mapa de receptores de eventos.  
  
 `idFirst`  
 El identificador de control del primer control OLE en el intervalo.  
  
 `idLast`  
 El identificador del último control OLE en el intervalo del control.  
  
 `dispid`  
 El identificador de envío de los eventos desencadenados por el control.  
  
 `pfnHandler`  
 Puntero a una función miembro que controla el evento. Esta función debe tener un **BOOL** tipo, un primer parámetro de tipo de valor devuelto **UINT** (para el identificador de control) y los tipos de parámetros adicionales que coinciden con los parámetros del evento (consulte `vtsParams`). La función debe devolver **TRUE** para indicar que el evento se ha controlado; en caso contrario **FALSE**.  
  
 `vtsParams`  
 Una secuencia de **VTS_** constantes que especifica los tipos de los parámetros para el evento. La primera constante debe ser del tipo **VTS_I4**, para el identificador del control. Éstas son las constantes mismas que se usan en las entradas del mapa de envíos como `DISP_FUNCTION`.  
  
### <a name="remarks"></a>Comentarios  
 El `vtsParams` argumento es una lista separada por espacios de valores de la **VTS_** constantes. Uno o varios de estos valores separados por espacios (no por comas) especifican la lista de parámetros de la función. Por ejemplo:  
  
 [!code-cpp[NVC_MFCAutomation&#11;](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 Especifica una lista que contiene un entero corto seguido por un **BOOL**.  
  
 Para obtener una lista de los **VTS_** constantes, vea [EVENT_CUSTOM](event-maps.md#event_custom).  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un controlador de eventos para el evento MouseDown, implementado para tres controles ( `IDC_MYCTRL1` a través de `IDC_MYCTRL3`). La función de controlador de eventos, `OnRangeMouseDown`, se declara en el archivo de encabezado de la clase de cuadro de diálogo ( `CMyDlg`) como:  
  
 [!code-cpp[NVC_MFCAutomation&#12;](../../mfc/codesnippet/cpp/event-sink-maps_2.h)]  
  
 El código siguiente se define en el archivo de implementación de la clase de cuadro de diálogo.  
  
 [!code-cpp[NVC_MFCAutomation&#13;](../../mfc/codesnippet/cpp/event-sink-maps_3.cpp)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="on_event_reflect"></a>ON_EVENT_REFLECT  
 El `ON_EVENT_REFLECT` recibe de macro, cuando se utiliza en el evento de clase de contenedor de un control OLE, mapa de receptores de eventos desencadenados por el control antes de que están controlados por el contenedor del control.  
  
```   
ON_EVENT_REFLECT(theClass,  dispid, pfnHandler,  vtsParams) 
```  
  
### <a name="parameters"></a>Parámetros  
 `theClass`  
 La clase a la que pertenece este mapa de receptores de eventos.  
  
 DISPID  
 El identificador de envío de los eventos desencadenados por el control.  
  
 `pfnHandler`  
 Puntero a una función miembro que controla el evento. Esta función debe tener un **BOOL** tipo devuelto y los tipos de parámetros que coinciden con los parámetros del evento (consulte `vtsParams`). La función debe devolver **TRUE** para indicar que el evento se ha controlado; en caso contrario **FALSE**.  
  
 `vtsParams`  
 Una secuencia de **VTS_** constantes que especifica los tipos de los parámetros para el evento. Éstas son las constantes mismas que se usan en las entradas del mapa de envíos como `DISP_FUNCTION`.  
  
### <a name="remarks"></a>Comentarios  
 El `vtsParams` argumento es una lista separada por espacios de valores de la **VTS_** constantes.  
  
 Uno o varios de estos valores separados por espacios (no por comas) especifican la lista de parámetros de la función. Por ejemplo:  
  
 [!code-cpp[NVC_MFCAutomation&#11;](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 Especifica una lista que contiene un entero corto seguido por un **BOOL**.  
  
 Para obtener una lista de los **VTS_** constantes, vea [EVENT_CUSTOM](event-maps.md#event_custom).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="on_propnotify"></a>ON_PROPNOTIFY  
 Utilice la `ON_PROPNOTIFY` macro para definir una entrada de mapa de receptores de eventos para controlar las notificaciones de la propiedad de un control OLE.  
  
```   
ON_PROPNOTIFY(theClass, id, dispid, pfnRequest, pfnChanged)  
 
```  
  
### <a name="parameters"></a>Parámetros  
 `theClass`  
 La clase a la que pertenece este mapa de receptores de eventos.  
  
 `id`  
 El identificador del control del control OLE.  
  
 `dispid`  
 El identificador de envío de la propiedad implicada en la notificación.  
  
 `pfnRequest`  
 Puntero a una función miembro que controla la **OnRequestEdit** notificaciones para esta propiedad. Esta función debe tener un **BOOL** tipo de valor devuelto y un **BOOL\* ** parámetro. Esta función debe establecer el parámetro **TRUE** para permitir que la propiedad que se va a cambiar y **FALSE** para no permitir. La función debe devolver **TRUE** para indicar la notificación se ha controlado; en caso contrario **FALSE**.  
  
 `pfnChanged`  
 Puntero a una función miembro que controla la **OnChanged** notificaciones para esta propiedad. La función debe tener un **BOOL** tipo de valor devuelto y un **UINT** parámetro. La función debe devolver **TRUE** para indicar que la notificación se ha controlado; en caso contrario **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 El `vtsParams` argumento es una lista separada por espacios de valores de la **VTS_** constantes. Uno o varios de estos valores separados por espacios (no por comas) especifican la lista de parámetros de la función. Por ejemplo:  
  
 [!code-cpp[NVC_MFCAutomation&#11;](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 Especifica una lista que contiene un entero corto seguido por un **BOOL**.  
  
 Para obtener una lista de los **VTS_** constantes, vea [EVENT_CUSTOM](event-maps.md#event_custom).  
  
##  <a name="on_propnotify_range"></a>ON_PROPNOTIFY_RANGE  
 Utilice la `ON_PROPNOTIFY_RANGE` macro para definir una entrada de mapa de receptores de eventos para controlar las notificaciones de la propiedad de cualquier control OLE con un identificador de control dentro de un intervalo contiguo de identificadores.  
  
```  
 
ON_PROPNOTIFY_RANGE(theClass, idFirst, idLast, dispid, pfnRequest, pfnChanged)  
 
```  
  
### <a name="parameters"></a>Parámetros  
 `theClass`  
 La clase a la que pertenece este mapa de receptores de eventos.  
  
 `idFirst`  
 El identificador de control del primer control OLE en el intervalo.  
  
 `idLast`  
 El identificador del último control OLE en el intervalo del control.  
  
 `dispid`  
 El identificador de envío de la propiedad implicada en la notificación.  
  
 `pfnRequest`  
 Puntero a una función miembro que controla la **OnRequestEdit** notificaciones para esta propiedad. Esta función debe tener un **BOOL** tipo de valor devuelto y **UINT** y **BOOL\* ** parámetros. La función debe establecer el parámetro **TRUE** para permitir que la propiedad que se va a cambiar y **FALSE** para no permitir. La función debe devolver **TRUE** para indicar que la notificación se ha controlado; en caso contrario **FALSE**.  
  
 `pfnChanged`  
 Puntero a una función miembro que controla la **OnChanged** notificaciones para esta propiedad. La función debe tener un **BOOL** tipo de valor devuelto y un **UINT** parámetro. La función debe devolver **TRUE** para indicar que la notificación se ha controlado; en caso contrario **FALSE**.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="on_propnotify_reflect"></a>ON_PROPNOTIFY_REFLECT  
 El `ON_PROPNOTIFY_REFLECT` macro, cuando se utiliza en el evento mapa de receptores de clase de contenedor de un control OLE, recibe notificaciones de propiedad enviadas por el control antes de que están controlados por el contenedor del control.  
  
```  
 
ON_PROPNOTIFY_REFLECT(theClass, dispid, pfnRequest, pfnChanged)  
 
```  
  
### <a name="parameters"></a>Parámetros  
 `theClass`  
 La clase a la que pertenece este mapa de receptores de eventos.  
  
 `dispid`  
 El identificador de envío de la propiedad implicada en la notificación.  
  
 `pfnRequest`  
 Puntero a una función miembro que controla la **OnRequestEdit** notificaciones para esta propiedad. Esta función debe tener un **BOOL** tipo de valor devuelto y un **BOOL\* ** parámetro. Esta función debe establecer el parámetro **TRUE** para permitir que la propiedad que se va a cambiar y **FALSE** para no permitir. La función debe devolver **TRUE** para indicar la notificación se ha controlado; en caso contrario **FALSE**.  
  
 `pfnChanged`  
 Puntero a una función miembro que controla la **OnChanged** notificaciones para esta propiedad. La función debe tener un **BOOL** tipo devuelto y sin parámetros. La función debe devolver **TRUE** para indicar la notificación se ha controlado; en caso contrario **FALSE**.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
    
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)

