---
title: Macros de mapa (ATL) del mensaje | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlwin/ATL::ALT_MSG_MAP
- atlwin/ATL::BEGIN_MSG_MAP
- atlwin/ATL::CHAIN_MSG_MAP_ALT
- atlwin/ATL::CHAIN_MSG_MAP_ALT_MEMBER
- atlwin/ATL::CHAIN_MSG_MAP
- atlwin/ATL::CHAIN_MSG_MAP_DYNAMIC
- atlwin/ATL::CHAIN_MSG_MAP_MEMBER
- atlwin/ATL::COMMAND_CODE_HANDLER
- atlwin/ATL::COMMAND_HANDLER
- atlwin/ATL::COMMAND_ID_HANDLER
- atlwin/ATL::COMMAND_RANGE_CODE_HANDLER
- atlwin/ATL::COMMAND_RANGE_HANDLER
- atlwin/ATL::DECLARE_EMPTY_MSG_MAP
- atlwin/ATL::DEFAULT_REFLECTION_HANDLER
- atlwin/ATL::END_MSG_MAP
- atlwin/ATL::FORWARD_NOTIFICATIONS
- atlwin/ATL::MESSAGE_HANDLER
- atlwin/ATL::MESSAGE_RANGE_HANDLER
- atlwin/ATL::NOTIFY_CODE_HANDLER
- atlwin/ATL::NOTIFY_HANDLER
- atlwin/ATL::NOTIFY_ID_HANDLER
- atlwin/ATL::NOTIFY_RANGE_CODE_HANDLER
- atlwin/ATL::NOTIFY_RANGE_HANDLER
- atlwin/ATL::REFLECT_NOTIFICATIONS
- atlwin/ATL::REFLECTED_COMMAND_CODE_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_ID_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_RANGE_CODE_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_RANGE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_CODE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_ID_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_RANGE_CODE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_RANGE_HANDLER
dev_langs:
- C++
ms.assetid: eefdd546-8934-4a30-b263-9c06a8addcbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fbfd58491981cdba1b3aa3002736f49a7c09038c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054481"
---
# <a name="message-map-macros-atl"></a>Macros de mapa de mensajes (ATL)

Estas macros definen entradas y mapas de mensajes.

