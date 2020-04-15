---
title: Macros de mapa de mensajes (ATL)
ms.date: 11/04/2016
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
ms.assetid: eefdd546-8934-4a30-b263-9c06a8addcbd
ms.openlocfilehash: 157812fa6625869c86dd8a27156a2970a3dc8d4a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326230"
---
# <a name="message-map-macros-atl"></a>Macros de mapa de mensajes (ATL)

Estas macros definen mapas de mensajes y entradas.

|||
|-|-|
|[ALT_MSG_MAP](#alt_msg_map)|Marca el comienzo de un mapa de mensajes alternativo.|
|[BEGIN_MSG_MAP](#begin_msg_map)|Marca el principio del mapa de mensajes predeterminado.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Cadenas a un mapa de mensajes alternativo en la clase base.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Cadenas a un mapa de mensajes alternativo en un miembro de datos de la clase.|
|[CHAIN_MSG_MAP](#chain_msg_map)|Cadenas al mapa de mensajes predeterminado en la clase base.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Cadenas al mapa de mensajes en otra clase en tiempo de ejecución.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Cadenas al mapa de mensajes predeterminado en un miembro de datos de la clase.|
|[COMMAND_CODE_HANDLER](#command_code_handler)|Asigna un mensaje de WM_COMMAND a una función de controlador, en función del código de notificación.|
|[COMMAND_HANDLER](#command_handler)|Asigna un mensaje de WM_COMMAND a una función de controlador, en función del código de notificación y el identificador del elemento de menú, control o acelerador.|
|[COMMAND_ID_HANDLER](#command_id_handler)|Asigna un mensaje de WM_COMMAND a una función de controlador, en función del identificador del elemento de menú, control o acelerador.|
|[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)|Asigna un mensaje de WM_COMMAND a una función de controlador, en función del código de notificación y un intervalo contiguo de identificadores de control.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Asigna un mensaje de WM_COMMAND a una función de controlador, en función de un intervalo contiguo de identificadores de control.|
|[DECLARE_EMPTY_MSG_MAP](#declare_empty_msg_map)|Implementa un mapa de mensajes vacío.|
|[DEFAULT_REFLECTION_HANDLER](#default_reflection_handler)|Proporciona un controlador predeterminado para los mensajes reflejados que no se controlan de otro modo.|
|[END_MSG_MAP](#end_msg_map)|Marca el final de un mapa de mensajes.|
|[FORWARD_NOTIFICATIONS](#forward_notifications)|Reenvía los mensajes de notificación a la ventana primaria.|
|[MESSAGE_HANDLER](#message_handler)|Asigna un mensaje de Windows a una función de controlador.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Asigna un intervalo contiguo de mensajes de Windows a una función de controlador.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Asigna un mensaje de WM_NOTIFY a una función de controlador, en función del código de notificación.|
|[NOTIFY_HANDLER](#notify_handler)|Asigna un mensaje de WM_NOTIFY a una función de controlador, en función del código de notificación y el identificador de control.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Asigna un mensaje de WM_NOTIFY a una función de controlador, en función del identificador de control.|
|[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)|Asigna un mensaje de WM_NOTIFY a una función de controlador, en función del código de notificación y un intervalo contiguo de identificadores de control.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Asigna un mensaje de WM_NOTIFY a una función de controlador, en función de un intervalo contiguo de identificadores de control.|
|[REFLECT_NOTIFICATIONS](#reflect_notifications)|Refleja los mensajes de notificación a la ventana que los envió.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Asigna un mensaje de WM_COMMAND reflejado a una función de controlador, en función del código de notificación.|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Asigna un mensaje de WM_COMMAND reflejado a una función de controlador, en función del código de notificación y el identificador del elemento de menú, control o acelerador.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Asigna un mensaje reflejado WM_COMMAND a una función de controlador, en función del identificador del elemento de menú, control o acelerador.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Asigna un mensaje de WM_COMMAND reflejado a una función de controlador, en función del código de notificación y un intervalo contiguo de identificadores de control.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Asigna un mensaje de WM_COMMAND reflejado a una función de controlador, en función de un intervalo contiguo de identificadores de control.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Asigna un mensaje reflejado WM_NOTIFY a una función de controlador, en función del código de notificación.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Asigna un mensaje de WM_NOTIFY reflejado a una función de controlador, en función del código de notificación y el identificador de control.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Asigna un mensaje de WM_NOTIFY reflejado a una función de controlador, en función del identificador de control.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Asigna un mensaje de WM_NOTIFY reflejado a una función de controlador, en función del código de notificación y un intervalo contiguo de identificadores de control.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Asigna un mensaje de WM_NOTIFY reflejado a una función de controlador, en función de un intervalo contiguo de identificadores de control.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="alt_msg_map"></a><a name="alt_msg_map"></a>ALT_MSG_MAP

Marca el comienzo de un mapa de mensajes alternativo.

```
ALT_MSG_MAP(msgMapID)
```

### <a name="parameters"></a>Parámetros

*msgMapID*<br/>
[en] El identificador del mapa de mensajes.

### <a name="remarks"></a>Observaciones

ATL identifica cada mapa de mensajes por un número. El mapa de mensajes predeterminado (declarado con la macro BEGIN_MSG_MAP) se identifica por 0. Un mapa de mensajes alternativo se identifica mediante *msgMapID*.

Los mapas de mensajes se utilizan para procesar los mensajes enviados a una ventana. Por ejemplo, [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) permite especificar el identificador de un mapa de mensajes en el objeto contenedor. [CContainedWindow::WindowProc,](ccontainedwindowt-class.md#windowproc) a continuación, utiliza este mapa de mensajes para dirigir los mensajes de la ventana contenida a la función de controlador adecuada o a otro mapa de mensajes. Para obtener una lista de macros que declaran funciones de controlador, vea [BEGIN_MSG_MAP](#begin_msg_map).

Comience siempre un mapa de mensajes con BEGIN_MSG_MAP. A continuación, puede declarar mapas de mensajes alternativos posteriores.

La macro [END_MSG_MAP](#end_msg_map) marca el final del mapa de mensajes. Tenga en cuenta que siempre hay exactamente una instancia de BEGIN_MSG_MAP y END_MSG_MAP.

Para obtener más información sobre el uso de mapas de mensajes en ATL, consulte [Mapas](../../atl/message-maps-atl.md)de mensajes .

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el mapa de mensajes predeterminado y un mapa de mensajes alternativo, cada uno de los cuales contiene una función de controlador:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

En el ejemplo siguiente se muestran dos mapas de mensajes alternativos. El mapa de mensajes predeterminado está vacío.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="begin_msg_map"></a><a name="begin_msg_map"></a>BEGIN_MSG_MAP

Marca el principio del mapa de mensajes predeterminado.

```
BEGIN_MSG_MAP(theClass)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
[en] El nombre de la clase que contiene el mapa de mensajes.

### <a name="remarks"></a>Observaciones

[CWindowImpl::WindowProc](cwindowimpl-class.md#windowproc) utiliza el mapa de mensajes predeterminado para procesar los mensajes enviados a la ventana. El mapa de mensajes dirige los mensajes a la función de controlador adecuada o a otro mapa de mensajes.

Las siguientes macros asignan un mensaje a una función de controlador. Esta función debe definirse en *theClass*.

|Macro|Descripción|
|-----------|-----------------|
|[MESSAGE_HANDLER](#message_handler)|Asigna un mensaje de Windows a una función de controlador.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Asigna un intervalo contiguo de mensajes de Windows a una función de controlador.|
|[COMMAND_HANDLER](#command_handler)|Asigna un mensaje de WM_COMMAND a una función de controlador, en función del código de notificación y el identificador del elemento de menú, control o acelerador.|
|[COMMAND_ID_HANDLER](#command_id_handler)|Asigna un mensaje de WM_COMMAND a una función de controlador, en función del identificador del elemento de menú, control o acelerador.|
|[COMMAND_CODE_HANDLER](#command_handler)|Asigna un mensaje de WM_COMMAND a una función de controlador, en función del código de notificación.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Asigna un intervalo contiguo de mensajes de WM_COMMAND a una función de controlador, en función del identificador del elemento de menú, control o acelerador.|
|[NOTIFY_HANDLER](#notify_handler)|Asigna un mensaje de WM_NOTIFY a una función de controlador, en función del código de notificación y el identificador de control.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Asigna un mensaje de WM_NOTIFY a una función de controlador, en función del identificador de control.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Asigna un mensaje de WM_NOTIFY a una función de controlador, en función del código de notificación.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Asigna un intervalo contiguo de mensajes WM_NOTIFY a una función de controlador, en función del identificador de control.|

Las siguientes macros dirigen los mensajes a otro mapa de mensajes. Este proceso se denomina "encadenamiento".

|Macro|Descripción|
|-----------|-----------------|
|[CHAIN_MSG_MAP](#chain_msg_map)|Cadenas al mapa de mensajes predeterminado en la clase base.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Cadenas al mapa de mensajes predeterminado en un miembro de datos de la clase.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Cadenas a un mapa de mensajes alternativo en la clase base.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Cadenas a un mapa de mensajes alternativo en un miembro de datos de la clase.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Cadenas al mapa de mensajes predeterminado en otra clase en tiempo de ejecución.|

Las siguientes macros dirigen mensajes "reflejados" desde la ventana primaria. Por ejemplo, un control normalmente envía mensajes de notificación a su ventana primaria para su procesamiento, pero la ventana primaria puede reflejar el mensaje de nuevo en el control.

|Macro|Descripción|
|-----------|-----------------|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Asigna un mensaje de WM_COMMAND reflejado a una función de controlador, en función del código de notificación y el identificador del elemento de menú, control o acelerador.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Asigna un mensaje reflejado WM_COMMAND a una función de controlador, en función del identificador del elemento de menú, control o acelerador.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Asigna un mensaje de WM_COMMAND reflejado a una función de controlador, en función del código de notificación.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Asigna un mensaje de WM_COMMAND reflejado a una función de controlador, en función de un intervalo contiguo de identificadores de control.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Asigna un mensaje de WM_COMMAND reflejado a una función de controlador, en función del código de notificación y un intervalo contiguo de identificadores de control.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Asigna un mensaje de WM_NOTIFY reflejado a una función de controlador, en función del código de notificación y el identificador de control.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Asigna un mensaje de WM_NOTIFY reflejado a una función de controlador, en función del identificador de control.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Asigna un mensaje reflejado WM_NOTIFY a una función de controlador, en función del código de notificación.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Asigna un mensaje de WM_NOTIFY reflejado a una función de controlador, en función de un intervalo contiguo de identificadores de control.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Asigna un mensaje de WM_NOTIFY reflejado a una función de controlador, en función del código de notificación y un intervalo contiguo de identificadores de control.|

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#102](../../atl/codesnippet/cpp/message-map-macros-atl_3.h)]

Cuando `CMyExtWindow` un objeto recibe un mensaje WM_PAINT, `CMyExtWindow::OnPaint` el mensaje se dirige a para el procesamiento real. Si `OnPaint` indica que el mensaje requiere un procesamiento adicional, el mensaje `CMyBaseWindow`se dirigirá al mapa de mensajes predeterminado en .

Además del mapa de mensajes predeterminado, puede definir un mapa de mensajes alternativo con [ALT_MSG_MAP](#alt_msg_map). Comience siempre un mapa de mensajes con BEGIN_MSG_MAP. A continuación, puede declarar mapas de mensajes alternativos posteriores. En el ejemplo siguiente se muestra el mapa de mensajes predeterminado y un mapa de mensajes alternativo, cada uno de los cuales contiene una función de controlador:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

En el ejemplo siguiente se muestran dos mapas de mensajes alternativos. El mapa de mensajes predeterminado está vacío.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

La macro [END_MSG_MAP](#end_msg_map) marca el final del mapa de mensajes. Tenga en cuenta que siempre hay exactamente una instancia de BEGIN_MSG_MAP y END_MSG_MAP.

Para obtener más información sobre el uso de mapas de mensajes en ATL, consulte [Mapas](../../atl/message-maps-atl.md)de mensajes .

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="chain_msg_map_alt"></a><a name="chain_msg_map_alt"></a>CHAIN_MSG_MAP_ALT

Define una entrada en un mapa de mensajes.

```
CHAIN_MSG_MAP_ALT(theChainClass, msgMapID)
```

### <a name="parameters"></a>Parámetros

*theChainClass*<br/>
[en] El nombre de la clase base que contiene el mapa de mensajes.

*msgMapID*<br/>
[en] El identificador del mapa de mensajes.

### <a name="remarks"></a>Observaciones

CHAIN_MSG_MAP_ALT dirige los mensajes a un mapa de mensajes alternativo en una clase base. Debe haber declarado este mapa de mensajes alternativo con [ALT_MSG_MAP(msgMapID)](#alt_msg_map). Para dirigir mensajes al mapa de mensajes predeterminado de una clase base (declarado con [BEGIN_MSG_MAP),](#begin_msg_map)utilice CHAIN_MSG_MAP. Para obtener un ejemplo, vea [CHAIN_MSG_MAP](#chain_msg_map).

> [!NOTE]
> Comience siempre un mapa de mensajes con BEGIN_MSG_MAP. A continuación, puede declarar mapas de mensajes alternativos posteriores con ALT_MSG_MAP. La macro [END_MSG_MAP](#end_msg_map) marca el final del mapa de mensajes. Cada mapa de mensajes debe tener exactamente una instancia de BEGIN_MSG_MAP y END_MSG_MAP.

Para obtener más información sobre el uso de mapas de mensajes en ATL, consulte [Mapas](../../atl/message-maps-atl.md)de mensajes .

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="chain_msg_map_alt_member"></a><a name="chain_msg_map_alt_member"></a>CHAIN_MSG_MAP_ALT_MEMBER

Define una entrada en un mapa de mensajes.

```
CHAIN_MSG_MAP_ALT_MEMBER(theChainMember, msgMapID)
```

### <a name="parameters"></a>Parámetros

*theChainMember*<br/>
[en] El nombre del miembro de datos que contiene el mapa de mensajes.

*msgMapID*<br/>
[en] El identificador del mapa de mensajes.

### <a name="remarks"></a>Observaciones

CHAIN_MSG_MAP_ALT_MEMBER dirige los mensajes a un mapa de mensajes alternativo en un miembro de datos. Debe haber declarado este mapa de mensajes alternativo con [ALT_MSG_MAP(msgMapID)](#alt_msg_map). Para dirigir mensajes al mapa de mensajes predeterminado de un miembro de datos (declarado con [BEGIN_MSG_MAP),](#begin_msg_map)utilice CHAIN_MSG_MAP_MEMBER. Para obtener un ejemplo, consulte [CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member).

> [!NOTE]
> Comience siempre un mapa de mensajes con BEGIN_MSG_MAP. A continuación, puede declarar mapas de mensajes alternativos posteriores con ALT_MSG_MAP. La macro [END_MSG_MAP](#end_msg_map) marca el final del mapa de mensajes. Cada mapa de mensajes debe tener exactamente una instancia de BEGIN_MSG_MAP y END_MSG_MAP.

Para obtener más información sobre el uso de mapas de mensajes en ATL, consulte [Mapas](../../atl/message-maps-atl.md)de mensajes .

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="chain_msg_map"></a><a name="chain_msg_map"></a>CHAIN_MSG_MAP

Define una entrada en un mapa de mensajes.

```
CHAIN_MSG_MAP(theChainClass)
```

### <a name="parameters"></a>Parámetros

*theChainClass*<br/>
[en] El nombre de la clase base que contiene el mapa de mensajes.

### <a name="remarks"></a>Observaciones

CHAIN_MSG_MAP dirige los mensajes al mapa de mensajes predeterminado de una clase base (declarado con [BEGIN_MSG_MAP](#begin_msg_map)). Para dirigir mensajes al mapa de mensajes alternativo de una clase base (declarado con [ALT_MSG_MAP),](#alt_msg_map)utilice [CHAIN_MSG_MAP_ALT](#chain_msg_map_alt).

> [!NOTE]
> Comience siempre un mapa de mensajes con BEGIN_MSG_MAP. A continuación, puede declarar mapas de mensajes alternativos posteriores con ALT_MSG_MAP. La macro [END_MSG_MAP](#end_msg_map) marca el final del mapa de mensajes. Cada mapa de mensajes debe tener exactamente una instancia de BEGIN_MSG_MAP y END_MSG_MAP.

Para obtener más información sobre el uso de mapas de mensajes en ATL, consulte [Mapas](../../atl/message-maps-atl.md)de mensajes .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#107](../../atl/codesnippet/cpp/message-map-macros-atl_4.h)]

Este ejemplo ilustra lo siguiente:

- Si un procedimiento `CMyClass`de ventana utiliza `OnPaint` el mapa de mensajes predeterminado de `CMyBaseClass`'s y no controla un mensaje, el mensaje se dirige al mapa de mensajes predeterminado de 's para su procesamiento.

- Si un procedimiento de ventana utiliza `CMyClass`el primer mapa `CMyBaseClass`de mensajes alternativo en , todos los mensajes se dirigen al mapa de mensajes predeterminado .

- Si un procedimiento `CMyClass`de ventana utiliza el `OnChar` segundo mapa de mensajes alternativo de 's y `CMyBaseClass`no controla un mensaje, el mensaje se dirige al mapa de mensajes alternativo especificado en . `CMyBaseClass`debe haber declarado este mapa de mensajes con ALT_MSG_MAP(1).

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="chain_msg_map_dynamic"></a><a name="chain_msg_map_dynamic"></a>CHAIN_MSG_MAP_DYNAMIC

Define una entrada en un mapa de mensajes.

```
CHAIN_MSG_MAP_DYNAMIC(dynaChainID)
```

### <a name="parameters"></a>Parámetros

*dynaChainID*<br/>
[en] Identificador único para el mapa de mensajes de un objeto.

### <a name="remarks"></a>Observaciones

CHAIN_MSG_MAP_DYNAMIC dirige los mensajes, en tiempo de ejecución, al mapa de mensajes predeterminado en otro objeto. El objeto y su mapa de mensajes están asociados con *dynaChainID*, que se define a través de [CDynamicChain::SetChainEntry](cdynamicchain-class.md#setchainentry). Debe derivar su `CDynamicChain` clase para poder utilizar CHAIN_MSG_MAP_DYNAMIC. Para obtener un ejemplo, consulte la información general [de CDynamicChain.](../../atl/reference/cdynamicchain-class.md)

> [!NOTE]
> Comience siempre un mapa de mensajes con [BEGIN_MSG_MAP](#begin_msg_map). A continuación, puede declarar mapas de mensajes alternativos posteriores con ALT_MSG_MAP. La macro [END_MSG_MAP](#end_msg_map) marca el final del mapa de mensajes. Cada mapa de mensajes debe tener exactamente una instancia de BEGIN_MSG_MAP y END_MSG_MAP.

Para obtener más información sobre el uso de mapas de mensajes en ATL, consulte [Mapas](../../atl/message-maps-atl.md)de mensajes .

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="chain_msg_map_member"></a><a name="chain_msg_map_member"></a>CHAIN_MSG_MAP_MEMBER

Define una entrada en un mapa de mensajes.

```
CHAIN_MSG_MAP_MEMBER(theChainMember)
```

### <a name="parameters"></a>Parámetros

*theChainMember*<br/>
[en] El nombre del miembro de datos que contiene el mapa de mensajes.

### <a name="remarks"></a>Observaciones

CHAIN_MSG_MAP_MEMBER dirige los mensajes al mapa de mensajes predeterminado de un miembro de datos (declarado con [BEGIN_MSG_MAP](#begin_msg_map)). Para dirigir mensajes al mapa de mensajes alternativo de un miembro de datos (declarado con [ALT_MSG_MAP),](#alt_msg_map)utilice [CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member).

> [!NOTE]
> Comience siempre un mapa de mensajes con BEGIN_MSG_MAP. A continuación, puede declarar mapas de mensajes alternativos posteriores con ALT_MSG_MAP. La macro [END_MSG_MAP](#end_msg_map) marca el final del mapa de mensajes. Cada mapa de mensajes debe tener exactamente una instancia de BEGIN_MSG_MAP y END_MSG_MAP.

Para obtener más información sobre el uso de mapas de mensajes en ATL, consulte [Mapas](../../atl/message-maps-atl.md)de mensajes .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#108](../../atl/codesnippet/cpp/message-map-macros-atl_5.h)]

Este ejemplo ilustra lo siguiente:

- Si un procedimiento `CMyClass`de ventana utiliza `OnPaint` el mapa de mensajes predeterminado de `m_obj`'s y no controla un mensaje, el mensaje se dirige al mapa de mensajes predeterminado de 's para su procesamiento.

- Si un procedimiento de ventana utiliza `CMyClass`el primer mapa `m_obj`de mensajes alternativo en , todos los mensajes se dirigen al mapa de mensajes predeterminado .

- Si un procedimiento `CMyClass`de ventana utiliza el `OnChar` segundo mapa de mensajes alternativo de 's y `m_obj`no controla un mensaje, el mensaje se dirige al mapa de mensajes alternativo especificado de . La `CMyContainedClass` clase debe haber declarado este mapa de mensajes con ALT_MSG_MAP(1).

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="command_code_handler"></a><a name="command_code_handler"></a>COMMAND_CODE_HANDLER

Similar a [COMMAND_HANDLER](#command_handler), pero asigna un [mensaje de WM_COMMAND](/windows/win32/menurc/wm-command) basado únicamente en el código de notificación.

```
COMMAND_CODE_HANDLER(code, func)
```

### <a name="parameters"></a>Parámetros

*Código*<br/>
[en] El código de notificación.

*Func*<br/>
[en] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="command_handler"></a><a name="command_handler"></a>COMMAND_HANDLER

Define una entrada en un mapa de mensajes.

```
COMMAND_HANDLER(id, code, func)
```

### <a name="parameters"></a>Parámetros

*id*<br/>
[en] Identificador del elemento de menú, control o acelerador.

*Código*<br/>
[en] El código de notificación.

*Func*<br/>
[en] El nombre de la función de controlador de mensajes.

### <a name="remarks"></a>Observaciones

COMMAND_HANDLER asigna un mensaje [de WM_COMMAND](/windows/win32/menurc/wm-command) a la función de controlador especificada, en función del código de notificación y el identificador de control. Por ejemplo:

[!code-cpp[NVC_ATL_Windowing#119](../../atl/codesnippet/cpp/message-map-macros-atl_6.h)]

Cualquier función especificada en una macro COMMAND_HANDLER debe definirse de la siguiente manera:

`LRESULT CommandHandler(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled);`

El mapa `bHandled` de mensajes `CommandHandler` se establece en TRUE antes de llamar. Si `CommandHandler` no controla completamente el `bHandled` mensaje, debe establecerse en FALSE para indicar que el mensaje necesita procesamiento adicional.

> [!NOTE]
> Comience siempre un mapa de mensajes con [BEGIN_MSG_MAP](#begin_msg_map). A continuación, puede declarar mapas de mensajes alternativos subsiguientes con [ALT_MSG_MAP](#alt_msg_map). La macro [END_MSG_MAP](#end_msg_map) marca el final del mapa de mensajes. Cada mapa de mensajes debe tener exactamente una instancia de BEGIN_MSG_MAP y END_MSG_MAP.

Además de COMMAND_HANDLER, puede usar [MESSAGE_HANDLER](#message_handler) para asignar un mensaje de WM_COMMAND sin tener en cuenta un identificador o código. En este `MESSAGE_HANDLER(WM_COMMAND, OnHandlerFunction)` caso, dirigirá todos `OnHandlerFunction`los mensajes WM_COMMAND a .

Para obtener más información sobre el uso de mapas de mensajes en ATL, consulte [Mapas](../../atl/message-maps-atl.md)de mensajes .

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="command_id_handler"></a><a name="command_id_handler"></a>COMMAND_ID_HANDLER

De forma similar a [COMMAND_HANDLER](#command_handler), pero asigna un mensaje [de WM_COMMAND](/windows/win32/menurc/wm-command) basado únicamente en el identificador del elemento de menú, control o acelerador.

```
COMMAND_ID_HANDLER(id, func)
```

### <a name="parameters"></a>Parámetros

*id*<br/>
[en] Identificador del elemento de menú, control o acelerador que envía el mensaje.

*Func*<br/>
[en] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="command_range_code_handler"></a><a name="command_range_code_handler"></a>COMMAND_RANGE_CODE_HANDLER

Similar a [COMMAND_RANGE_HANDLER](#command_range_handler), pero asigna [WM_COMMAND](/windows/win32/menurc/wm-command) mensajes con un código de notificación específico de un intervalo de controles a una única función de controlador.

```
COMMAND_RANGE_CODE_HANDLER(idFirst, idLast, code, func)
```

### <a name="parameters"></a>Parámetros

*idFirst*<br/>
[en] Marca el principio de un intervalo contiguo de identificadores de control.

*idLast*<br/>
[en] Marca el final de un intervalo contiguo de identificadores de control.

*Código*<br/>
[en] El código de notificación.

*Func*<br/>
[en] El nombre de la función de controlador de mensajes.

### <a name="remarks"></a>Observaciones

Este intervalo se basa en el identificador del elemento de menú, control o acelerador que envía el mensaje.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="command_range_handler"></a><a name="command_range_handler"></a>COMMAND_RANGE_HANDLER

Similar a [COMMAND_HANDLER](#command_handler), pero asigna [WM_COMMAND](/windows/win32/menurc/wm-command) mensajes de un intervalo de controles a una sola función de controlador.

```
COMMAND_RANGE_HANDLER( idFirst, idLast, func)
```

### <a name="parameters"></a>Parámetros

*idFirst*<br/>
[en] Marca el principio de un intervalo contiguo de identificadores de control.

*idLast*<br/>
[en] Marca el final de un intervalo contiguo de identificadores de control.

*Func*<br/>
[en] El nombre de la función de controlador de mensajes.

### <a name="remarks"></a>Observaciones

Este intervalo se basa en el identificador del elemento de menú, control o acelerador que envía el mensaje.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="declare_empty_msg_map"></a><a name="declare_empty_msg_map"></a>DECLARE_EMPTY_MSG_MAP

Declara un mapa de mensajes vacío.

```
DECLARE_EMPTY_MSG_MAP()
```

### <a name="remarks"></a>Observaciones

DECLARE_EMPTY_MSG_MAP es una macro de conveniencia que llama a las macros [BEGIN_MSG_MAP](#begin_msg_map) y [END_MSG_MAP](#end_msg_map) para crear un mapa de mensajes vacío:

[!code-cpp[NVC_ATL_Windowing#122](../../atl/codesnippet/cpp/message-map-macros-atl_7.h)]

## <a name="default_reflection_handler"></a><a name="default_reflection_handler"></a>DEFAULT_REFLECTION_HANDLER

Proporciona un controlador predeterminado para la ventana secundaria (control) que recibirá mensajes reflejados; el controlador pasará correctamente los `DefWindowProc`mensajes no controlados a .

```
DEFAULT_REFLECTION_HANDLER()
```

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="end_msg_map"></a><a name="end_msg_map"></a>END_MSG_MAP

Marca el final de un mapa de mensajes.

```
END_MSG_MAP()
```

### <a name="remarks"></a>Observaciones

Utilice siempre la macro [BEGIN_MSG_MAP](#begin_msg_map) para marcar el principio de un mapa de mensajes. Utilice [ALT_MSG_MAP](#alt_msg_map) para declarar mapas de mensajes alternativos posteriores.

Tenga en cuenta que siempre hay exactamente una instancia de BEGIN_MSG_MAP y END_MSG_MAP.

Para obtener más información sobre el uso de mapas de mensajes en ATL, consulte [Mapas](../../atl/message-maps-atl.md)de mensajes .

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el mapa de mensajes predeterminado y un mapa de mensajes alternativo, cada uno de los cuales contiene una función de controlador:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

En el ejemplo siguiente se muestran dos mapas de mensajes alternativos. El mapa de mensajes predeterminado está vacío.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="forward_notifications"></a><a name="forward_notifications"></a>FORWARD_NOTIFICATIONS

Reenvía los mensajes de notificación a la ventana primaria.

```
FORWARD_NOTIFICATIONS()
```

### <a name="remarks"></a>Observaciones

Especifique esta macro como parte del mapa de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="message_handler"></a><a name="message_handler"></a>MESSAGE_HANDLER

Define una entrada en un mapa de mensajes.

```
MESSAGE_HANDLER( msg, func )
```

### <a name="parameters"></a>Parámetros

*Msg*<br/>
[en] El mensaje de Windows.

*Func*<br/>
[en] El nombre de la función de controlador de mensajes.

### <a name="remarks"></a>Observaciones

MESSAGE_HANDLER asigna un mensaje de Windows a la función de controlador especificada.

Cualquier función especificada en una macro de MESSAGE_HANDLER debe definirse de la siguiente manera:

`LRESULT MessageHandler(UINT uMsg, WPARAM wParam, LPARAM lParam, BOOL& bHandled);`

El mapa `bHandled` de mensajes `MessageHandler` se establece en TRUE antes de llamar. Si `MessageHandler` no controla completamente el `bHandled` mensaje, debe establecerse en FALSE para indicar que el mensaje necesita procesamiento adicional.

> [!NOTE]
> Comience siempre un mapa de mensajes con [BEGIN_MSG_MAP](#begin_msg_map). A continuación, puede declarar mapas de mensajes alternativos subsiguientes con [ALT_MSG_MAP](#alt_msg_map). La macro [END_MSG_MAP](#end_msg_map) marca el final del mapa de mensajes. Cada mapa de mensajes debe tener exactamente una instancia de BEGIN_MSG_MAP y END_MSG_MAP.

Además de MESSAGE_HANDLER, puede utilizar [COMMAND_HANDLER](#command_handler) y [NOTIFY_HANDLER](#notify_handler) para asignar [mensajes de WM_COMMAND](/windows/win32/menurc/wm-command) y [WM_NOTIFY,](/windows/win32/controls/wm-notify) respectivamente.

Para obtener más información sobre el uso de mapas de mensajes en ATL, consulte [Mapas](../../atl/message-maps-atl.md)de mensajes .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#129](../../atl/codesnippet/cpp/message-map-macros-atl_8.h)]

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="message_range_handler"></a><a name="message_range_handler"></a>MESSAGE_RANGE_HANDLER

Similar a [MESSAGE_HANDLER](#message_handler), pero asigna un intervalo de mensajes de Windows a una única función de controlador.

```
MESSAGE_RANGE_HANDLER( msgFirst, msgLast, func )
```

### <a name="parameters"></a>Parámetros

*msgFirst*<br/>
[en] Marca el principio de un rango contiguo de mensajes.

*msgLast*<br/>
[en] Marca el final de un intervalo contiguo de mensajes.

*Func*<br/>
[en] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="notify_code_handler"></a><a name="notify_code_handler"></a>NOTIFY_CODE_HANDLER

Similar a [NOTIFY_HANDLER](#notify_handler), pero asigna un mensaje [de WM_NOTIFY](/windows/win32/controls/wm-notify) basado únicamente en el código de notificación.

```
NOTIFY_CODE_HANDLER(cd, func)
```

### <a name="parameters"></a>Parámetros

*Cd*<br/>
[en] El código de notificación.

*Func*<br/>
[en] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="notify_handler"></a><a name="notify_handler"></a>NOTIFY_HANDLER

Define una entrada en un mapa de mensajes.

```
NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>Parámetros

*id*<br/>
[en] Identificador del control que envía el mensaje.

*Cd*<br/>
[en] El código de notificación.

*Func*<br/>
[en] El nombre de la función de controlador de mensajes.

### <a name="remarks"></a>Observaciones

NOTIFY_HANDLER asigna un mensaje [de WM_NOTIFY](/windows/win32/controls/wm-notify) a la función de controlador especificada, en función del código de notificación y el identificador de control.

Cualquier función especificada en una macro NOTIFY_HANDLER debe definirse de la siguiente manera:

`LRESULT NotifyHandler(int idCtrl, LPNMHDR pnmh, BOOL& bHandled);`

El mapa `bHandled` de mensajes `NotifyHandler` se establece en TRUE antes de llamar. Si `NotifyHandler` no controla completamente el `bHandled` mensaje, debe establecerse en FALSE para indicar que el mensaje necesita procesamiento adicional.

> [!NOTE]
> Comience siempre un mapa de mensajes con [BEGIN_MSG_MAP](#begin_msg_map). A continuación, puede declarar mapas de mensajes alternativos subsiguientes con [ALT_MSG_MAP](#alt_msg_map). La macro [END_MSG_MAP](#end_msg_map) marca el final del mapa de mensajes. Cada mapa de mensajes debe tener exactamente una instancia de BEGIN_MSG_MAP y END_MSG_MAP.

Además de NOTIFY_HANDLER, puede usar [MESSAGE_HANDLER](#message_handler) para asignar un mensaje de WM_NOTIFY sin tener en cuenta un identificador o código. En este `MESSAGE_HANDLER(WM_NOTIFY, OnHandlerFunction)` caso, dirigirá todos `OnHandlerFunction`los mensajes WM_NOTIFY a .

Para obtener más información sobre el uso de mapas de mensajes en ATL, consulte [Mapas](../../atl/message-maps-atl.md)de mensajes .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#130](../../atl/codesnippet/cpp/message-map-macros-atl_9.h)]

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="notify_id_handler"></a><a name="notify_id_handler"></a>NOTIFY_ID_HANDLER

Similar a [NOTIFY_HANDLER](#notify_handler), pero asigna un [mensaje de WM_NOTIFY](/windows/win32/controls/wm-notify) basado únicamente en el identificador de control.

```
NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parámetros

*id*<br/>
[en] Identificador del control que envía el mensaje.

*Func*<br/>
[en] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="notify_range_code_handler"></a><a name="notify_range_code_handler"></a>NOTIFY_RANGE_CODE_HANDLER

Similar a [NOTIFY_RANGE_HANDLER](#notify_range_handler), pero asigna [WM_NOTIFY](/windows/win32/controls/wm-notify) mensajes con un código de notificación específico de un intervalo de controles a una única función de controlador.

```
NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>Parámetros

*idFirst*<br/>
[en] Marca el principio de un intervalo contiguo de identificadores de control.

*idLast*<br/>
[en] Marca el final de un intervalo contiguo de identificadores de control.

*Cd*<br/>
[en] El código de notificación.

*Func*<br/>
[en] El nombre de la función de controlador de mensajes.

### <a name="remarks"></a>Observaciones

Este intervalo se basa en el identificador del control que envía el mensaje.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="notify_range_handler"></a><a name="notify_range_handler"></a>NOTIFY_RANGE_HANDLER

Similar a [NOTIFY_HANDLER](#notify_handler), pero asigna [WM_NOTIFY](/windows/win32/controls/wm-notify) mensajes de un intervalo de controles a una sola función de controlador.

```
NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parámetros

*idFirst*<br/>
[en] Marca el principio de un intervalo contiguo de identificadores de control.

*idLast*<br/>
[en] Marca el final de un intervalo contiguo de identificadores de control.

*Func*<br/>
[en] El nombre de la función de controlador de mensajes.

### <a name="remarks"></a>Observaciones

Este intervalo se basa en el identificador del control que envía el mensaje.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="reflect_notifications"></a><a name="reflect_notifications"></a>REFLECT_NOTIFICATIONS

Refleja los mensajes de notificación a la ventana secundaria (control) que los envió.

```
REFLECT_NOTIFICATIONS()
```

### <a name="remarks"></a>Observaciones

Especifique esta macro como parte del mapa de mensajes de la ventana primaria.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="reflected_command_code_handler"></a><a name="reflected_command_code_handler"></a>REFLECTED_COMMAND_CODE_HANDLER

Similar a [COMMAND_CODE_HANDLER](#command_code_handler), pero los comandos de mapas se reflejan desde la ventana primaria.

```
REFLECTED_COMMAND_CODE_HANDLER( code, func )
```

### <a name="parameters"></a>Parámetros

*Código*<br/>
[en] El código de notificación.

*Func*<br/>
[en] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="reflected_command_handler"></a><a name="reflected_command_handler"></a>REFLECTED_COMMAND_HANDLER

Similar a [COMMAND_HANDLER](#command_handler), pero los comandos de mapas se reflejan desde la ventana primaria.

```
REFLECTED_COMMAND_HANDLER( id, code, func )
```

### <a name="parameters"></a>Parámetros

*id*<br/>
[en] Identificador del elemento de menú, control o acelerador.

*Código*<br/>
[en] El código de notificación.

*Func*<br/>
[en] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="reflected_command_id_handler"></a><a name="reflected_command_id_handler"></a>REFLECTED_COMMAND_ID_HANDLER

Similar a [COMMAND_ID_HANDLER](#command_id_handler), pero los comandos de mapas se reflejan desde la ventana primaria.

```
REFLECTED_COMMAND_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parámetros

*id*<br/>
[en] Identificador del elemento de menú, control o acelerador.

*Func*<br/>
[en] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="reflected_command_range_code_handler"></a><a name="reflected_command_range_code_handler"></a>REFLECTED_COMMAND_RANGE_CODE_HANDLER

Similar a [COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler), pero los comandos de mapas se reflejan desde la ventana primaria.

```
REFLECTED_COMMAND_RANGE_CODE_HANDLER( idFirst, idLast, code, func )
```

### <a name="parameters"></a>Parámetros

*idFirst*<br/>
[en] Marca el principio de un intervalo contiguo de identificadores de control.

*idLast*<br/>
[en] Marca el final de un intervalo contiguo de identificadores de control.

*Código*<br/>
[en] El código de notificación.

*Func*<br/>
[en] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="reflected_command_range_handler"></a><a name="reflected_command_range_handler"></a>REFLECTED_COMMAND_RANGE_HANDLER

Similar a [COMMAND_RANGE_HANDLER](#command_range_handler), pero los comandos de mapas se reflejan desde la ventana primaria.

```
REFLECTED_COMMAND_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parámetros

*idFirst*<br/>
[en] Marca el principio de un intervalo contiguo de identificadores de control.

*idLast*<br/>
[en] Marca el final de un intervalo contiguo de identificadores de control.

*Func*<br/>
[en] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="reflected_notify_code_handler"></a><a name="reflected_notify_code_handler"></a>REFLECTED_NOTIFY_CODE_HANDLER

Similar a [NOTIFY_CODE_HANDLER](#notify_code_handler), pero asigna notificaciones reflejadas desde la ventana primaria.

```
REFLECTED_NOTIFY_CODE_HANDLER_EX( cd, func )
```

### <a name="parameters"></a>Parámetros

*Cd*<br/>
[en] El código de notificación.

*Func*<br/>
[en] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="reflected_notify_handler"></a><a name="reflected_notify_handler"></a>REFLECTED_NOTIFY_HANDLER

Similar a [NOTIFY_HANDLER](#notify_handler), pero asigna notificaciones reflejadas desde la ventana primaria.

```
REFLECTED_NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>Parámetros

*id*<br/>
[en] Identificador del elemento de menú, control o acelerador.

*Cd*<br/>
[en] El código de notificación.

*Func*<br/>
[en] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="reflected_notify_id_handler"></a><a name="reflected_notify_id_handler"></a>REFLECTED_NOTIFY_ID_HANDLER

Similar a [NOTIFY_ID_HANDLER](#notify_id_handler), pero asigna notificaciones reflejadas desde la ventana primaria.

```
REFLECTED_NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parámetros

*id*<br/>
[en] Identificador del elemento de menú, control o acelerador.

*Func*<br/>
[en] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="reflected_notify_range_code_handler"></a><a name="reflected_notify_range_code_handler"></a>REFLECTED_NOTIFY_RANGE_CODE_HANDLER

Similar a [NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler), pero asigna notificaciones reflejadas desde la ventana primaria.

```
REFLECTED_NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>Parámetros

*idFirst*<br/>
[en] Marca el principio de un intervalo contiguo de identificadores de control.

*idLast*<br/>
[en] Marca el final de un intervalo contiguo de identificadores de control.

*Cd*<br/>
[en] El código de notificación.

*Func*<br/>
[en] El nombre de la función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="reflected_notify_range_handler"></a><a name="reflected_notify_range_handler"></a>REFLECTED_NOTIFY_RANGE_HANDLER

Similar a [NOTIFY_RANGE_HANDLER](#notify_range_handler), pero asigna notificaciones reflejadas desde la ventana primaria.

```
REFLECTED_NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parámetros

*idFirst*<br/>
[en] Marca el principio de un intervalo contiguo de identificadores de control.

*idLast*<br/>
[en] Marca el final de un intervalo contiguo de identificadores de control.

*Func*<br/>
[en] El nombre de la función de controlador de mensajes.

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)
