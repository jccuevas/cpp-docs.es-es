---
title: Macros de Control compuesto
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_SINK_MAP
- atlcom/ATL::END_SINK_MAP
- atlcom/ATL::SINK_ENTRY
helpviewer_keywords:
- composite controls, macros
ms.assetid: 17f2dd5e-07e6-4aa6-b965-7a361c78c45e
ms.openlocfilehash: 2c6d3e350755ef4a0cf4a84561e34619ab3974be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62278324"
---
# <a name="composite-control-macros"></a>Macros de Control compuesto

Estas macros definen los mapas de receptor de eventos y entradas.

|||
|-|-|
|[BEGIN_SINK_MAP](#begin_sink_map)|Marca el principio de la asignación de receptor de eventos para el control compuesto.|
|[END_SINK_MAP](#end_sink_map)|Marca el final de la asignación de receptor de eventos para el control compuesto.|
|[SINK_ENTRY](#sink_entry)|Entrada en el mapa de receptores de eventos.|
|[SINK_ENTRY_EX](#sink_entry_ex)|Entrada en el mapa de receptores de eventos con un parámetro adicional.|
|[SINK_ENTRY_EX_P](#sink_entry_ex)| (Visual Studio 2017) Similar a SINK_ENTRY_EX, salvo que toma un puntero a iid.|
|[SINK_ENTRY_INFO](#sink_entry_info)|Entrada a la asignación de receptor de eventos con información de tipo proporcionado manualmente para su uso con [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md).|
|[SINK_ENTRY_INFO_P](#sink_entry_info)| (Visual Studio 2017) Es similar a la macro SINK_ENTRY_INFO salvo que toma un puntero a iid.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="begin_sink_map"></a>  BEGIN_SINK_MAP

Declara el principio de la asignación de receptor de eventos para el control compuesto.

```
BEGIN_SINK_MAP(_class)
```

### <a name="parameters"></a>Parámetros

*_class*<br/>
[in] Especifica el control.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Comentarios

Implementación de ATL de CE de ActiveX eventos receptores solo admite valores devueltos de tipo HRESULT o void desde los métodos de controlador de eventos; no se admite ningún otro tipo de valor devuelto y su comportamiento es indefinido.

##  <a name="end_sink_map"></a>  END_SINK_MAP

Declara el final de la asignación de receptor de eventos para el control compuesto.

```
END_SINK_MAP()
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Comentarios

Implementación de ATL de CE de ActiveX eventos receptores solo admite valores devueltos de tipo HRESULT o void desde los métodos de controlador de eventos; no se admite ningún otro tipo de valor devuelto y su comportamiento es indefinido.

##  <a name="sink_entry"></a>  SINK_ENTRY

Declara la función de controlador (*fn*) para el evento especificado (*dispid*), del control identificado por *id*.

```
SINK_ENTRY( id, dispid, fn )
```

### <a name="parameters"></a>Parámetros

*identificador*<br/>
[in] Identifica el control.

*dispid*<br/>
[in] Identifica el evento especificado.

*fn*<br/>
[in] Nombre de la función de controlador de eventos. Esta función debe usar el `_stdcall` convención de llamada y tiene la firma de estilo de interfaz dispinterface adecuado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Comentarios

Implementación de ATL de CE de ActiveX eventos receptores solo admite valores devueltos de tipo HRESULT o void desde los métodos de controlador de eventos; no se admite ningún otro tipo de valor devuelto y su comportamiento es indefinido.

##  <a name="sink_entry_ex"></a>  SINK_ENTRY_EX y SINK_ENTRY_EX_P

Declara la función de controlador (*fn*) para el evento especificado (*dispid*), de la interfaz de envío (*iid*), para el control identificado por *id*.

```
SINK_ENTRY_EX( id, iid, dispid, fn )
SINK_ENTRY_EX_P( id, piid, dispid, fn ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parámetros

*identificador*<br/>
[in] Identifica el control.

*iid*<br/>
[in] Identifica la interfaz de envío.

*piid*<br/>
[in] Puntero a la interfaz de envío.

*dispid*<br/>
[in] Identifica el evento especificado.

*fn*<br/>
[in] Nombre de la función de controlador de eventos. Esta función debe usar el `_stdcall` convención de llamada y tiene la firma de estilo de interfaz dispinterface adecuado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#136](../../atl/codesnippet/cpp/composite-control-macros_2.h)]

### <a name="remarks"></a>Comentarios

Implementación de ATL de CE de ActiveX eventos receptores solo admite valores devueltos de tipo HRESULT o void desde los métodos de controlador de eventos; no se admite ningún otro tipo de valor devuelto y su comportamiento es indefinido.

##  <a name="sink_entry_info"></a>  Macro SINK_ENTRY_INFO y SINK_ENTRY_INFO_P

Utilice la macro de macro SINK_ENTRY_INFO dentro de un mapa de receptores de eventos para proporcionar la información necesaria para [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) enrutar eventos a la función de controlador correspondiente.

```
SINK_ENTRY_INFO( id, iid, dispid, fn, info )
SINK_ENTRY_INFO_P( id, piid, dispid, fn, info ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parámetros

*identificador*<br/>
[in] Entero sin signo que identifica el origen del evento. Este valor debe coincidir con el *nID* parámetro de plantilla utilizado en el que se relaciona [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) clase base.

*iid*<br/>
[in] IID que identifica la interfaz de envío.

*piid*<br/>
[in] Puntero a IID que identifica la interfaz de envío.

*dispid*<br/>
[in] Identificador de envío que identifica el evento especificado.

*fn*<br/>
[in] Nombre de la función de controlador de eventos. Esta función debe usar el `_stdcall` convención de llamada y tiene la firma de estilo de interfaz dispinterface adecuado.

*info*<br/>
[in] Escriba la información de la función de controlador de eventos. Esta información de tipo se proporciona en forma de un puntero a un `_ATL_FUNC_INFO` estructura. CC_CDECL es la única opción admitida en Windows CE para el campo CALLCONV del `_ATL_FUNC_INFO` estructura. No se admite cualquier otro valor, por tanto, su comportamiento sin definir.

### <a name="remarks"></a>Comentarios

Los parámetros de cuatro primeros macro son las mismas que para el [SINK_ENTRY_EX](#sink_entry_ex) macro. El parámetro final proporciona la información de tipo para el evento. Implementación de ATL de CE de ActiveX eventos receptores solo admite valores devueltos de tipo HRESULT o void desde los métodos de controlador de eventos; no se admite ningún otro tipo de valor devuelto y su comportamiento es indefinido.

## <a name="see-also"></a>Vea también

[Macros](../../atl/reference/atl-macros.md)<br/>
[Funciones globales de control compuesto](../../atl/reference/composite-control-global-functions.md)
