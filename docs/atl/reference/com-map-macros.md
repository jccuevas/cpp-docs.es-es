---
title: Macros de mapa COM
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
ms.openlocfilehash: 3159a53b5a500aa61b85cf2bc5a97d321ed6ebb5
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423259"
---
# <a name="com-map-macros"></a>Macros de mapa COM

Estas macros definen mapas de interfaz COM.

|||
|-|-|
|[BEGIN_COM_MAP](#begin_com_map)|Marca el principio de las entradas de asignación de interfaz COM.|
|[END_COM_MAP](#end_com_map)|Marca el final de las entradas de asignación de interfaz COM.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="begin_com_map"></a>BEGIN_COM_MAP

El mapa COM es el mecanismo que expone las interfaces de un objeto a un cliente a través de `QueryInterface`.

```
BEGIN_COM_MAP(x)
```

### <a name="parameters"></a>Parámetros

*x*<br/>
de Nombre del objeto de clase en el que se exponen las interfaces.

### <a name="remarks"></a>Observaciones

[CComObjectRootEx:: InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) solo devuelve punteros para las interfaces en el mapa com. Inicie el mapa de interfaz con la macro BEGIN_COM_MAP, agregue entradas para cada una de las interfaces con la macro [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) o una de sus variantes y complete el mapa con la macro [END_COM_MAP](#end_com_map) .

### <a name="example"></a>Ejemplo

En el ejemplo de [bip](../../overview/visual-cpp-samples.md) de ATL:

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

##  <a name="end_com_map"></a>END_COM_MAP

Finaliza la definición del mapa de interfaz COM.

```
END_COM_MAP()
```

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)<br/>
[Funciones globales de mapa COM](../../atl/reference/com-map-global-functions.md)