|||
|-|-|
|[ALT_MSG_MAP](#alt_msg_map)|Marca el principio de un mapa de mensajes alternativo.|
|[BEGIN_MSG_MAP](#begin_msg_map)|Marca el principio del mapa de mensajes de forma predeterminada.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Se encadena a un mapa de mensajes alternativo en la clase base.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Se encadena a un mapa de mensajes alternativo en un miembro de datos de la clase.|
|[CHAIN_MSG_MAP](#chain_msg_map)|Cadenas para el mapa de mensajes de forma predeterminada en la clase base.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Cadenas para el mapa de mensajes en otra clase en tiempo de ejecución.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Cadenas para el mapa de mensajes de forma predeterminada en un miembro de datos de la clase.|
|[COMMAND_CODE_HANDLER](#command_code_handler)|Un mensaje WM_COMMAND se asigna a una función de controlador, según el código de notificación.|
|[COMMAND_HANDLER](#command_handler)|Un mensaje WM_COMMAND se asigna a una función de controlador, según el código de notificación y el identificador del elemento de menú, control o acelerador.|
|[COMMAND_ID_HANDLER](#command_id_handler)|Un mensaje WM_COMMAND se asigna a una función de controlador, según el identificador del elemento de menú, control o acelerador.|
|[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)|Un mensaje WM_COMMAND se asigna a una función de controlador, según el código de notificación y un intervalo contiguo de identificadores de control.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Un mensaje WM_COMMAND se asigna a una función de controlador, según un intervalo contiguo de identificadores de control.|
|[DECLARE_EMPTY_MSG_MAP](#declare_empty_msg_map)|Implementa un mapa de mensajes vacíos.|
|[DEFAULT_REFLECTION_HANDLER](#default_reflection_handler)|Proporciona un controlador predeterminado para los mensajes reflejados no administradas en caso contrario.|
|[END_MSG_MAP](#end_msg_map)|Marca el final de un mapa de mensajes.|
|[FORWARD_NOTIFICATIONS](#forward_notifications)|Reenvía los mensajes de notificación a la ventana primaria.|
|[MESSAGE_HANDLER](#message_handler)|Asigna un mensaje de Windows a una función de controlador.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Los mensajes de un intervalo contiguo de Windows se asigna a una función de controlador.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Un mensaje WM_NOTIFY se asigna a una función de controlador, según el código de notificación.|
|[NOTIFY_HANDLER](#notify_handler)|Un mensaje WM_NOTIFY se asigna a una función de controlador, según el código de notificación y el identificador del control.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Un mensaje WM_NOTIFY se asigna a una función de controlador, según el identificador del control.|
|[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)|Un mensaje WM_NOTIFY se asigna a una función de controlador, según el código de notificación y un intervalo contiguo de identificadores de control.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Un mensaje WM_NOTIFY se asigna a una función de controlador, según un intervalo contiguo de identificadores de control.|
|[REFLECT_NOTIFICATIONS](#reflect_notifications)|Refleja los mensajes de notificación a la ventana que se enviaron.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Un mensaje WM_COMMAND reflejado se asigna a una función de controlador, según el código de notificación.|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Un mensaje WM_COMMAND reflejado se asigna a una función de controlador, según el código de notificación y el identificador del elemento de menú, control o acelerador.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Un mensaje WM_COMMAND reflejado se asigna a una función de controlador, según el identificador del elemento de menú, control o acelerador.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Un mensaje WM_COMMAND reflejado se asigna a una función de controlador, según el código de notificación y un intervalo contiguo de identificadores de control.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Un mensaje WM_COMMAND reflejado se asigna a una función de controlador, según un intervalo contiguo de identificadores de control.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Un mensaje WM_NOTIFY reflejado se asigna a una función de controlador, según el código de notificación.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Un mensaje WM_NOTIFY reflejado se asigna a una función de controlador, según el código de notificación y el identificador del control.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Un mensaje WM_NOTIFY reflejado se asigna a una función de controlador, según el identificador del control.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Un mensaje WM_NOTIFY reflejado se asigna a una función de controlador, según el código de notificación y un intervalo contiguo de identificadores de control.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Un mensaje WM_NOTIFY reflejado se asigna a una función de controlador, según un intervalo contiguo de identificadores de control.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="alt_msg_map"></a>  ALT_MSG_MAP

Marca el principio de un mapa de mensajes alternativo.

```
ALT_MSG_MAP(msgMapID)
```

### <a name="parameters"></a>Parámetros

*msgMapID*<br/>
[in] Identificador de asignación de mensaje.

### <a name="remarks"></a>Comentarios

ATL identifica cada mapa de mensajes por un número. El mapa de mensajes predeterminado (declarado con la macro BEGIN_MSG_MAP) se identifica por 0. Un mapa de mensajes alternativo se identifica mediante *msgMapID*.

Mapas de mensajes se utilizan para procesar los mensajes enviados a una ventana. Por ejemplo, [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) le permite especificar el identificador de un mapa de mensajes del objeto contenedor. [CContainedWindow:: WindowProc](ccontainedwindowt-class.md#windowproc) , a continuación, usa este mapa de mensajes para dirigir los mensajes de la ventana contenido a la función de controlador adecuado o al otro mapa de mensajes. Para obtener una lista de macros que declaran las funciones de controlador, consulte [BEGIN_MSG_MAP](#begin_msg_map).

Siempre empiezan con BEGIN_MSG_MAP un mapa de mensajes. A continuación, puede declarar mapas de mensajes alternativos posteriores.

El [END_MSG_MAP](#end_msg_map) macro marca el final del mapa de mensajes. Tenga en cuenta que siempre hay exactamente una instancia de BEGIN_MSG_MAP y END_MSG_MAP.

Para obtener más información sobre el uso de mapas de mensajes en ATL, vea [mapas de mensajes](../../atl/message-maps-atl.md).

### <a name="example"></a>Ejemplo

El ejemplo siguiente muestra el mapa de mensajes predeterminado y la asignación de un mensaje alternativo, cada una con una función de controlador:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

El siguiente ejemplo muestra dos mapas de mensajes alternativos. El mapa de mensajes predeterminado está vacío.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="begin_msg_map"></a>  BEGIN_MSG_MAP

Marca el principio del mapa de mensajes de forma predeterminada.

```
BEGIN_MSG_MAP(theClass)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
[in] El nombre de la clase que contiene el mapa de mensajes.

### <a name="remarks"></a>Comentarios

[CWindowImpl:: WindowProc](cwindowimpl-class.md#windowproc) usa el mapa de mensajes de forma predeterminada para procesar los mensajes enviados a la ventana. El mapa de mensajes dirige los mensajes a la función de controlador adecuado o al otro mapa de mensajes.

Las macros siguientes asignan un mensaje a una función de controlador. Esta función debe definirse en *theClass*.

|Macro|Descripción|
|-----------|-----------------|
|[MESSAGE_HANDLER](#message_handler)|Asigna un mensaje de Windows a una función de controlador.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Los mensajes de un intervalo contiguo de Windows se asigna a una función de controlador.|
|[COMMAND_HANDLER](#command_handler)|Un mensaje WM_COMMAND se asigna a una función de controlador, según el código de notificación y el identificador del elemento de menú, control o acelerador.|
|[COMMAND_ID_HANDLER](#command_id_handler)|Un mensaje WM_COMMAND se asigna a una función de controlador, según el identificador del elemento de menú, control o acelerador.|
|[COMMAND_CODE_HANDLER](#command_handler)|Un mensaje WM_COMMAND se asigna a una función de controlador, según el código de notificación.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Asigna un intervalo contiguo de WM_COMMAND (mensajes) a una función de controlador, según el identificador del elemento de menú, control o acelerador.|
|[NOTIFY_HANDLER](#notify_handler)|Un mensaje WM_NOTIFY se asigna a una función de controlador, según el código de notificación y el identificador del control.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Un mensaje WM_NOTIFY se asigna a una función de controlador, según el identificador del control.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Un mensaje WM_NOTIFY se asigna a una función de controlador, según el código de notificación.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Los mensajes de un intervalo contiguo de WM_NOTIFY se asigna a una función de controlador, según el identificador del control.|

Las macros siguientes dirigen los mensajes al otro mapa de mensajes. Este proceso se denomina "encadenamiento".

|Macro|Descripción|
|-----------|-----------------|
|[CHAIN_MSG_MAP](#chain_msg_map)|Cadenas para el mapa de mensajes de forma predeterminada en la clase base.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Cadenas para el mapa de mensajes de forma predeterminada en un miembro de datos de la clase.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Se encadena a un mapa de mensajes alternativo en la clase base.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Se encadena a un mapa de mensajes alternativo en un miembro de datos de la clase.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Cadenas para el mapa de mensajes de forma predeterminada en otra clase en tiempo de ejecución.|

Las macros siguientes dirigen los mensajes "refleja" desde la ventana primaria. Por ejemplo, un control normalmente envía mensajes de notificación a su ventana primaria para procesamiento, pero la ventana primaria puede reflejar el mensaje al control.

|Macro|Descripción|
|-----------|-----------------|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Un mensaje WM_COMMAND reflejado se asigna a una función de controlador, según el código de notificación y el identificador del elemento de menú, control o acelerador.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Un mensaje WM_COMMAND reflejado se asigna a una función de controlador, según el identificador del elemento de menú, control o acelerador.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Un mensaje WM_COMMAND reflejado se asigna a una función de controlador, según el código de notificación.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Un mensaje WM_COMMAND reflejado se asigna a una función de controlador, según un intervalo contiguo de identificadores de control.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Un mensaje WM_COMMAND reflejado se asigna a una función de controlador, según el código de notificación y un intervalo contiguo de identificadores de control.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Un mensaje WM_NOTIFY reflejado se asigna a una función de controlador, según el código de notificación y el identificador del control.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Un mensaje WM_NOTIFY reflejado se asigna a una función de controlador, según el identificador del control.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Un mensaje WM_NOTIFY reflejado se asigna a una función de controlador, según el código de notificación.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Un mensaje WM_NOTIFY reflejado se asigna a una función de controlador, según un intervalo contiguo de identificadores de control.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Un mensaje WM_NOTIFY reflejado se asigna a una función de controlador, según el código de notificación y un intervalo contiguo de identificadores de control.|

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#102](../../atl/codesnippet/cpp/message-map-macros-atl_3.h)]

Cuando un `CMyExtWindow` objeto recibe un mensaje WM_PAINT, el mensaje se dirige a `CMyExtWindow::OnPaint` para el procesamiento real. Si `OnPaint` indica el mensaje requiere procesamiento, la voluntad de mensaje, a continuación, se dirige al mapa de mensajes de forma predeterminada en `CMyBaseWindow`.

Además el mapa de mensajes de forma predeterminada, puede definir un mapa de mensajes alternativo con [ALT_MSG_MAP](#alt_msg_map). Siempre empiezan con BEGIN_MSG_MAP un mapa de mensajes. A continuación, puede declarar mapas de mensajes alternativos posteriores. El ejemplo siguiente muestra el mapa de mensajes predeterminado y la asignación de un mensaje alternativo, cada una con una función de controlador:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

El siguiente ejemplo muestra dos mapas de mensajes alternativos. El mapa de mensajes predeterminado está vacío.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

El [END_MSG_MAP](#end_msg_map) macro marca el final del mapa de mensajes. Tenga en cuenta que siempre hay exactamente una instancia de BEGIN_MSG_MAP y END_MSG_MAP.

Para obtener más información sobre el uso de mapas de mensajes en ATL, vea [mapas de mensajes](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="chain_msg_map_alt"></a>  CHAIN_MSG_MAP_ALT

Define una entrada en un mapa de mensajes.

```
CHAIN_MSG_MAP_ALT(theChainClass, msgMapID)
```

### <a name="parameters"></a>Parámetros

*theChainClass*<br/>
[in] El nombre de la clase base que contiene el mapa de mensajes.

*msgMapID*<br/>
[in] Identificador de asignación de mensaje.

### <a name="remarks"></a>Comentarios

CHAIN_MSG_MAP_ALT dirige los mensajes a un mapa de mensajes alternativo de una clase base. Debe haber declarado en este mapa de mensajes alternativo con [ALT_MSG_MAP(msgMapID)](#alt_msg_map). Para dirigir los mensajes al mapa de mensajes de una clase base predeterminada (declarado con [BEGIN_MSG_MAP](#begin_msg_map)), utilice CHAIN_MSG_MAP. Para obtener un ejemplo, vea [CHAIN_MSG_MAP](#chain_msg_map).

> [!NOTE]
>  Siempre empiezan con BEGIN_MSG_MAP un mapa de mensajes. A continuación, puede declarar mapas de mensajes alternativos posteriores con ALT_MSG_MAP. El [END_MSG_MAP](#end_msg_map) macro marca el final del mapa de mensajes. Cada mapa de mensajes debe tener exactamente una instancia de BEGIN_MSG_MAP y END_MSG_MAP.

Para obtener más información sobre el uso de mapas de mensajes en ATL, vea [mapas de mensajes](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="chain_msg_map_alt_member"></a>  CHAIN_MSG_MAP_ALT_MEMBER

Define una entrada en un mapa de mensajes.

```
CHAIN_MSG_MAP_ALT_MEMBER(theChainMember, msgMapID)
```

### <a name="parameters"></a>Parámetros

*theChainMember*<br/>
[in] El nombre del miembro de datos que contiene el mapa de mensajes.

*msgMapID*<br/>
[in] Identificador de asignación de mensaje.

### <a name="remarks"></a>Comentarios

CHAIN_MSG_MAP_ALT_MEMBER dirige los mensajes a un mapa de mensajes alternativo de un miembro de datos. Debe haber declarado en este mapa de mensajes alternativo con [ALT_MSG_MAP(msgMapID)](#alt_msg_map). Para dirigir los mensajes al mapa de mensajes de un miembro de datos predeterminado (declarado con [BEGIN_MSG_MAP](#begin_msg_map)), utilice CHAIN_MSG_MAP_MEMBER. Para obtener un ejemplo, vea [CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member).

> [!NOTE]
>  Siempre empiezan con BEGIN_MSG_MAP un mapa de mensajes. A continuación, puede declarar mapas de mensajes alternativos posteriores con ALT_MSG_MAP. El [END_MSG_MAP](#end_msg_map) macro marca el final del mapa de mensajes. Cada mapa de mensajes debe tener exactamente una instancia de BEGIN_MSG_MAP y END_MSG_MAP.

Para obtener más información sobre el uso de mapas de mensajes en ATL, vea [mapas de mensajes](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="chain_msg_map"></a>  CHAIN_MSG_MAP

Define una entrada en un mapa de mensajes.

```
CHAIN_MSG_MAP(theChainClass)
```

### <a name="parameters"></a>Parámetros

*theChainClass*<br/>
[in] El nombre de la clase base que contiene el mapa de mensajes.

### <a name="remarks"></a>Comentarios

CHAIN_MSG_MAP dirige los mensajes al mapa de mensajes de una clase base predeterminada (declarado con [BEGIN_MSG_MAP](#begin_msg_map)). Para dirigir mensajes a mapa de mensajes alternativo de una clase base (declarado con [ALT_MSG_MAP](#alt_msg_map)), utilice [CHAIN_MSG_MAP_ALT](#chain_msg_map_alt).

> [!NOTE]
>  Siempre empiezan con BEGIN_MSG_MAP un mapa de mensajes. A continuación, puede declarar mapas de mensajes alternativos posteriores con ALT_MSG_MAP. El [END_MSG_MAP](#end_msg_map) macro marca el final del mapa de mensajes. Cada mapa de mensajes debe tener exactamente una instancia de BEGIN_MSG_MAP y END_MSG_MAP.

Para obtener más información sobre el uso de mapas de mensajes en ATL, vea [mapas de mensajes](../../atl/message-maps-atl.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#107](../../atl/codesnippet/cpp/message-map-macros-atl_4.h)]

En este ejemplo se muestra lo siguiente:

- Si está usando un procedimiento de ventana `CMyClass`del mapa de mensajes predeterminado y `OnPaint` no identificador de un mensaje, el mensaje se dirige a `CMyBaseClass`del mapa de mensajes predeterminado para su procesamiento.

- Si un procedimiento de ventana está usando el mapa de mensajes alternativo primera `CMyClass`, todos los mensajes se dirigen a `CMyBaseClass`del mapa de mensajes predeterminado.

- Si está usando un procedimiento de ventana `CMyClass`del segundo mensaje alternativo se asignan y `OnChar` no identificador de un mensaje, el mensaje se dirige a la asignación de mensajes alternativos especificado en `CMyBaseClass`. `CMyBaseClass` debe haber declarado con ALT_MSG_MAP(1) este mapa de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="chain_msg_map_dynamic"></a>  CHAIN_MSG_MAP_DYNAMIC

Define una entrada en un mapa de mensajes.

```
CHAIN_MSG_MAP_DYNAMIC(dynaChainID)
```

### <a name="parameters"></a>Parámetros

*dynaChainID*<br/>
[in] El identificador único para el mapa de mensajes de un objeto.

### <a name="remarks"></a>Comentarios

CHAIN_MSG_MAP_DYNAMIC dirige los mensajes, en tiempo de ejecución para el mapa de mensajes de forma predeterminada en otro objeto. El objeto y su mapa de mensajes asociadas con *dynaChainID*, que se define a través de [CDynamicChain:: SetChainEntry](cdynamicchain-class.md#setchainentry). Debe derivar la clase de `CDynamicChain` para poder usar CHAIN_MSG_MAP_DYNAMIC. Para obtener un ejemplo, vea el [CDynamicChain](../../atl/reference/cdynamicchain-class.md) información general.

> [!NOTE]
>  Siempre empiezan con un mapa de mensajes [BEGIN_MSG_MAP](#begin_msg_map). A continuación, puede declarar mapas de mensajes alternativos posteriores con ALT_MSG_MAP. El [END_MSG_MAP](#end_msg_map) macro marca el final del mapa de mensajes. Cada mapa de mensajes debe tener exactamente una instancia de BEGIN_MSG_MAP y END_MSG_MAP.

Para obtener más información sobre el uso de mapas de mensajes en ATL, vea [mapas de mensajes](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="chain_msg_map_member"></a>  CHAIN_MSG_MAP_MEMBER

Define una entrada en un mapa de mensajes.

```
CHAIN_MSG_MAP_MEMBER(theChainMember)
```

### <a name="parameters"></a>Parámetros

*theChainMember*<br/>
[in] El nombre del miembro de datos que contiene el mapa de mensajes.

### <a name="remarks"></a>Comentarios

CHAIN_MSG_MAP_MEMBER dirige los mensajes al mapa de mensajes de un miembro de datos predeterminado (declarado con [BEGIN_MSG_MAP](#begin_msg_map)). Para dirigir los mensajes al mapa de mensajes alternativo de un miembro de datos (declarado con [ALT_MSG_MAP](#alt_msg_map)), utilice [CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member).

> [!NOTE]
>  Siempre empiezan con BEGIN_MSG_MAP un mapa de mensajes. A continuación, puede declarar mapas de mensajes alternativos posteriores con ALT_MSG_MAP. El [END_MSG_MAP](#end_msg_map) macro marca el final del mapa de mensajes. Cada mapa de mensajes debe tener exactamente una instancia de BEGIN_MSG_MAP y END_MSG_MAP.

Para obtener más información sobre el uso de mapas de mensajes en ATL, vea [mapas de mensajes](../../atl/message-maps-atl.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#108](../../atl/codesnippet/cpp/message-map-macros-atl_5.h)]

En este ejemplo se muestra lo siguiente:

- Si está usando un procedimiento de ventana `CMyClass`del mapa de mensajes predeterminado y `OnPaint` no identificador de un mensaje, el mensaje se dirige a `m_obj`del mapa de mensajes predeterminado para su procesamiento.

- Si un procedimiento de ventana está usando el mapa de mensajes alternativo primera `CMyClass`, todos los mensajes se dirigen a `m_obj`del mapa de mensajes predeterminado.

- Si está usando un procedimiento de ventana `CMyClass`del segundo mensaje alternativo se asignan y `OnChar` no identificador de un mensaje, el mensaje se dirige a la asignación de mensajes alternativo especificado de `m_obj`. Clase `CMyContainedClass` debe haber declarado con ALT_MSG_MAP(1) este mapa de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="command_code_handler"></a>  COMMAND_CODE_HANDLER

Similar a [COMMAND_HANDLER](#command_handler), pero se asigna un [WM_COMMAND](/windows/desktop/menurc/wm-command) mensaje basándose únicamente en el código de notificación.

```
COMMAND_CODE_HANDLER(code, func)
```

### <a name="parameters"></a>Parámetros

*code*<br/>
[in] El código de notificación.

*func*<br/>
[in] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="command_handler"></a>  COMMAND_HANDLER

Define una entrada en un mapa de mensajes.

```
COMMAND_HANDLER(id, code, func)
```

### <a name="parameters"></a>Parámetros

*identificador*<br/>
[in] El identificador del elemento de menú, control o acelerador.

*code*<br/>
[in] El código de notificación.

*func*<br/>
[in] El nombre de la función de controlador de mensajes.

### <a name="remarks"></a>Comentarios

COMMAND_HANDLER asigna un [WM_COMMAND](/windows/desktop/menurc/wm-command) mensaje a la función de controlador especificado, según el código de notificación y el identificador del control. Por ejemplo:

[!code-cpp[NVC_ATL_Windowing#119](../../atl/codesnippet/cpp/message-map-macros-atl_6.h)]

Cualquier función especificada en una macro COMMAND_HANDLER debe definirse como sigue:

`LRESULT CommandHandler(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled);`

Los conjuntos de mapa de mensajes `bHandled` en TRUE antes de `CommandHandler` se llama. Si `CommandHandler` no controla totalmente el mensaje, se debe establecer `bHandled` en FALSE para indicar que el mensaje requiere un procesamiento posterior.

> [!NOTE]
>  Siempre empiezan con un mapa de mensajes [BEGIN_MSG_MAP](#begin_msg_map). A continuación, puede declarar mapas de mensajes alternativos posteriores con [ALT_MSG_MAP](#alt_msg_map). El [END_MSG_MAP](#end_msg_map) macro marca el final del mapa de mensajes. Cada mapa de mensajes debe tener exactamente una instancia de BEGIN_MSG_MAP y END_MSG_MAP.

Además de COMMAND_HANDLER, puede usar [MESSAGE_HANDLER](#message_handler) para asignar un mensaje WM_COMMAND sin tener en cuenta un identificador o código. En este caso, `MESSAGE_HANDLER(WM_COMMAND, OnHandlerFunction)` le indica que todos los mensajes WM_COMMAND `OnHandlerFunction`.

Para obtener más información sobre el uso de mapas de mensajes en ATL, vea [mapas de mensajes](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="command_id_handler"></a>  COMMAND_ID_HANDLER

Similar a [COMMAND_HANDLER](#command_handler), pero se asigna un [WM_COMMAND](/windows/desktop/menurc/wm-command) mensaje solo según el identificador del elemento de menú, control o acelerador.

```
COMMAND_ID_HANDLER(id, func)
```

### <a name="parameters"></a>Parámetros

*identificador*<br/>
[in] El identificador del elemento de menú, el control o el Acelerador de enviar el mensaje.

*func*<br/>
[in] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="command_range_code_handler"></a>  COMMAND_RANGE_CODE_HANDLER

Similar a [COMMAND_RANGE_HANDLER](#command_range_handler), pero asigna [WM_COMMAND](/windows/desktop/menurc/wm-command) mensajes con un código de notificación específico desde una variedad de controles a una función de controlador único.

```
COMMAND_RANGE_CODE_HANDLER(idFirst, idLast, code, func)
```

### <a name="parameters"></a>Parámetros

*idFirst*<br/>
[in] Marca el principio de un intervalo contiguo de identificadores de control.

*idLast*<br/>
[in] Marca el final de un intervalo contiguo de identificadores de control.

*code*<br/>
[in] El código de notificación.

*func*<br/>
[in] El nombre de la función de controlador de mensajes.

### <a name="remarks"></a>Comentarios

Este intervalo se basa en el identificador del elemento de menú, el control o el Acelerador de enviar el mensaje.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="command_range_handler"></a>  COMMAND_RANGE_HANDLER

Similar a [COMMAND_HANDLER](#command_handler), pero asigna [WM_COMMAND](/windows/desktop/menurc/wm-command) mensajes de una gama de controles a una función de controlador único.

```
COMMAND_RANGE_HANDLER( idFirst, idLast, func)
```

### <a name="parameters"></a>Parámetros

*idFirst*<br/>
[in] Marca el principio de un intervalo contiguo de identificadores de control.

*idLast*<br/>
[in] Marca el final de un intervalo contiguo de identificadores de control.

*func*<br/>
[in] El nombre de la función de controlador de mensajes.

### <a name="remarks"></a>Comentarios

Este intervalo se basa en el identificador del elemento de menú, el control o el Acelerador de enviar el mensaje.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="declare_empty_msg_map"></a>  DECLARE_EMPTY_MSG_MAP

Declara una asignación de mensaje vacío.

```
DECLARE_EMPTY_MSG_MAP()
```

### <a name="remarks"></a>Comentarios

DECLARE_EMPTY_MSG_MAP es una macro de conveniencia que llama a las macros [BEGIN_MSG_MAP](#begin_msg_map) y [END_MSG_MAP](#end_msg_map) para crear un mapa de mensajes vacíos:

[!code-cpp[NVC_ATL_Windowing#122](../../atl/codesnippet/cpp/message-map-macros-atl_7.h)]

##  <a name="default_reflection_handler"></a>  DEFAULT_REFLECTION_HANDLER

Proporciona un controlador predeterminado para la ventana secundaria (control) que va a recibir mensajes; de reflejados el controlador pasará correctamente los mensajes no controlados `DefWindowProc`.

```
DEFAULT_REFLECTION_HANDLER()
```

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="end_msg_map"></a>  END_MSG_MAP

Marca el final de un mapa de mensajes.

```
END_MSG_MAP()
```

### <a name="remarks"></a>Comentarios

Use siempre la [BEGIN_MSG_MAP](#begin_msg_map) macro para marcar el principio de un mapa de mensajes. Use [ALT_MSG_MAP](#alt_msg_map) para declarar los mapas de mensajes alternativos posteriores.

Tenga en cuenta que siempre hay exactamente una instancia de BEGIN_MSG_MAP y END_MSG_MAP.

Para obtener más información sobre el uso de mapas de mensajes en ATL, vea [mapas de mensajes](../../atl/message-maps-atl.md).

### <a name="example"></a>Ejemplo

El ejemplo siguiente muestra el mapa de mensajes predeterminado y la asignación de un mensaje alternativo, cada una con una función de controlador:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

El siguiente ejemplo muestra dos mapas de mensajes alternativos. El mapa de mensajes predeterminado está vacío.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="forward_notifications"></a>  FORWARD_NOTIFICATIONS

Reenvía los mensajes de notificación a la ventana primaria.

```
FORWARD_NOTIFICATIONS()
```

### <a name="remarks"></a>Comentarios

Especifique esta macro como parte de su mapa de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="message_handler"></a>  MESSAGE_HANDLER

Define una entrada en un mapa de mensajes.

```
MESSAGE_HANDLER( msg, func )
```

### <a name="parameters"></a>Parámetros

*mens.*<br/>
[in] El mensaje de Windows.

*func*<br/>
[in] El nombre de la función de controlador de mensajes.

### <a name="remarks"></a>Comentarios

MESSAGE_HANDLER asigna un mensaje de Windows a la función de controlador especificado.

Cualquier función especificada en una macro MESSAGE_HANDLER debe definirse como sigue:

`LRESULT MessageHandler(UINT uMsg, WPARAM wParam, LPARAM lParam, BOOL& bHandled);`

Los conjuntos de mapa de mensajes `bHandled` en TRUE antes de `MessageHandler` se llama. Si `MessageHandler` no controla totalmente el mensaje, se debe establecer `bHandled` en FALSE para indicar que el mensaje requiere un procesamiento posterior.

> [!NOTE]
>  Siempre empiezan con un mapa de mensajes [BEGIN_MSG_MAP](#begin_msg_map). A continuación, puede declarar mapas de mensajes alternativos posteriores con [ALT_MSG_MAP](#alt_msg_map). El [END_MSG_MAP](#end_msg_map) macro marca el final del mapa de mensajes. Cada mapa de mensajes debe tener exactamente una instancia de BEGIN_MSG_MAP y END_MSG_MAP.

Además de MESSAGE_HANDLER, puede usar [COMMAND_HANDLER](#command_handler) y [NOTIFY_HANDLER](#notify_handler) para asignar [WM_COMMAND](/windows/desktop/menurc/wm-command) y [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583) mensajes , respectivamente.

Para obtener más información sobre el uso de mapas de mensajes en ATL, vea [mapas de mensajes](../../atl/message-maps-atl.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#129](../../atl/codesnippet/cpp/message-map-macros-atl_8.h)]

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="message_range_handler"></a>  MESSAGE_RANGE_HANDLER

Similar a [MESSAGE_HANDLER](#message_handler), pero se asigna un intervalo de Windows los mensajes a una función de controlador único.

```
MESSAGE_RANGE_HANDLER( msgFirst, msgLast, func )
```

### <a name="parameters"></a>Parámetros

*msgFirst*<br/>
[in] Marca el principio de un intervalo contiguo de mensajes.

*msgLast*<br/>
[in] Marca el final de un intervalo contiguo de mensajes.

*func*<br/>
[in] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="notify_code_handler"></a>  NOTIFY_CODE_HANDLER

Similar a [NOTIFY_HANDLER](#notify_handler), pero se asigna un [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583) mensaje basándose únicamente en el código de notificación.

```
NOTIFY_CODE_HANDLER(cd, func)
```

### <a name="parameters"></a>Parámetros

*CD*<br/>
[in] El código de notificación.

*func*<br/>
[in] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="notify_handler"></a>  NOTIFY_HANDLER

Define una entrada en un mapa de mensajes.

```
NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>Parámetros

*identificador*<br/>
[in] El identificador del control que envía el mensaje.

*CD*<br/>
[in] El código de notificación.

*func*<br/>
[in] El nombre de la función de controlador de mensajes.

### <a name="remarks"></a>Comentarios

NOTIFY_HANDLER asigna un [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583) mensaje a la función de controlador especificado, según el código de notificación y el identificador del control.

Cualquier función especificada en una macro NOTIFY_HANDLER debe definirse como sigue:

`LRESULT NotifyHandler(int idCtrl, LPNMHDR pnmh, BOOL& bHandled);`

Los conjuntos de mapa de mensajes `bHandled` en TRUE antes de `NotifyHandler` se llama. Si `NotifyHandler` no controla totalmente el mensaje, se debe establecer `bHandled` en FALSE para indicar que el mensaje requiere un procesamiento posterior.

> [!NOTE]
>  Siempre empiezan con un mapa de mensajes [BEGIN_MSG_MAP](#begin_msg_map). A continuación, puede declarar mapas de mensajes alternativos posteriores con [ALT_MSG_MAP](#alt_msg_map). El [END_MSG_MAP](#end_msg_map) macro marca el final del mapa de mensajes. Cada mapa de mensajes debe tener exactamente una instancia de BEGIN_MSG_MAP y END_MSG_MAP.

Además de NOTIFY_HANDLER, puede usar [MESSAGE_HANDLER](#message_handler) para asignar un mensaje WM_NOTIFY sin tener en cuenta un identificador o código. En este caso, `MESSAGE_HANDLER(WM_NOTIFY, OnHandlerFunction)` dirigirá a todos los mensajes WM_NOTIFY `OnHandlerFunction`.

Para obtener más información sobre el uso de mapas de mensajes en ATL, vea [mapas de mensajes](../../atl/message-maps-atl.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#130](../../atl/codesnippet/cpp/message-map-macros-atl_9.h)]

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="notify_id_handler"></a>  NOTIFY_ID_HANDLER

Similar a [NOTIFY_HANDLER](#notify_handler), pero se asigna un [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583) mensaje solo según el identificador del control.

```
NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parámetros

*identificador*<br/>
[in] El identificador del control que envía el mensaje.

*func*<br/>
[in] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="notify_range_code_handler"></a>  NOTIFY_RANGE_CODE_HANDLER

Similar a [NOTIFY_RANGE_HANDLER](#notify_range_handler), pero asigna [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583) mensajes con un código de notificación específico desde una variedad de controles a una función de controlador único.

```
NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>Parámetros

*idFirst*<br/>
[in] Marca el principio de un intervalo contiguo de identificadores de control.

*idLast*<br/>
[in] Marca el final de un intervalo contiguo de identificadores de control.

*CD*<br/>
[in] El código de notificación.

*func*<br/>
[in] El nombre de la función de controlador de mensajes.

### <a name="remarks"></a>Comentarios

Este intervalo se basa en el identificador del control que envía el mensaje.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="notify_range_handler"></a>  NOTIFY_RANGE_HANDLER

Similar a [NOTIFY_HANDLER](#notify_handler), pero asigna [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583) mensajes de una gama de controles a una función de controlador único.

```
NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parámetros

*idFirst*<br/>
[in] Marca el principio de un intervalo contiguo de identificadores de control.

*idLast*<br/>
[in] Marca el final de un intervalo contiguo de identificadores de control.

*func*<br/>
[in] El nombre de la función de controlador de mensajes.

### <a name="remarks"></a>Comentarios

Este intervalo se basa en el identificador del control que envía el mensaje.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="reflect_notifications"></a>  REFLECT_NOTIFICATIONS

Refleja los mensajes de notificación a la ventana secundaria (control) que les enviado.

```
REFLECT_NOTIFICATIONS()
```

### <a name="remarks"></a>Comentarios

Especifique esta macro como parte del mapa de mensajes de la ventana primaria.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="reflected_command_code_handler"></a>  REFLECTED_COMMAND_CODE_HANDLER

Similar a [COMMAND_CODE_HANDLER](#command_code_handler), pero asigna comandos reflejados desde la ventana primaria.

```
REFLECTED_COMMAND_CODE_HANDLER( code, func )
```

### <a name="parameters"></a>Parámetros

*code*<br/>
[in] El código de notificación.

*func*<br/>
[in] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="reflected_command_handler"></a>  REFLECTED_COMMAND_HANDLER

Similar a [COMMAND_HANDLER](#command_handler), pero asigna comandos reflejados desde la ventana primaria.

```
REFLECTED_COMMAND_HANDLER( id, code, func )
```

### <a name="parameters"></a>Parámetros

*identificador*<br/>
[in] El identificador del elemento de menú, control o acelerador.

*code*<br/>
[in] El código de notificación.

*func*<br/>
[in] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="reflected_command_id_handler"></a>  REFLECTED_COMMAND_ID_HANDLER

Similar a [COMMAND_ID_HANDLER](#command_id_handler), pero asigna comandos reflejados desde la ventana primaria.

```
REFLECTED_COMMAND_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parámetros

*identificador*<br/>
[in] El identificador del elemento de menú, control o acelerador.

*func*<br/>
[in] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="reflected_command_range_code_handler"></a>  REFLECTED_COMMAND_RANGE_CODE_HANDLER

Similar a [COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler), pero asigna comandos reflejados desde la ventana primaria.

```
REFLECTED_COMMAND_RANGE_CODE_HANDLER( idFirst, idLast, code, func )
```

### <a name="parameters"></a>Parámetros

*idFirst*<br/>
[in] Marca el principio de un intervalo contiguo de identificadores de control.

*idLast*<br/>
[in] Marca el final de un intervalo contiguo de identificadores de control.

*code*<br/>
[in] El código de notificación.

*func*<br/>
[in] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="reflected_command_range_handler"></a>  REFLECTED_COMMAND_RANGE_HANDLER

Similar a [COMMAND_RANGE_HANDLER](#command_range_handler), pero asigna comandos reflejados desde la ventana primaria.

```
REFLECTED_COMMAND_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parámetros

*idFirst*<br/>
[in] Marca el principio de un intervalo contiguo de identificadores de control.

*idLast*<br/>
[in] Marca el final de un intervalo contiguo de identificadores de control.

*func*<br/>
[in] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="reflected_notify_code_handler"></a>  REFLECTED_NOTIFY_CODE_HANDLER

Similar a [NOTIFY_CODE_HANDLER](#notify_code_handler), pero asigna las notificaciones reflejadas desde la ventana primaria.

```
REFLECTED_NOTIFY_CODE_HANDLER_EX( cd, func )
```

### <a name="parameters"></a>Parámetros

*CD*<br/>
[in] El código de notificación.

*func*<br/>
[in] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="reflected_notify_handler"></a>  REFLECTED_NOTIFY_HANDLER

Similar a [NOTIFY_HANDLER](#notify_handler), pero asigna las notificaciones reflejadas desde la ventana primaria.

```
REFLECTED_NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>Parámetros

*identificador*<br/>
[in] El identificador del elemento de menú, control o acelerador.

*CD*<br/>
[in] El código de notificación.

*func*<br/>
[in] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="reflected_notify_id_handler"></a>  REFLECTED_NOTIFY_ID_HANDLER

Similar a [NOTIFY_ID_HANDLER](#notify_id_handler), pero asigna las notificaciones reflejadas desde la ventana primaria.

```
REFLECTED_NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parámetros

*identificador*<br/>
[in] El identificador del elemento de menú, control o acelerador.

*func*<br/>
[in] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="reflected_notify_range_code_handler"></a>  REFLECTED_NOTIFY_RANGE_CODE_HANDLER

Similar a [NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler), pero asigna las notificaciones reflejadas desde la ventana primaria.

```
REFLECTED_NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>Parámetros

*idFirst*<br/>
[in] Marca el principio de un intervalo contiguo de identificadores de control.

*idLast*<br/>
[in] Marca el final de un intervalo contiguo de identificadores de control.

*CD*<br/>
[in] El código de notificación.

*func*<br/>
[in] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="reflected_notify_range_handler"></a>  REFLECTED_NOTIFY_RANGE_HANDLER

Similar a [NOTIFY_RANGE_HANDLER](#notify_range_handler), pero asigna las notificaciones reflejadas desde la ventana primaria.

```
REFLECTED_NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parámetros

*idFirst*<br/>
[in] Marca el principio de un intervalo contiguo de identificadores de control.

*idLast*<br/>
[in] Marca el final de un intervalo contiguo de identificadores de control.

*func*<br/>
[in] El nombre de la función de controlador de mensajes.

## <a name="see-also"></a>Vea también

[Macros](../../atl/reference/atl-macros.md)
