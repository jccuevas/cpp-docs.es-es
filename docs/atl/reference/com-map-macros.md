---
title: Macros de mapas COM
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
ms.openlocfilehash: 191a0ba0aeda6ad18cdac7ba14f7ab5f3b2282f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326600"
---
# <a name="com-map-macros"></a>Macros de mapas COM

Estas macros definen mapas de interfaz COM.

|||
|-|-|
|[BEGIN_COM_MAP](#begin_com_map)|Marca el principio de las entradas de mapa de interfaz COM.|
|[END_COM_MAP](#end_com_map)|Marca el final de las entradas de mapa de interfaz COM.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="begin_com_map"></a><a name="begin_com_map"></a>BEGIN_COM_MAP

La asignación COM es el mecanismo que expone interfaces en un objeto a un cliente a través `QueryInterface`de .

```
BEGIN_COM_MAP(x)
```

### <a name="parameters"></a>Parámetros

*X*<br/>
[en] El nombre del objeto de clase en el que está exponiendo interfaces.

### <a name="remarks"></a>Observaciones

[CComObjectRootEx::InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) solo devuelve punteros para interfaces en el mapa COM. Inicie el mapa de interfaz con la macro BEGIN_COM_MAP, añada entradas para cada una de sus interfaces con la macro [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) o una de sus variantes y complete el mapa con la macro [END_COM_MAP.](#end_com_map)

### <a name="example"></a>Ejemplo

Del ejemplo ATL [BEEPER:](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

## <a name="end_com_map"></a><a name="end_com_map"></a>END_COM_MAP

Finaliza la definición del mapa de interfaz COM.

```
END_COM_MAP()
```

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)<br/>
[Funciones globales del mapa COM](../../atl/reference/com-map-global-functions.md)
