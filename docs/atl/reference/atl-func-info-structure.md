---
title: Estructura de _ATL_FUNC_INFO
ms.date: 11/04/2016
f1_keywords:
- _ATL_FUNC_INFO
- ATL::_ATL_FUNC_INFO
- ATL._ATL_FUNC_INFO
helpviewer_keywords:
- _ATL_FUNC_INFO structure
- ATL_FUNC_INFO structure
ms.assetid: 441ebe2c-f971-47de-9f52-a258e8d6f88e
ms.openlocfilehash: b1c740cf1a1ed344dbceb028bd1f39a87fc09363
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168597"
---
# <a name="_atl_func_info-structure"></a>Estructura de _ATL_FUNC_INFO

Contiene información de tipos que se usa para describir un método o una propiedad en una interfaz dispinterface.

## <a name="syntax"></a>Sintaxis

```cpp
struct _ATL_FUNC_INFO {
    CALLCONV cc;
    VARTYPE vtReturn;
    SHORT nParams;
    VARTYPE pVarTypes[_ATL_MAX_VARTYPES];
};
```

## <a name="members"></a>Members

`cc`<br/>
Convención de llamada. Al utilizar esta estructura con la clase [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) , este miembro debe ser CC_STDCALL. `CC_CDECL`es la única opción admitida en Windows CE para `CALLCONV` el campo de `_ATL_FUNC_INFO` la estructura. No se admite ningún otro valor, por lo que su comportamiento no está definido.

`vtReturn`<br/>
Tipo Variant del valor devuelto de la función.

`nParams`<br/>
El número de parámetros de función.

`pVarTypes`<br/>
Matriz de tipos Variant de los parámetros de la función.

## <a name="remarks"></a>Observaciones

Internamente, ATL usa esta estructura para almacenar la información obtenida de una biblioteca de tipos. Es posible que tenga que manipular esta estructura directamente si proporciona información de tipo para un controlador de eventos que se usa con la clase [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) y [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) macro.

## <a name="example"></a>Ejemplo

Dado un método dispinterface definido en IDL:

[!code-cpp[NVC_ATL_Windowing#139](../../atl/codesnippet/cpp/atl-func-info-structure_1.idl)]

definiría una `_ATL_FUNC_INFO` estructura:

[!code-cpp[NVC_ATL_Windowing#140](../../atl/codesnippet/cpp/atl-func-info-structure_2.h)]

## <a name="requirements"></a>Requisitos

Encabezado: atlcom.h

## <a name="see-also"></a>Consulte también

[Clases y estructuras](../../atl/reference/atl-classes.md)<br/>
[IDispEventSimpleImpl (clase)](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)
