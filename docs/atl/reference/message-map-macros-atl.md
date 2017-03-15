---
title: Macros de mapa (ATL) de mensajes | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: eefdd546-8934-4a30-b263-9c06a8addcbd
caps.latest.revision: 16
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 8097982d6574af2ce1ba592dbead8abf6f6433df
ms.lasthandoff: 02/24/2017

---
# <a name="message-map-macros-atl"></a>Macros de mapa de mensajes (ATL)
Estas macros definen entradas y mapas de mensajes.  
  
|||  
|-|-|  
|[ALT_MSG_MAP](#alt_msg_map)|Marca el principio de un mapa de mensajes alternativo.|  
|[BEGIN_MSG_MAP](#begin_msg_map)|Marca el principio del mapa de mensajes predeterminado.|  
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Está vinculado a un mapa de mensajes alternativo en la clase base.|  
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Está vinculado a un mapa de mensajes alternativo en un miembro de datos de la clase.|  
|[CHAIN_MSG_MAP](#chain_msg_map)|Está vinculado al mapa de mensajes predeterminado de la clase base.|  
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Está vinculado al mapa de mensajes en otra clase en tiempo de ejecución.|  
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Está vinculado al mapa de mensajes predeterminado en un miembro de datos de la clase.|  
|[COMMAND_CODE_HANDLER](#command_code_handler)|Se asigna un **WM_COMMAND** mensaje a una función de controlador, según el código de notificación.|  
|[COMMAND_HANDLER](#command_handler)|Se asigna un **WM_COMMAND** mensaje a una función de controlador, según el código de notificación y el identificador del elemento de menú, control o acelerador.|  
|[COMMAND_ID_HANDLER](#command_id_handler)|Se asigna un **WM_COMMAND** mensaje a una función de controlador, basándose en el identificador del elemento de menú, control o acelerador.|  
|[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)|Se asigna un **WM_COMMAND** mensaje a una función de controlador, según el código de notificación y un intervalo contiguo de identificadores de control.|  
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Se asigna un **WM_COMMAND** mensaje a una función de controlador, basándose en un intervalo contiguo de identificadores de control.|  
|[DECLARE_EMPTY_MSG_MAP](#declare_empty_msg_map)|Implementa un mapa de mensajes vacío.|  
|[DEFAULT_REFLECTION_HANDLER](#default_reflection_handler)|Proporciona un controlador predeterminado para los mensajes reflejados no administradas en caso contrario.|  
|[END_MSG_MAP](#end_msg_map)|Marca el final de un mapa de mensajes.|  
|[FORWARD_NOTIFICATIONS](#forward_notifications)|Reenvía los mensajes de notificación a la ventana primaria.|  
|[MESSAGE_HANDLER](#message_handler)|Asigna un mensaje de Windows a una función de controlador.|  
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Los mensajes de un intervalo contiguo de Windows se asigna a una función de controlador.|  
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Se asigna un **WM_NOTIFY** mensaje a una función de controlador, según el código de notificación.|  
|[NOTIFY_HANDLER](#notify_handler)|Se asigna un **WM_NOTIFY** mensaje a una función de controlador, según el código de notificación y el identificador del control.|  
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Se asigna un **WM_NOTIFY** mensaje a una función de controlador, según el identificador del control.|  
|[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)|Se asigna un **WM_NOTIFY** mensaje a una función de controlador, según el código de notificación y un intervalo contiguo de identificadores de control.|  
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Se asigna un **WM_NOTIFY** mensaje a una función de controlador, basándose en un intervalo contiguo de identificadores de control.|  
|[REFLECT_NOTIFICATIONS](#reflect_notifications)|Refleja los mensajes de notificación a la ventana que se enviaron.|  
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Asigna un reflejado **WM_COMMAND** mensaje a una función de controlador, según el código de notificación.|  
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Asigna un reflejado **WM_COMMAND** mensaje a una función de controlador, según el código de notificación y el identificador del elemento de menú, control o acelerador.|  
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Asigna un reflejado **WM_COMMAND** mensaje a una función de controlador, basándose en el identificador del elemento de menú, control o acelerador.|  
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Asigna un reflejado **WM_COMMAND** mensaje a una función de controlador, según el código de notificación y un intervalo contiguo de identificadores de control.|  
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Asigna un reflejado **WM_COMMAND** mensaje a una función de controlador, basándose en un intervalo contiguo de identificadores de control.|  
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Asigna un reflejado **WM_NOTIFY** mensaje a una función de controlador, según el código de notificación.|  
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Asigna un reflejado **WM_NOTIFY** mensaje a una función de controlador, según el código de notificación y el identificador del control.|  
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Asigna un reflejado **WM_NOTIFY** mensaje a una función de controlador, según el identificador del control.|  
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Asigna un reflejado **WM_NOTIFY** mensaje a una función de controlador, según el código de notificación y un intervalo contiguo de identificadores de control.|  
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Asigna un reflejado **WM_NOTIFY** mensaje a una función de controlador, basándose en un intervalo contiguo de identificadores de control.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  

##  <a name="a-namealtmsgmapa--altmsgmap"></a><a name="alt_msg_map"></a>ALT_MSG_MAP  
 Marca el principio de un mapa de mensajes alternativo.  
  
```
ALT_MSG_MAP(msgMapID)
```  
  
### <a name="parameters"></a>Parámetros  
 `msgMapID`  
 [in] El identificador del mapa de mensajes.  
  
### <a name="remarks"></a>Comentarios  
 ATL identifica cada mapa de mensajes por un número. El mapa de mensajes predeterminado (declarado con la `BEGIN_MSG_MAP` (macro)) se identifica por 0. Un mapa de mensajes alternativo se identifica mediante `msgMapID`.  
  
 Mapas de mensajes se utilizan para procesar los mensajes enviados a una ventana. Por ejemplo, [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) permite especificar el identificador de un mapa de mensajes en el objeto contenedor. [CContainedWindow:: WindowProc](ccontainedwindowt-class.md#windowproc) , a continuación, utiliza este mapa de mensajes para enviar los mensajes de la ventana independiente a la función de controlador adecuado o a otro mapa de mensajes. Para obtener una lista de macros que declaran funciones del controlador, consulte [BEGIN_MSG_MAP](#begin_msg_map).  
  
 Siempre comienzan con un mapa de mensajes `BEGIN_MSG_MAP`. Puede declarar mapas de mensajes alternativos subsiguientes.  
  
 El [END_MSG_MAP](#end_msg_map) macro marca el final del mapa de mensajes. Tenga en cuenta que siempre hay exactamente una instancia de `BEGIN_MSG_MAP` y `END_MSG_MAP`.  
  
 Para obtener más información sobre el uso de mapas de mensajes en ATL, vea [mapas de mensajes](../../atl/message-maps-atl.md).  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el mapa de mensajes predeterminado y la asignación de un mensaje alternativo, cada una con una función de controlador:  
  
 [!code-cpp[NVC_ATL_Windowing&#98;](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]  
  
 El ejemplo siguiente muestra dos mapas de mensajes alternativos. El mapa de mensajes predeterminado está vacío.  
  
 [!code-cpp[NVC_ATL_Windowing&#99;](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h   

##  <a name="a-namebeginmsgmapa--beginmsgmap"></a><a name="begin_msg_map"></a>BEGIN_MSG_MAP  
 Marca el principio del mapa de mensajes predeterminado.  
  
```
BEGIN_MSG_MAP(theClass)
```  
  
### <a name="parameters"></a>Parámetros  
 `theClass`  
 [in] El nombre de la clase que contiene el mapa de mensajes.  
  
### <a name="remarks"></a>Comentarios  
 [CWindowImpl:: WindowProc](cwindowimpl-class.md#windowproc) utiliza el mapa de mensajes predeterminado para procesar los mensajes enviados a la ventana. El mapa de mensajes dirige los mensajes a la función de controlador adecuado o a otro mapa de mensajes.  

  
 Las siguientes macros asignan un mensaje a una función de controlador. Esta función debe estar definida en `theClass`.  
  
|Macro|Descripción|  
|-----------|-----------------|  
|[MESSAGE_HANDLER](#message_handler)|Asigna un mensaje de Windows a una función de controlador.|  
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Los mensajes de un intervalo contiguo de Windows se asigna a una función de controlador.|  
|[COMMAND_HANDLER](#command_handler)|Se asigna un **WM_COMMAND** mensaje a una función de controlador, según el código de notificación y el identificador del elemento de menú, control o acelerador.|  
|[COMMAND_ID_HANDLER](#command_id_handler)|Se asigna un **WM_COMMAND** mensaje a una función de controlador, basándose en el identificador del elemento de menú, control o acelerador.|  
|[COMMAND_CODE_HANDLER](#command_handler)|Se asigna un **WM_COMMAND** mensaje a una función de controlador, según el código de notificación.|  
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Asigna un intervalo contiguo de **WM_COMMAND** mensajes a una función de controlador, basándose en el identificador del elemento de menú, control o acelerador.|  
|[NOTIFY_HANDLER](#notify_handler)|Se asigna un **WM_NOTIFY** mensaje a una función de controlador, según el código de notificación y el identificador del control.|  
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Se asigna un **WM_NOTIFY** mensaje a una función de controlador, según el identificador del control.|  
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Se asigna un **WM_NOTIFY** mensaje a una función de controlador, según el código de notificación.|  
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Asigna un intervalo contiguo de **WM_NOTIFY** mensajes a una función de controlador, según el identificador del control.|  
  
 Las siguientes macros dirigen mensajes a otro mapa de mensajes. Este proceso se denomina "encadenamiento".  
  
|Macro|Descripción|  
|-----------|-----------------|  
|[CHAIN_MSG_MAP](#chain_msg_map)|Está vinculado al mapa de mensajes predeterminado de la clase base.|  
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Está vinculado al mapa de mensajes predeterminado en un miembro de datos de la clase.|  
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Está vinculado a un mapa de mensajes alternativo en la clase base.|  
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Está vinculado a un mapa de mensajes alternativo en un miembro de datos de la clase.|  
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Está vinculado al mapa de mensajes predeterminado en otra clase en tiempo de ejecución.|  
  
 Las siguientes macros dirigen mensajes "reflejados" de la ventana primaria. Por ejemplo, un control normalmente envía mensajes de notificación a su ventana primaria para procesamiento, pero la ventana primaria puede reflejar el mensaje al control.  
  
|Macro|Descripción|  
|-----------|-----------------|  
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Asigna un reflejado **WM_COMMAND** mensaje a una función de controlador, según el código de notificación y el identificador del elemento de menú, control o acelerador.|  
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Asigna un reflejado **WM_COMMAND** mensaje a una función de controlador, basándose en el identificador del elemento de menú, control o acelerador.|  
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Asigna un reflejado **WM_COMMAND** mensaje a una función de controlador, según el código de notificación.|  
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Asigna un reflejado **WM_COMMAND** mensaje a una función de controlador, basándose en un intervalo contiguo de identificadores de control.|  
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Asigna un reflejado **WM_COMMAND** mensaje a una función de controlador, según el código de notificación y un intervalo contiguo de identificadores de control.|  
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Asigna un reflejado **WM_NOTIFY** mensaje a una función de controlador, según el código de notificación y el identificador del control.|  
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Asigna un reflejado **WM_NOTIFY** mensaje a una función de controlador, según el identificador del control.|  
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Asigna un reflejado **WM_NOTIFY** mensaje a una función de controlador, según el código de notificación.|  
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Asigna un reflejado **WM_NOTIFY** mensaje a una función de controlador, basándose en un intervalo contiguo de identificadores de control.|  
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Asigna un reflejado **WM_NOTIFY** mensaje a una función de controlador, según el código de notificación y un intervalo contiguo de identificadores de control.|  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#102;](../../atl/codesnippet/cpp/message-map-macros-atl_3.h)]  
  
 Cuando un `CMyExtWindow` objeto recibe un `WM_PAINT` mensaje, el mensaje se dirige a `CMyExtWindow::OnPaint` para el procesamiento real. Si `OnPaint` indica que el mensaje requiere procesamiento adicional, tendrá de mensaje, a continuación, se dirige al mapa de mensajes predeterminado en `CMyBaseWindow`.  
  
 Además el mapa de mensajes predeterminado, puede definir un mapa de mensajes alternativo con [ALT_MSG_MAP](#alt_msg_map). Siempre comienzan con un mapa de mensajes `BEGIN_MSG_MAP`. Puede declarar mapas de mensajes alternativos subsiguientes. En el ejemplo siguiente se muestra el mapa de mensajes predeterminado y la asignación de un mensaje alternativo, cada una con una función de controlador:  
  
 [!code-cpp[NVC_ATL_Windowing&#98;](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]  
  
 El ejemplo siguiente muestra dos mapas de mensajes alternativos. El mapa de mensajes predeterminado está vacío.  
  
 [!code-cpp[NVC_ATL_Windowing&#99;](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]  
  
 El [END_MSG_MAP](#end_msg_map) macro marca el final del mapa de mensajes. Tenga en cuenta que siempre hay exactamente una instancia de `BEGIN_MSG_MAP` y `END_MSG_MAP`.  
  
 Para obtener más información sobre el uso de mapas de mensajes en ATL, vea [mapas de mensajes](../../atl/message-maps-atl.md).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h   
  
##  <a name="a-namechainmsgmapalta--chainmsgmapalt"></a><a name="chain_msg_map_alt"></a>CHAIN_MSG_MAP_ALT  
 Define una entrada en un mapa de mensajes.  
  
```
CHAIN_MSG_MAP_ALT(theChainClass, msgMapID)
```  
  
### <a name="parameters"></a>Parámetros  
 `theChainClass`  
 [in] El nombre de la clase base que contiene el mapa de mensajes.  
  
 `msgMapID`  
 [in] El identificador del mapa de mensajes.  
  
### <a name="remarks"></a>Comentarios  
 `CHAIN_MSG_MAP_ALT`dirige los mensajes a un mapa de mensajes alternativo en una clase base. Debe haber declarado este mapa de mensajes alternativo con [ALT_MSG_MAP(msgMapID)](#alt_msg_map). Para enviar los mensajes al mapa de mensajes predeterminado de la clase base (declarado con [BEGIN_MSG_MAP](#begin_msg_map)), utilice `CHAIN_MSG_MAP`. Para obtener un ejemplo, vea [CHAIN_MSG_MAP](#chain_msg_map).  
  
> [!NOTE]
>  Siempre comienzan con un mapa de mensajes `BEGIN_MSG_MAP`. Puede declarar mapas de mensajes alternativos posteriores con `ALT_MSG_MAP`. El [END_MSG_MAP](#end_msg_map) macro marca el final del mapa de mensajes. Cada mapa de mensajes debe tener exactamente una instancia de `BEGIN_MSG_MAP` y `END_MSG_MAP`.  
  
 Para obtener más información sobre el uso de mapas de mensajes en ATL, vea [mapas de mensajes](../../atl/message-maps-atl.md).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h   
  
##  <a name="a-namechainmsgmapaltmembera--chainmsgmapaltmember"></a><a name="chain_msg_map_alt_member"></a>CHAIN_MSG_MAP_ALT_MEMBER  
 Define una entrada en un mapa de mensajes.  
  
```
CHAIN_MSG_MAP_ALT_MEMBER(theChainMember, msgMapID)
```  
  
### <a name="parameters"></a>Parámetros  
 `theChainMember`  
 [in] El nombre del miembro de datos que contiene el mapa de mensajes.  
  
 `msgMapID`  
 [in] El identificador del mapa de mensajes.  
  
### <a name="remarks"></a>Comentarios  
 `CHAIN_MSG_MAP_ALT_MEMBER`dirige los mensajes a un mapa de mensajes alternativo en un miembro de datos. Debe haber declarado este mapa de mensajes alternativo con [ALT_MSG_MAP(msgMapID)](#alt_msg_map). Para enviar los mensajes al mapa de mensajes predeterminado de un miembro de datos (declarado con [BEGIN_MSG_MAP](#begin_msg_map)), utilice `CHAIN_MSG_MAP_MEMBER`. Para obtener un ejemplo, vea [CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member).  
  
> [!NOTE]
>  Siempre comienzan con un mapa de mensajes `BEGIN_MSG_MAP`. Puede declarar mapas de mensajes alternativos posteriores con `ALT_MSG_MAP`. El [END_MSG_MAP](#end_msg_map) macro marca el final del mapa de mensajes. Cada mapa de mensajes debe tener exactamente una instancia de `BEGIN_MSG_MAP` y `END_MSG_MAP`.  
  
 Para obtener más información sobre el uso de mapas de mensajes en ATL, vea [mapas de mensajes](../../atl/message-maps-atl.md).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h   
  
##  <a name="a-namechainmsgmapa--chainmsgmap"></a><a name="chain_msg_map"></a>CHAIN_MSG_MAP  
 Define una entrada en un mapa de mensajes.  
  
```
CHAIN_MSG_MAP(theChainClass)
```  
  
### <a name="parameters"></a>Parámetros  
 `theChainClass`  
 [in] El nombre de la clase base que contiene el mapa de mensajes.  
  
### <a name="remarks"></a>Comentarios  
 `CHAIN_MSG_MAP`dirige los mensajes al mapa de mensajes predeterminado de la clase base (declarado con [BEGIN_MSG_MAP](#begin_msg_map)). Para enviar los mensajes al mapa de mensajes alternativo de una clase base (declarado con [ALT_MSG_MAP](#alt_msg_map)), utilice [CHAIN_MSG_MAP_ALT](#chain_msg_map_alt).  
  
> [!NOTE]
>  Siempre comienzan con un mapa de mensajes `BEGIN_MSG_MAP`. Puede declarar mapas de mensajes alternativos posteriores con `ALT_MSG_MAP`. El [END_MSG_MAP](#end_msg_map) macro marca el final del mapa de mensajes. Cada mapa de mensajes debe tener exactamente una instancia de `BEGIN_MSG_MAP` y `END_MSG_MAP`.  
  
 Para obtener más información sobre el uso de mapas de mensajes en ATL, vea [mapas de mensajes](../../atl/message-maps-atl.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#107;](../../atl/codesnippet/cpp/message-map-macros-atl_4.h)]  
  
 Este ejemplo muestra lo siguiente:  
  
-   Si está utilizando un procedimiento de ventana `CMyClass`del mapa de mensajes predeterminado y `OnPaint` no identificador de un mensaje, el mensaje se dirige a `CMyBaseClass`del mapa de mensajes predeterminado para el procesamiento.  
  
-   Si un procedimiento de ventana está usando el mapa de mensajes alternativo primer en `CMyClass`, todos los mensajes se dirigen a `CMyBaseClass`del mapa de mensajes predeterminado.  
  
-   Si está utilizando un procedimiento de ventana `CMyClass`del segundo mensaje alternativo asignar y `OnChar` no identificador de un mensaje, el mensaje se dirige al mapa de mensajes alternativo especificado en `CMyBaseClass`. `CMyBaseClass`debe haber declarado este mapa de mensajes con `ALT_MSG_MAP(1)`.  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h   
  
##  <a name="a-namechainmsgmapdynamica--chainmsgmapdynamic"></a><a name="chain_msg_map_dynamic"></a>CHAIN_MSG_MAP_DYNAMIC  
 Define una entrada en un mapa de mensajes.  
  
```
CHAIN_MSG_MAP_DYNAMIC(dynaChainID)
```  
  
### <a name="parameters"></a>Parámetros  
 *dynaChainID*  
 [in] El identificador único para el mapa de mensajes de un objeto.  
  
### <a name="remarks"></a>Comentarios  
 `CHAIN_MSG_MAP_DYNAMIC`dirige los mensajes, en tiempo de ejecución para el mapa de mensajes predeterminado en otro objeto. El objeto y su mapa de mensajes están asociados con *dynaChainID*, que se definen a través de [CDynamicChain:: SetChainEntry](cdynamicchain-class.md#setchainentry). Debe derivar su clase de `CDynamicChain` para poder utilizar `CHAIN_MSG_MAP_DYNAMIC`. Para obtener un ejemplo, consulte el [CDynamicChain](../../atl/reference/cdynamicchain-class.md) información general.  

  
> [!NOTE]
>  Siempre comienzan con un mapa de mensajes [BEGIN_MSG_MAP](#begin_msg_map). Puede declarar mapas de mensajes alternativos posteriores con `ALT_MSG_MAP`. El [END_MSG_MAP](#end_msg_map) macro marca el final del mapa de mensajes. Cada mapa de mensajes debe tener exactamente una instancia de `BEGIN_MSG_MAP` y `END_MSG_MAP`.  
  
 Para obtener más información sobre el uso de mapas de mensajes en ATL, vea [mapas de mensajes](../../atl/message-maps-atl.md).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h   
  
##  <a name="a-namechainmsgmapmembera--chainmsgmapmember"></a><a name="chain_msg_map_member"></a>CHAIN_MSG_MAP_MEMBER  
 Define una entrada en un mapa de mensajes.  
  
```
CHAIN_MSG_MAP_MEMBER(theChainMember)
```  
  
### <a name="parameters"></a>Parámetros  
 `theChainMember`  
 [in] El nombre del miembro de datos que contiene el mapa de mensajes.  
  
### <a name="remarks"></a>Comentarios  
 `CHAIN_MSG_MAP_MEMBER`dirige los mensajes al mapa de mensajes predeterminado de un miembro de datos (declarado con [BEGIN_MSG_MAP](#begin_msg_map)). Para enviar los mensajes al mapa de mensajes alternativo de un miembro de datos (declarado con [ALT_MSG_MAP](#alt_msg_map)), utilice [CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member).  
  
> [!NOTE]
>  Siempre comienzan con un mapa de mensajes `BEGIN_MSG_MAP`. Puede declarar mapas de mensajes alternativos posteriores con `ALT_MSG_MAP`. El [END_MSG_MAP](#end_msg_map) macro marca el final del mapa de mensajes. Cada mapa de mensajes debe tener exactamente una instancia de `BEGIN_MSG_MAP` y `END_MSG_MAP`.  
  
 Para obtener más información sobre el uso de mapas de mensajes en ATL, vea [mapas de mensajes](../../atl/message-maps-atl.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#108;](../../atl/codesnippet/cpp/message-map-macros-atl_5.h)]  
  
 Este ejemplo muestra lo siguiente:  
  
-   Si está utilizando un procedimiento de ventana `CMyClass`del mapa de mensajes predeterminado y `OnPaint` no identificador de un mensaje, el mensaje se dirige a `m_obj`del mapa de mensajes predeterminado para el procesamiento.  
  
-   Si un procedimiento de ventana está usando el mapa de mensajes alternativo primer en `CMyClass`, todos los mensajes se dirigen a `m_obj`del mapa de mensajes predeterminado.  
  
-   Si está utilizando un procedimiento de ventana `CMyClass`del segundo mensaje alternativo asignar y `OnChar` no identificador de un mensaje, el mensaje se dirige al mapa de mensajes alternativo especificado `m_obj`. Clase `CMyContainedClass` debe haber declarado este mapa de mensajes con `ALT_MSG_MAP(1)`.  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h   
  
##  <a name="a-namecommandcodehandlera--commandcodehandler"></a><a name="command_code_handler"></a>COMMAND_CODE_HANDLER  
 Similar a [COMMAND_HANDLER](#command_handler), pero se asigna un [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) mensaje basándose únicamente en el código de notificación.  
  
```
COMMAND_CODE_HANDLER(code, func)
```  
  
### <a name="parameters"></a>Parámetros  
 `code`  
 [in] El código de notificación.  
  
 `func`  
 [in] El nombre de la función de controlador de mensajes.  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h   
  
##  <a name="a-namecommandhandlera--commandhandler"></a><a name="command_handler"></a>COMMAND_HANDLER  
 Define una entrada en un mapa de mensajes.  
  
```
COMMAND_HANDLER(id, code, func)
```    
  
### <a name="parameters"></a>Parámetros  
 `id`  
 [in] El identificador del elemento de menú, control o acelerador.  
  
 `code`  
 [in] El código de notificación.  
  
 `func`  
 [in] El nombre de la función de controlador de mensajes.  
  
### <a name="remarks"></a>Comentarios  
 `COMMAND_HANDLER`asigna un [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) mensaje a la función de controlador especificado, basada en el código de notificación y el identificador del control. Por ejemplo:  
  
 [!code-cpp[NVC_ATL_Windowing&#119;](../../atl/codesnippet/cpp/message-map-macros-atl_6.h)]  
  
 Cualquier función especificada en un `COMMAND_HANDLER` macro debe definirse como sigue:  
  
 `LRESULT CommandHandler(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled);`  
  
 Los conjuntos de mapa de mensajes `bHandled` a **TRUE** antes de `CommandHandler` se llama. Si `CommandHandler` no controla totalmente el mensaje, se debe establecer `bHandled` a **FALSE** para indicar que el mensaje requiere un procesamiento adicional.  
  
> [!NOTE]
>  Siempre comienzan con un mapa de mensajes [BEGIN_MSG_MAP](#begin_msg_map). Puede declarar mapas de mensajes alternativos posteriores con [ALT_MSG_MAP](#alt_msg_map). El [END_MSG_MAP](#end_msg_map) macro marca el final del mapa de mensajes. Cada mapa de mensajes debe tener exactamente una instancia de `BEGIN_MSG_MAP` y `END_MSG_MAP`.  
  
 Además `COMMAND_HANDLER`, puede usar [MESSAGE_HANDLER](#message_handler) para asignar un **WM_COMMAND** mensaje sin tener en cuenta un identificador o código. En este caso, `MESSAGE_HANDLER(WM_COMMAND, OnHandlerFunction)` dirigirá todos **WM_COMMAND** mensajes a `OnHandlerFunction`.  
  
 Para obtener más información sobre el uso de mapas de mensajes en ATL, vea [mapas de mensajes](../../atl/message-maps-atl.md).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h   
  
##  <a name="a-namecommandidhandlera--commandidhandler"></a><a name="command_id_handler"></a>COMMAND_ID_HANDLER  
 Similar a [COMMAND_HANDLER](#command_handler), pero se asigna un [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) mensaje basándose sólo en el identificador del elemento de menú, control o acelerador.  
  
```
COMMAND_ID_HANDLER(id, func)
```  
  
### <a name="parameters"></a>Parámetros  
 `id`  
 [in] El identificador del elemento de menú, control o Acelerador de enviar el mensaje.  
  
 `func`  
 [in] El nombre de la función de controlador de mensajes.  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h   
  
##  <a name="a-namecommandrangecodehandlera--commandrangecodehandler"></a><a name="command_range_code_handler"></a>COMMAND_RANGE_CODE_HANDLER  
 Similar a [COMMAND_RANGE_HANDLER](#command_range_handler), pero asigna [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) mensajes con un código de notificación específica de una variedad de controles para una función de controlador único.  
  
```
COMMAND_RANGE_CODE_HANDLER(idFirst, idLast, code, func)
```    
  
### <a name="parameters"></a>Parámetros  
 `idFirst`  
 [in] Marca el principio de un intervalo contiguo de identificadores de control.  
  
 `idLast`  
 [in] Marca el final de un intervalo contiguo de identificadores de control.  
  
 `code`  
 [in] El código de notificación.  
  
 `func`  
 [in] El nombre de la función de controlador de mensajes.  
  
### <a name="remarks"></a>Comentarios  
 Este intervalo se basa en el identificador del elemento de menú, control o Acelerador de enviar el mensaje.  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h   
  
##  <a name="a-namecommandrangehandlera--commandrangehandler"></a><a name="command_range_handler"></a>COMMAND_RANGE_HANDLER  
 Similar a [COMMAND_HANDLER](#command_handler), pero asigna [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) mensajes de una variedad de controles a una función de controlador único.  
  
```
COMMAND_RANGE_HANDLER( idFirst, idLast, func)
```    
  
### <a name="parameters"></a>Parámetros  
 `idFirst`  
 [in] Marca el principio de un intervalo contiguo de identificadores de control.  
  
 `idLast`  
 [in] Marca el final de un intervalo contiguo de identificadores de control.  
  
 `func`  
 [in] El nombre de la función de controlador de mensajes.  
  
### <a name="remarks"></a>Comentarios  
 Este intervalo se basa en el identificador del elemento de menú, control o Acelerador de enviar el mensaje.  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h   
  
##  <a name="a-namedeclareemptymsgmapa--declareemptymsgmap"></a><a name="declare_empty_msg_map"></a>DECLARE_EMPTY_MSG_MAP  
 Declara un mapa de mensajes vacío.  
  
```
DECLARE_EMPTY_MSG_MAP()
```  
  
### <a name="remarks"></a>Comentarios  
 `DECLARE_EMPTY_MSG_MAP`es una macro de conveniencia que llama a las macros [BEGIN_MSG_MAP](#begin_msg_map) y [END_MSG_MAP](#end_msg_map) para crear un mapa de mensajes vacío:  
  
 [!code-cpp[NVC_ATL_Windowing&#122;](../../atl/codesnippet/cpp/message-map-macros-atl_7.h)]  
  
##  <a name="a-namedefaultreflectionhandlera--defaultreflectionhandler"></a><a name="default_reflection_handler"></a>DEFAULT_REFLECTION_HANDLER  
 Proporciona un controlador predeterminado para la ventana secundaria (control) que recibirá los mensajes; reflejados el controlador pasará correctamente los mensajes no controlados para `DefWindowProc`.  
  
```
DEFAULT_REFLECTION_HANDLER()
```  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h   
  
##  <a name="a-nameendmsgmapa--endmsgmap"></a><a name="end_msg_map"></a>END_MSG_MAP  
 Marca el final de un mapa de mensajes.  
  
```
END_MSG_MAP()
```  
  
### <a name="remarks"></a>Comentarios  
 Utilice siempre la [BEGIN_MSG_MAP](#begin_msg_map) macro para indicar el comienzo de un mapa de mensajes. Utilice [ALT_MSG_MAP](#alt_msg_map) para declarar los mapas de mensajes alternativos subsiguientes.  
  
 Tenga en cuenta que siempre hay exactamente una instancia de `BEGIN_MSG_MAP` y `END_MSG_MAP`.  
  
 Para obtener más información sobre el uso de mapas de mensajes en ATL, vea [mapas de mensajes](../../atl/message-maps-atl.md).  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el mapa de mensajes predeterminado y la asignación de un mensaje alternativo, cada una con una función de controlador:  
  
 [!code-cpp[NVC_ATL_Windowing&#98;](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]  
  
 El ejemplo siguiente muestra dos mapas de mensajes alternativos. El mapa de mensajes predeterminado está vacío.  
  
 [!code-cpp[NVC_ATL_Windowing&#99;](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h   
  
##  <a name="a-nameforwardnotificationsa--forwardnotifications"></a><a name="forward_notifications"></a>FORWARD_NOTIFICATIONS  
 Reenvía los mensajes de notificación a la ventana primaria.  
  
```
FORWARD_NOTIFICATIONS()
```  
  
### <a name="remarks"></a>Comentarios  
 Especifique esta macro como parte de su mapa de mensajes.  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h   
  
##  <a name="a-namemessagehandlera--messagehandler"></a><a name="message_handler"></a>MESSAGE_HANDLER  
 Define una entrada en un mapa de mensajes.  
  
```
MESSAGE_HANDLER( msg, func )
```  
  
### <a name="parameters"></a>Parámetros  
 `msg`  
 [in] Mensaje de Windows.  
  
 `func`  
 [in] El nombre de la función de controlador de mensajes.  
  
### <a name="remarks"></a>Comentarios  
 `MESSAGE_HANDLER`asigna un mensaje de Windows a la función de controlador especificado.  
  
 Cualquier función especificada en un `MESSAGE_HANDLER` macro debe definirse como sigue:  
  
 `LRESULT MessageHandler(UINT uMsg, WPARAM wParam, LPARAM lParam, BOOL& bHandled);`  
  
 Los conjuntos de mapa de mensajes `bHandled` a **TRUE** antes de `MessageHandler` se llama. Si `MessageHandler` no controla totalmente el mensaje, se debe establecer `bHandled` a **FALSE** para indicar que el mensaje requiere un procesamiento adicional.  
  
> [!NOTE]
>  Siempre comienzan con un mapa de mensajes [BEGIN_MSG_MAP](#begin_msg_map). Puede declarar mapas de mensajes alternativos posteriores con [ALT_MSG_MAP](#alt_msg_map). El [END_MSG_MAP](#end_msg_map) macro marca el final del mapa de mensajes. Cada mapa de mensajes debe tener exactamente una instancia de `BEGIN_MSG_MAP` y `END_MSG_MAP`.  
  
 Además `MESSAGE_HANDLER`, puede usar [COMMAND_HANDLER](#command_handler) y [NOTIFY_HANDLER](#notify_handler) asignar [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) y [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583) mensajes, respectivamente.  
  
 Para obtener más información sobre el uso de mapas de mensajes en ATL, vea [mapas de mensajes](../../atl/message-maps-atl.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#129;](../../atl/codesnippet/cpp/message-map-macros-atl_8.h)]  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h   
  
##  <a name="a-namemessagerangehandlera--messagerangehandler"></a><a name="message_range_handler"></a>MESSAGE_RANGE_HANDLER  
 Similar a [MESSAGE_HANDLER](#message_handler), pero los mapas de mensajes de un intervalo de Windows a una función de controlador único.  
  
```
MESSAGE_RANGE_HANDLER( msgFirst, msgLast, func )
```  
  
### <a name="parameters"></a>Parámetros  
 *msgFirst*  
 [in] Marca el principio de un intervalo contiguo de mensajes.  
  
 *msgLast*  
 [in] Marca el final de un intervalo contiguo de mensajes.  
  
 `func`  
 [in] El nombre de la función de controlador de mensajes.  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h   
  
##  <a name="a-namenotifycodehandlera--notifycodehandler"></a><a name="notify_code_handler"></a>NOTIFY_CODE_HANDLER  
 Similar a [NOTIFY_HANDLER](#notify_handler), pero se asigna un [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583) mensaje basándose únicamente en el código de notificación.  
  
```
NOTIFY_CODE_HANDLER(cd, func)
```  
  
### <a name="parameters"></a>Parámetros  
 `cd`  
 [in] El código de notificación.  
  
 `func`  
 [in] El nombre de la función de controlador de mensajes.  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h   
  
##  <a name="a-namenotifyhandlera--notifyhandler"></a><a name="notify_handler"></a>NOTIFY_HANDLER  
 Define una entrada en un mapa de mensajes.  
  
```
NOTIFY_HANDLER( id, cd, func )
```  
  
### <a name="parameters"></a>Parámetros  
 `id`  
 [in] El identificador del control que envía el mensaje.  
  
 `cd`  
 [in] El código de notificación.  
  
 `func`  
 [in] El nombre de la función de controlador de mensajes.  
  
### <a name="remarks"></a>Comentarios  
 `NOTIFY_HANDLER`asigna un [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583) mensaje a la función de controlador especificado, basada en el código de notificación y el identificador del control.  
  
 Cualquier función especificada en un `NOTIFY_HANDLER` macro debe definirse como sigue:  
  
 `LRESULT NotifyHandler(int idCtrl, LPNMHDR pnmh, BOOL& bHandled);`  
  
 Los conjuntos de mapa de mensajes `bHandled` a **TRUE** antes de `NotifyHandler` se llama. Si `NotifyHandler` no controla totalmente el mensaje, se debe establecer `bHandled` a **FALSE** para indicar que el mensaje requiere un procesamiento adicional.  
  
> [!NOTE]
>  Siempre comienzan con un mapa de mensajes [BEGIN_MSG_MAP](#begin_msg_map). Puede declarar mapas de mensajes alternativos posteriores con [ALT_MSG_MAP](#alt_msg_map). El [END_MSG_MAP](#end_msg_map) macro marca el final del mapa de mensajes. Cada mapa de mensajes debe tener exactamente una instancia de `BEGIN_MSG_MAP` y `END_MSG_MAP`.  
  
 Además `NOTIFY_HANDLER`, puede usar [MESSAGE_HANDLER](#message_handler) para asignar un **WM_NOTIFY** mensaje sin tener en cuenta un identificador o código. En este caso, `MESSAGE_HANDLER(WM_NOTIFY, OnHandlerFunction)` dirigirá todos **WM_NOTIFY** mensajes a `OnHandlerFunction`.  
  
 Para obtener más información sobre el uso de mapas de mensajes en ATL, vea [mapas de mensajes](../../atl/message-maps-atl.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#130;](../../atl/codesnippet/cpp/message-map-macros-atl_9.h)]  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h   
  
##  <a name="a-namenotifyidhandlera--notifyidhandler"></a><a name="notify_id_handler"></a>NOTIFY_ID_HANDLER  
 Similar a [NOTIFY_HANDLER](#notify_handler), pero se asigna un [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583) mensaje basándose únicamente en el identificador del control.  
  
```
NOTIFY_ID_HANDLER( id, func )
```  
  
### <a name="parameters"></a>Parámetros  
 `id`  
 [in] El identificador del control que envía el mensaje.  
  
 `func`  
 [in] El nombre de la función de controlador de mensajes.  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h   
  
##  <a name="a-namenotifyrangecodehandlera--notifyrangecodehandler"></a><a name="notify_range_code_handler"></a>NOTIFY_RANGE_CODE_HANDLER  
 Similar a [NOTIFY_RANGE_HANDLER](#notify_range_handler), pero asigna [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583) mensajes con un código de notificación específica de una variedad de controles para una función de controlador único.  
  
```
NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```  
  
### <a name="parameters"></a>Parámetros  
 `idFirst`  
 [in] Marca el principio de un intervalo contiguo de identificadores de control.  
  
 `idLast`  
 [in] Marca el final de un intervalo contiguo de identificadores de control.  
  
 `cd`  
 [in] El código de notificación.  
  
 `func`  
 [in] El nombre de la función de controlador de mensajes.  
  
### <a name="remarks"></a>Comentarios  
 Este intervalo se basa en el identificador del control que envía el mensaje.  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h   
  
##  <a name="a-namenotifyrangehandlera--notifyrangehandler"></a><a name="notify_range_handler"></a>NOTIFY_RANGE_HANDLER  
 Similar a [NOTIFY_HANDLER](#notify_handler), pero asigna [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583) mensajes de una variedad de controles a una función de controlador único.  
  
```
NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```  
  
### <a name="parameters"></a>Parámetros  
 `idFirst`  
 [in] Marca el principio de un intervalo contiguo de identificadores de control.  
  
 `idLast`  
 [in] Marca el final de un intervalo contiguo de identificadores de control.  
  
 `func`  
 [in] El nombre de la función de controlador de mensajes.  
  
### <a name="remarks"></a>Comentarios  
 Este intervalo se basa en el identificador del control que envía el mensaje.  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h   
  
##  <a name="a-namereflectnotificationsa--reflectnotifications"></a><a name="reflect_notifications"></a>REFLECT_NOTIFICATIONS  
 Refleja los mensajes de notificación a la ventana secundaria (control) que envían.  
  
```
REFLECT_NOTIFICATIONS()
```  
  
### <a name="remarks"></a>Comentarios  
 Especifique esta macro como parte del mapa de mensajes de la ventana primaria.  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h   
  
##  <a name="a-namereflectedcommandcodehandlera--reflectedcommandcodehandler"></a><a name="reflected_command_code_handler"></a>REFLECTED_COMMAND_CODE_HANDLER  
 Similar a [COMMAND_CODE_HANDLER](#command_code_handler), pero asigna comandos reflejados desde la ventana primaria.  
  
```
REFLECTED_COMMAND_CODE_HANDLER( code, func )
```  
  
### <a name="parameters"></a>Parámetros  
 `code`  
 [in] El código de notificación.  
  
 `func`  
 [in] El nombre de la función de controlador de mensajes.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  
   
##  <a name="a-namereflectedcommandhandlera--reflectedcommandhandler"></a><a name="reflected_command_handler"></a>REFLECTED_COMMAND_HANDLER  
 Similar a [COMMAND_HANDLER](#command_handler), pero asigna comandos reflejados desde la ventana primaria.  
  
```
REFLECTED_COMMAND_HANDLER( id, code, func )
```  
  
### <a name="parameters"></a>Parámetros  
 `id`  
 [in] El identificador del elemento de menú, control o acelerador.  
  
 `code`  
 [in] El código de notificación.  
  
 `func`  
 [in] El nombre de la función de controlador de mensajes.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  

##  <a name="a-namereflectedcommandidhandlera--reflectedcommandidhandler"></a><a name="reflected_command_id_handler"></a>REFLECTED_COMMAND_ID_HANDLER  
 Similar a [COMMAND_ID_HANDLER](#command_id_handler), pero asigna comandos reflejados desde la ventana primaria.  
  
```
REFLECTED_COMMAND_ID_HANDLER( id, func )
```  
  
### <a name="parameters"></a>Parámetros  
 `id`  
 [in] El identificador del elemento de menú, control o acelerador.  
  
 `func`  
 [in] El nombre de la función de controlador de mensajes.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  

##  <a name="a-namereflectedcommandrangecodehandlera--reflectedcommandrangecodehandler"></a><a name="reflected_command_range_code_handler"></a>REFLECTED_COMMAND_RANGE_CODE_HANDLER  
 Similar a [COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler), pero asigna comandos reflejados desde la ventana primaria.  
  
```
REFLECTED_COMMAND_RANGE_CODE_HANDLER( idFirst, idLast, code, func )
```  
  
### <a name="parameters"></a>Parámetros  
 `idFirst`  
 [in] Marca el principio de un intervalo contiguo de identificadores de control.  
  
 `idLast`  
 [in] Marca el final de un intervalo contiguo de identificadores de control.  
  
 `code`  
 [in] El código de notificación.  
  
 `func`  
 [in] El nombre de la función de controlador de mensajes.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  

##  <a name="a-namereflectedcommandrangehandlera--reflectedcommandrangehandler"></a><a name="reflected_command_range_handler"></a>REFLECTED_COMMAND_RANGE_HANDLER  
 Similar a [COMMAND_RANGE_HANDLER](#command_range_handler), pero asigna comandos reflejados desde la ventana primaria.  
  
```
REFLECTED_COMMAND_RANGE_HANDLER( idFirst, idLast, func )
```  
  
### <a name="parameters"></a>Parámetros  
 `idFirst`  
 [in] Marca el principio de un intervalo contiguo de identificadores de control.  
  
 `idLast`  
 [in] Marca el final de un intervalo contiguo de identificadores de control.  
  
 `func`  
 [in] El nombre de la función de controlador de mensajes.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  

##  <a name="a-namereflectednotifycodehandlera--reflectednotifycodehandler"></a><a name="reflected_notify_code_handler"></a>REFLECTED_NOTIFY_CODE_HANDLER  
 Similar a [NOTIFY_CODE_HANDLER](#notify_code_handler), pero asigna notificaciones reflejadas desde la ventana primaria.  
  
```
REFLECTED_NOTIFY_CODE_HANDLER_EX( cd, func )
```  
  
### <a name="parameters"></a>Parámetros  
 `cd`  
 [in] El código de notificación.  
  
 `func`  
 [in] El nombre de la función de controlador de mensajes.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  

##  <a name="a-namereflectednotifyhandlera--reflectednotifyhandler"></a><a name="reflected_notify_handler"></a>REFLECTED_NOTIFY_HANDLER  
 Similar a [NOTIFY_HANDLER](#notify_handler), pero asigna notificaciones reflejadas desde la ventana primaria.  
  
```
REFLECTED_NOTIFY_HANDLER( id, cd, func )
```  
  
### <a name="parameters"></a>Parámetros  
 `id`  
 [in] El identificador del elemento de menú, control o acelerador.  
  
 `cd`  
 [in] El código de notificación.  
  
 `func`  
 [in] El nombre de la función de controlador de mensajes.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  

##  <a name="a-namereflectednotifyidhandlera--reflectednotifyidhandler"></a><a name="reflected_notify_id_handler"></a>REFLECTED_NOTIFY_ID_HANDLER  
 Similar a [NOTIFY_ID_HANDLER](#notify_id_handler), pero asigna notificaciones reflejadas desde la ventana primaria.  
  
```
REFLECTED_NOTIFY_ID_HANDLER( id, func )
```  
  
### <a name="parameters"></a>Parámetros  
 `id`  
 [in] El identificador del elemento de menú, control o acelerador.  
  
 `func`  
 [in] El nombre de la función de controlador de mensajes.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  

##  <a name="a-namereflectednotifyrangecodehandlera--reflectednotifyrangecodehandler"></a><a name="reflected_notify_range_code_handler"></a>REFLECTED_NOTIFY_RANGE_CODE_HANDLER  
 Similar a [NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler), pero asigna notificaciones reflejadas desde la ventana primaria.  
  
```
REFLECTED_NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```    
  
### <a name="parameters"></a>Parámetros  
 `idFirst`  
 [in] Marca el principio de un intervalo contiguo de identificadores de control.  
  
 `idLast`  
 [in] Marca el final de un intervalo contiguo de identificadores de control.  
  
 `cd`  
 [in] El código de notificación.  
  
 `func`  
 [in] El nombre de la función de controlador de mensajes.  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h   
  
##  <a name="a-namereflectednotifyrangehandlera--reflectednotifyrangehandler"></a><a name="reflected_notify_range_handler"></a>REFLECTED_NOTIFY_RANGE_HANDLER  
 Similar a [NOTIFY_RANGE_HANDLER](#notify_range_handler), pero asigna notificaciones reflejadas desde la ventana primaria.  
  
```
REFLECTED_NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```  
  
### <a name="parameters"></a>Parámetros  
 `idFirst`  
 [in] Marca el principio de un intervalo contiguo de identificadores de control.  
  
 `idLast`  
 [in] Marca el final de un intervalo contiguo de identificadores de control.  
  
 `func`  
 [in] El nombre de la función de controlador de mensajes.  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)

