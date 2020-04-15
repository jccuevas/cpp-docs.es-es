---
title: Macros de control compuesto
ms.date: 05/06/2019
f1_keywords:
- atlcom/ATL::BEGIN_SINK_MAP
- atlcom/ATL::END_SINK_MAP
- atlcom/ATL::SINK_ENTRY
helpviewer_keywords:
- composite controls, macros
ms.assetid: 17f2dd5e-07e6-4aa6-b965-7a361c78c45e
ms.openlocfilehash: 67ad18c07a92cfecca44667908a8488e8c2da234
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331513"
---
# <a name="composite-control-macros"></a>Macros de control compuesto

Estas macros definen asignaciones y entradas de receptores de eventos.

|||
|-|-|
|[BEGIN_SINK_MAP](#begin_sink_map)|Marca el principio del mapa del receptor de eventos para el control compuesto.|
|[END_SINK_MAP](#end_sink_map)|Marca el final del mapa del receptor de eventos para el control compuesto.|
|[SINK_ENTRY](#sink_entry)|Entrada al mapa del receptor de eventos.|
|[SINK_ENTRY_EX](#sink_entry_ex)|Entrada al mapa del receptor de eventos con un parámetro adicional.|
|[SINK_ENTRY_EX_P](#sink_entry_ex)| (Visual Studio 2017) Similar a SINK_ENTRY_EX excepto que toma un puntero a iid.|
|[SINK_ENTRY_INFO](#sink_entry_info)|Entrada al mapa del receptor de eventos con información de tipo proporcionada manualmente para su uso con [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md).|
|[SINK_ENTRY_INFO_P](#sink_entry_info)| (Visual Studio 2017) Similar a SINK_ENTRY_INFO excepto que toma un puntero a iid.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="begin_sink_map"></a><a name="begin_sink_map"></a>BEGIN_SINK_MAP

Declara el principio del mapa del receptor de eventos para el control compuesto.

```
BEGIN_SINK_MAP(_class)
```

### <a name="parameters"></a>Parámetros

*_class*<br/>
[en] Especifica el control.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Observaciones

La implementación de CE ATL de receptores de eventos ActiveX solo admite valores devueltos de tipo HRESULT o void de los métodos del controlador de eventos; cualquier otro valor devuelto no es compatible y su comportamiento es indefinido.

## <a name="end_sink_map"></a><a name="end_sink_map"></a>END_SINK_MAP

Declara el final del mapa del receptor de eventos para el control compuesto.

```
END_SINK_MAP()
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Observaciones

La implementación de CE ATL de receptores de eventos ActiveX solo admite valores devueltos de tipo HRESULT o void de los métodos del controlador de eventos; cualquier otro valor devuelto no es compatible y su comportamiento es indefinido.

## <a name="sink_entry"></a><a name="sink_entry"></a>SINK_ENTRY

Declara la función de controlador (*fn*) para el evento especificado (*dispid*), del control identificado por *id*.

```
SINK_ENTRY( id, dispid, fn )
```

### <a name="parameters"></a>Parámetros

*id*<br/>
[en] Identifica el control.

*dispid*<br/>
[en] Identifica el evento especificado.

*fn*<br/>
[en] Nombre de la función de controlador de eventos. Esta función `_stdcall` debe utilizar la convención de llamada y tener la firma de estilo dispinterface adecuada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Observaciones

La implementación de CE ATL de receptores de eventos ActiveX solo admite valores devueltos de tipo HRESULT o void de los métodos del controlador de eventos; cualquier otro valor devuelto no es compatible y su comportamiento es indefinido.

## <a name="sink_entry_ex-and-sink_entry_ex_p"></a><a name="sink_entry_ex"></a>SINK_ENTRY_EX y SINK_ENTRY_EX_P

Declara la función de controlador (*fn*) para el evento especificado (*dispid*), de la interfaz de envío (*iid*), para el control identificado por *id*.

```
SINK_ENTRY_EX( id, iid, dispid, fn )
SINK_ENTRY_EX_P( id, piid, dispid, fn ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parámetros

*id*<br/>
[en] Identifica el control.

*Iid*<br/>
[en] Identifica la interfaz de envío.

*piid*<br/>
[en] Puntero a la interfaz de envío.

*dispid*<br/>
[en] Identifica el evento especificado.

*fn*<br/>
[en] Nombre de la función de controlador de eventos. Esta función `_stdcall` debe utilizar la convención de llamada y tener la firma de estilo dispinterface adecuada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#136](../../atl/codesnippet/cpp/composite-control-macros_2.h)]

### <a name="remarks"></a>Observaciones

La implementación de CE ATL de receptores de eventos ActiveX solo admite valores devueltos de tipo HRESULT o void de los métodos del controlador de eventos; cualquier otro valor devuelto no es compatible y su comportamiento es indefinido.

## <a name="sink_entry_info-and-sink_entry_info_p"></a><a name="sink_entry_info"></a>SINK_ENTRY_INFO y SINK_ENTRY_INFO_P

Utilice la macro SINK_ENTRY_INFO dentro de un mapa de receptor es necesario para proporcionar la información necesaria para [enrutar](../../atl/reference/idispeventsimpleimpl-class.md) eventos a la función de controlador relevante.

```
SINK_ENTRY_INFO( id, iid, dispid, fn, info )
SINK_ENTRY_INFO_P( id, piid, dispid, fn, info ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parámetros

*id*<br/>
[en] Entero sin signo que identifica el origen del evento. Este valor debe coincidir con el parámetro de plantilla *nID* utilizado en la clase base [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) relacionada.

*Iid*<br/>
[en] IID que identifica la interfaz de envío.

*piid*<br/>
[en] Puntero a IID que identifica la interfaz de envío.

*dispid*<br/>
[en] DISPID identificando el evento especificado.

*fn*<br/>
[en] Nombre de la función de controlador de eventos. Esta función `_stdcall` debe utilizar la convención de llamada y tener la firma de estilo dispinterface adecuada.

*info*<br/>
[en] Escriba información para la función de controlador de eventos. Esta información de tipo se proporciona en `_ATL_FUNC_INFO` forma de puntero a una estructura. CC_CDECL es la única opción admitida en Windows CE `_ATL_FUNC_INFO` para el campo CALLCONV de la estructura. Cualquier otro valor no es compatible, por lo tanto, su comportamiento no está definido.

### <a name="remarks"></a>Observaciones

Los primeros cuatro parámetros de macro son los mismos que los de la macro [SINK_ENTRY_EX.](#sink_entry_ex) El parámetro final proporciona información de tipo para el evento. La implementación de CE ATL de receptores de eventos ActiveX solo admite valores devueltos de tipo HRESULT o void de los métodos del controlador de eventos; cualquier otro valor devuelto no es compatible y su comportamiento es indefinido.

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)<br/>
[Funciones globales de control compuesto](../../atl/reference/composite-control-global-functions.md)
