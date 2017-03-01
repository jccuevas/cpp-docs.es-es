---
title: Mapas de eventos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- event maps
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
caps.latest.revision: 15
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
ms.openlocfilehash: 4c4777496ce609d7c2fa20da726f211264095b6e
ms.lasthandoff: 02/24/2017

---
# <a name="event-maps"></a>Mapas de eventos
Cada vez que un control desea notificar a su contenedor que se ha producido alguna acción (determinado por el desarrollador del control) (como una pulsación de tecla, clic del mouse o un cambio en el estado del control) llama a una función de desencadenamiento de eventos. Esta función notifica el contenedor del control que se ha producido alguna acción importante desencadenando el evento relacionado.  
  
 Microsoft Foundation Class Library ofrece un modelo de programación optimizado para desencadenar eventos. En este modelo, "mapas de eventos" se utilizan para designar qué funciones activan los eventos de un control determinado. Mapas de eventos contienen una macro para cada evento. Por ejemplo, un mapa de eventos que desencadena una acción, haga clic en eventos tendrá este aspecto:  
  
 [!code-cpp[NVC_MFCAxCtl Nº&16;](../../mfc/reference/codesnippet/cpp/event-maps_1.cpp)]  
  
 El **EVENT_STOCK_CLICK** (macro) indica que el control desencadena una acción, haga clic en evento cada vez que detecte un mouse. Para obtener una lista más detallada de otros eventos estándar, vea el artículo [controles ActiveX: eventos](../../mfc/mfc-activex-controls-events.md). Las macros también están disponibles para indicar eventos personalizados.  
  
 Aunque las macros de mapa de eventos son importantes, por lo general no insertarlas directamente. Esto es porque la ventana Propiedades crea automáticamente las entradas del mapa de eventos en los archivos de origen cuando se utiliza para asociar las funciones de desencadenamiento de eventos a eventos. Cualquier momento que desee editar o agregar una entrada de mapa de eventos, puede utilizar la ventana Propiedades.  
  
 Para admitir los mapas de eventos, MFC proporciona las siguientes macros:  
  
### <a name="event-map-declaration-and-demarcation"></a>Delimitación y declaración de mapa de eventos  
  
