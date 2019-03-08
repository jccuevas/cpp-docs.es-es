---
title: Macros de mapa COM
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
ms.openlocfilehash: dbb84814c6865b5b666a8b3a1162e81a211de1eb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280711"
---
# <a name="com-map-macros"></a>Macros de mapa COM

Estas macros definen los mapas de interfaz COM.

|||
|-|-|
|[BEGIN_COM_MAP](#begin_com_map)|Marca el principio de las entradas del mapa de interfaz COM.|
|[END_COM_MAP](#end_com_map)|Marca el final de las entradas de mapa de interfaz COM.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="begin_com_map"></a>  BEGIN_COM_MAP

El mapa COM es el mecanismo que expone las interfaces en un objeto a un cliente a través de `QueryInterface`.

```
BEGIN_COM_MAP(x)
```

### <a name="parameters"></a>Parámetros

*x*<br/>
[in] El nombre del objeto de clase que se exponen en las interfaces.

### <a name="remarks"></a>Comentarios

[CComObjectRootEx:: InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) solo devuelve punteros para las interfaces en el mapa COM. Iniciar el mapa de interfaz con la macro BEGIN_COM_MAP, agregar entradas para cada una de las interfaces con la [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) macro o uno de sus variantes y complete el mapa con el [END_COM_MAP](#end_com_map) macro.

### <a name="example"></a>Ejemplo

Desde la biblioteca ATL [BUSCAPERSONAS](../../visual-cpp-samples.md) ejemplo:

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

##  <a name="end_com_map"></a>  END_COM_MAP

Termina la definición de la asignación de interfaz COM.

```
END_COM_MAP()
```

## <a name="see-also"></a>Vea también

[Macros](../../atl/reference/atl-macros.md)<br/>
[Funciones globales de mapa COM](../../atl/reference/com-map-global-functions.md)
