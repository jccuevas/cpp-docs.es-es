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
ms.openlocfilehash: 685bf55910d4746463de30b17b71aa6d246db199
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78857124"
---
# <a name="composite-control-macros"></a>Macros de control compuesto

Estas macros definen las asignaciones y las entradas del receptor de eventos.

|||
|-|-|
|[BEGIN_SINK_MAP](#begin_sink_map)|Marca el principio de la asignación del receptor de eventos para el control compuesto.|
|[END_SINK_MAP](#end_sink_map)|Marca el final de la asignación del receptor de eventos para el control compuesto.|
|[SINK_ENTRY](#sink_entry)|Entrada al mapa del receptor de eventos.|
|[SINK_ENTRY_EX](#sink_entry_ex)|Entrada al mapa del receptor de eventos con un parámetro adicional.|
|[SINK_ENTRY_EX_P](#sink_entry_ex)| (Visual Studio 2017) Similar a SINK_ENTRY_EX, salvo que toma un puntero a IID.|
|[SINK_ENTRY_INFO](#sink_entry_info)|Entrada al mapa del receptor de eventos con información de tipos proporcionada manualmente para su uso con [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md).|
|[SINK_ENTRY_INFO_P](#sink_entry_info)| (Visual Studio 2017) Similar a SINK_ENTRY_INFO, salvo que toma un puntero a IID.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="begin_sink_map"></a>BEGIN_SINK_MAP

Declara el principio de la asignación del receptor de eventos para el control compuesto.

```
BEGIN_SINK_MAP(_class)
```

### <a name="parameters"></a>Parámetros

*_class*<br/>
de Especifica el control.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Observaciones

La implementación de ATL ATL de receptores de eventos ActiveX solo admite valores devueltos de tipo HRESULT o void de los métodos de control de eventos; no se admite ningún otro valor devuelto y su comportamiento es indefinido.

##  <a name="end_sink_map"></a>END_SINK_MAP

Declara el final de la asignación del receptor de eventos para el control compuesto.

```
END_SINK_MAP()
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Observaciones

La implementación de ATL ATL de receptores de eventos ActiveX solo admite valores devueltos de tipo HRESULT o void de los métodos de control de eventos; no se admite ningún otro valor devuelto y su comportamiento es indefinido.

##  <a name="sink_entry"></a>SINK_ENTRY

Declara la función de controlador (*FN*) para el evento especificado (*DISPID*), del control identificado mediante el *identificador*.

```
SINK_ENTRY( id, dispid, fn )
```

### <a name="parameters"></a>Parámetros

*id*<br/>
de Identifica el control.

*DISPID*<br/>
de Identifica el evento especificado.

*FN*<br/>
de Nombre de la función de controlador de eventos. Esta función debe usar la Convención de llamada de `_stdcall` y tener la firma de estilo dispinterface adecuada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Observaciones

La implementación de ATL ATL de receptores de eventos ActiveX solo admite valores devueltos de tipo HRESULT o void de los métodos de control de eventos; no se admite ningún otro valor devuelto y su comportamiento es indefinido.

##  <a name="sink_entry_ex"></a>SINK_ENTRY_EX y SINK_ENTRY_EX_P

Declara la función de controlador (*FN*) para el evento especificado (*DISPID*) de la interfaz de envío (*IID*), para el control identificado mediante el *identificador*.

```
SINK_ENTRY_EX( id, iid, dispid, fn )
SINK_ENTRY_EX_P( id, piid, dispid, fn ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parámetros

*id*<br/>
de Identifica el control.

*suscripto*<br/>
de Identifica la interfaz de envío.

*piid*<br/>
de Puntero a la interfaz de envío.

*DISPID*<br/>
de Identifica el evento especificado.

*FN*<br/>
de Nombre de la función de controlador de eventos. Esta función debe usar la Convención de llamada de `_stdcall` y tener la firma de estilo dispinterface adecuada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#136](../../atl/codesnippet/cpp/composite-control-macros_2.h)]

### <a name="remarks"></a>Observaciones

La implementación de ATL ATL de receptores de eventos ActiveX solo admite valores devueltos de tipo HRESULT o void de los métodos de control de eventos; no se admite ningún otro valor devuelto y su comportamiento es indefinido.

##  <a name="sink_entry_info"></a>SINK_ENTRY_INFO y SINK_ENTRY_INFO_P

Use la macro SINK_ENTRY_INFO dentro de una asignación de receptor de eventos para proporcionar la información necesaria para que [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) dirija los eventos a la función de controlador pertinente.

```
SINK_ENTRY_INFO( id, iid, dispid, fn, info )
SINK_ENTRY_INFO_P( id, piid, dispid, fn, info ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parámetros

*id*<br/>
de Entero sin signo que identifica el origen del evento. Este valor debe coincidir con el parámetro de plantilla *nID* usado en la clase base [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) relacionada.

*suscripto*<br/>
de IID que identifica la interfaz de envío.

*piid*<br/>
de Puntero a IID que identifica la interfaz de envío.

*DISPID*<br/>
de DISPID que identifica el evento especificado.

*FN*<br/>
de Nombre de la función de controlador de eventos. Esta función debe usar la Convención de llamada de `_stdcall` y tener la firma de estilo dispinterface adecuada.

*info*<br/>
de Información de tipo para la función de controlador de eventos. Esta información de tipo se proporciona en forma de puntero a una estructura de `_ATL_FUNC_INFO`. CC_CDECL es la única opción admitida en Windows CE para el campo CALLCONV de la estructura `_ATL_FUNC_INFO`. No se admite ningún otro valor, por lo que su comportamiento no está definido.

### <a name="remarks"></a>Observaciones

Los cuatro primeros parámetros de macro son los mismos que los de la macro [SINK_ENTRY_EX](#sink_entry_ex) . El parámetro final proporciona información de tipo para el evento. La implementación de ATL ATL de receptores de eventos ActiveX solo admite valores devueltos de tipo HRESULT o void de los métodos de control de eventos; no se admite ningún otro valor devuelto y su comportamiento es indefinido.

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)<br/>
[Funciones globales de control compuesto](../../atl/reference/composite-control-global-functions.md)