|||  
|-|-|  
|[DECLARE_EVENT_MAP](#declare_event_map)|Declara que se utilizará un mapa de eventos en una clase para asignar sucesos a funciones de desencadenamiento de eventos (utilizado en la declaración de clase).|  
|[BEGIN_EVENT_MAP](#begin_event_map)|Inicia la definición de un mapa de eventos (debe utilizarse en la implementación de la clase).|  
|[END_EVENT_MAP](#end_event_map)|Termina la definición de un mapa de eventos (debe utilizarse en la implementación de la clase).|  
  
### <a name="event-mapping-macros"></a>Macros de asignación de eventos  
  
|||  
|-|-|  
|[EVENT_CUSTOM](#event_custom)|Indica qué función de activación del evento desencadenará el evento especificado.|  
|[EVENT_CUSTOM_ID](#event_custom_id)|Indica qué función de activación del evento desencadenará el evento especificado, con un identificador de envío designado.|  
  
### <a name="message-mapping-macros"></a>Macros de asignación de mensajes  
  
|||  
|-|-|  
|[ON_OLEVERB](#on_oleverb)|Indica un verbo personalizado que se controla mediante el control OLE.|  
|[ON_STDOLEVERB](#on_stdoleverb)|Reemplaza una asignación de verbo estándar del control OLE.|  
  
##  <a name="a-namedeclareeventmapa--declareeventmap"></a><a name="declare_event_map"></a>DECLARE_EVENT_MAP  
 Cada `COleControl`-clase derivada en el programa puede proporcionar un mapa de eventos para especificar los eventos que desencadenará el control.  
  
```   
DECLARE_EVENT_MAP()   
```  
  
### <a name="remarks"></a>Comentarios  
 Utilice la `DECLARE_EVENT_MAP` macro al final de la declaración de clase. A continuación, en el archivo .cpp que define las funciones de miembro para la clase, use la `BEGIN_EVENT_MAP` (macro), las entradas de macro para cada uno de los eventos del control y el `END_EVENT_MAP` macro para declarar el final de la lista de eventos.  
  
 Para obtener más información sobre mapas de eventos, vea el artículo [controles ActiveX: eventos](../../mfc/mfc-activex-controls-events.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="a-namebegineventmapa--begineventmap"></a><a name="begin_event_map"></a>BEGIN_EVENT_MAP  
 Inicia la definición de la asignación de eventos.  
  
```   
BEGIN_EVENT_MAP(theClass,  baseClass)  
```  
  
### <a name="parameters"></a>Parámetros  
 `theClass`  
 Especifica el nombre de la clase control cuyo evento asignar todo esto.  
  
 `baseClass`  
 Especifica el nombre de la clase base de `theClass`.  
  
### <a name="remarks"></a>Comentarios  
 En el archivo de implementación (.cpp) que define las funciones de miembro para la clase, iniciar el mapa de eventos con el `BEGIN_EVENT_MAP` (macro), a continuación, agregue entradas de macro para cada uno de los eventos y completar el mapa de eventos con el `END_EVENT_MAP` (macro).  
  
 Para obtener más información sobre eventos asigna y la `BEGIN_EVENT_MAP` (macro), consulte el artículo [controles ActiveX: eventos](../../mfc/mfc-activex-controls-events.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="a-nameendeventmapa--endeventmap"></a><a name="end_event_map"></a>END_EVENT_MAP  
 Utilice la `END_EVENT_MAP` macro para terminar la definición de la asignación de eventos.  
  
```   
END_EVENT_MAP()   
```  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="a-nameeventcustoma--eventcustom"></a><a name="event_custom"></a>EVENT_CUSTOM  
 Define una entrada de mapa de eventos para un evento personalizado.  
  
```   
EVENT_CUSTOM(pszName, pfnFire,  vtsParams) 
```  
  
### <a name="parameters"></a>Parámetros  
 `pszName`  
 Nombre del evento.  
  
 `pfnFire`  
 El nombre de la función de activación del evento.  
  
 `vtsParams`  
 Una lista separada por espacios de una o más constantes especificando la lista de parámetros de la función.  
  
### <a name="remarks"></a>Comentarios  
 El `vtsParams` parámetro es una lista separada por espacios de valores de la **VTS_** constantes. Uno o varios de estos valores separados por espacios (no por comas) especifican la lista de parámetros de la función. Por ejemplo:  
  
 [!code-cpp[NVC_MFCActiveXControl&#13;](../../mfc/codesnippet/cpp/event-maps_2.cpp)]  
  
 Especifica el color de una lista que contiene un entero de 32 bits que representa una RGB valor, seguido de un puntero a la **IFontDisp** interfaz de un objeto de fuente OLE.  
  
 El **VTS_** constantes y sus significados son los siguientes:  
  
|Símbolo|Tipo de parámetro|  
|------------|--------------------|  
|**VTS_I2**|**short**|  
|**VTS_I4**|**long**|  
|**VTS_R4**|**float**|  
|**VTS_R8**|**double**|  
|**VTS_COLOR**|**OLE_COLOR**|  
|**VTS_CY**|**MONEDA**|  
|**VTS_DATE**|**FECHA**|  
|**VTS_BSTR**|**const char\***|  
|**VTS_DISPATCH**|`LPDISPATCH`|  
|**VTS_FONT**|**IFontDispatch\***|  
|**VTS_HANDLE**|`HANDLE`|  
|**VTS_SCODE**|`SCODE`|  
|**VTS_BOOL**|**BOOL**|  
|**VTS_VARIANT**|**VARIANTE const\***|  
|**VTS_PVARIANT**|**VARIANT\***|  
|**VTS_UNKNOWN**|`LPUNKNOWN`|  
|**VTS_OPTEXCLUSIVE**|**OLE_OPTEXCLUSIVE**|  
|**VTS_PICTURE**|**IPictureDisp\***|  
|**VTS_TRISTATE**|**OLE_TRISTATE**|  
|**VTS_XPOS_PIXELS**|**OLE_XPOS_PIXELS**|  
|**VTS_YPOS_PIXELS**|**OLE_YPOS_PIXELS**|  
|**VTS_XSIZE_PIXELS**|**OLE_XSIZE_PIXELS**|  
|**VTS_YSIZE_PIXELS**|**OLE_YSIZE_PIXELS**|  
|**VTS_XPOS_HIMETRIC**|**OLE_XPOS_HIMETRIC**|  
|**VTS_YPOS_HIMETRIC**|**OLE_YPOS_HIMETRIC**|  
|**VTS_XSIZE_HIMETRIC**|**OLE_XSIZE_HIMETRIC**|  
|**VTS_YSIZE_HIMETRIC**|**OLE_YSIZE_HIMETRIC**|  
  
> [!NOTE]
>  Constantes de tipo variant adicionales se han definido para todos los tipos variant, con la excepción de **VTS_FONT** y **VTS_PICTURE**, que proporciona un puntero a la constante de datos variant. Estas constantes se denominan utilizando la **VTS_P** `constantname` convención. Por ejemplo, **VTS_PCOLOR** es un puntero a un **VTS_COLOR** constante.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="a-nameeventcustomida--eventcustomid"></a><a name="event_custom_id"></a>EVENT_CUSTOM_ID  
 Define un función para un evento personalizado que pertenecen a la especificada por el identificador de envío que desencadenó el evento `dispid`.  
  
```   
EVENT_CUSTOM_ID(
  pszName,   
  dispid,   
  pfnFire,
  vtsParams)  
 
```  
  
### <a name="parameters"></a>Parámetros  
 `pszName`  
 Nombre del evento.  
  
 `dispid`  
 El identificador de envío utilizado por el control cuando se desencadena el evento.  
  
 `pfnFire`  
 El nombre de la función de activación del evento.  
  
 `vtsParams`  
 Una lista de variables de parámetros pasados al contenedor del control cuando se desencadena el evento.  
  
### <a name="remarks"></a>Comentarios  
 El `vtsParams` argumento es una lista separada por espacios de valores de la **VTS_** constantes. Uno o varios de estos valores separados por espacios, no por comas, especifican la lista de parámetros de la función. Por ejemplo:  
  
 [!code-cpp[NVC_MFCActiveXControl&#13;](../../mfc/codesnippet/cpp/event-maps_2.cpp)]  
  
 Especifica el color de una lista que contiene un entero de 32 bits que representa una RGB valor, seguido de un puntero a la **IFontDisp** interfaz de un objeto de fuente OLE.  
  
 Para obtener una lista de los **VTS_** constantes, vea [EVENT_CUSTOM](#event_custom).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="a-nameonoleverba--onoleverb"></a><a name="on_oleverb"></a>ON_OLEVERB  
 Esta macro define una entrada de mapa de mensajes que se asigna a un verbo personalizado a una función miembro específico del control.  
  
```   
ON_OLEVERB(idsVerbName,  memberFxn)   
```  
  
### <a name="parameters"></a>Parámetros  
 *idsVerbName*  
 El identificador de recurso de cadena del nombre del verbo.  
  
 `memberFxn`  
 La función que llama el marco de trabajo cuando se invoque el verbo.  
  
### <a name="remarks"></a>Comentarios  
 El editor de recursos puede utilizarse para crear los nombres de verbo personalizados que se agregan a la tabla de cadenas.  
  
 El prototipo de función `memberFxn` es:  
  
 `BOOL memberFxn(`    
 `LPMSG` `lpMsg` `,`   
 `HWND` `hWndParent` `,`   
 `LPCRECT` `lpRect`   `);`  
  
 Los valores de la `lpMsg`, `hWndParent`, y `lpRect` parámetros se toman de los parámetros correspondientes de la **DoVerb** función miembro.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxole.h  
  
##  <a name="a-nameonstdoleverba--onstdoleverb"></a><a name="on_stdoleverb"></a>ON_STDOLEVERB  
 Usar esta macro para invalidar el comportamiento predeterminado de un verbo estándar.  
  
```   
ON_STDOLEVERB(iVerb,   memberFxn)   
```  
  
### <a name="parameters"></a>Parámetros  
 `iVerb`  
 El índice del verbo estándar para el verbo que se va a invalidar.  
  
 `memberFxn`  
 La función que llama el marco de trabajo cuando se invoque el verbo.  
  
### <a name="remarks"></a>Comentarios  
 El índice del verbo estándar tiene la forma **OLEIVERB_**, seguido de una acción. `OLEIVERB_SHOW`, `OLEIVERB_HIDE`, y `OLEIVERB_UIACTIVATE` son algunos ejemplos de verbos estándar.  
  
 Consulte [ON_OLEVERB](#on_oleverb) para obtener una descripción del prototipo de función que se usará como el `memberFxn` parámetro.  

  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxole.h  
    
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)

