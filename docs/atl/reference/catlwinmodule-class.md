---
title: Clase CAtlWinModule
ms.date: 11/04/2016
f1_keywords:
- CAtlWinModule
- ATLBASE/ATL::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::AddCreateWndData
- ATLBASE/ATL::CAtlWinModule::ExtractCreateWndData
helpviewer_keywords:
- CAtlWinModule class
ms.assetid: 7ec844af-0f68-4a34-b0c8-9de50a025df0
ms.openlocfilehash: 5cdf13ebbb982ad8184a52dcf1a3e30d71e4e5b0
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167713"
---
# <a name="catlwinmodule-class"></a>Clase CAtlWinModule

Esta clase proporciona compatibilidad con los componentes de ventanas de ATL.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```cpp
class CAtlWinModule : public _ATL_WIN_MODULE
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlWinModule::CAtlWinModule](#catlwinmodule)|El constructor.|
|[CAtlWinModule:: ~ CAtlWinModule](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlWinModule::AddCreateWndData](#addcreatewnddata)|Agrega un objeto de datos.|
|[CAtlWinModule::ExtractCreateWndData](#extractcreatewnddata)|Devuelve un puntero al objeto de datos del módulo de ventana.|

## <a name="remarks"></a>Observaciones

Esta clase proporciona compatibilidad con todas las clases ATL que requieren características de ventanas.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)

`CAtlWinModule`

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

## <a name="catlwinmoduleaddcreatewnddata"></a><a name="addcreatewnddata"></a>CAtlWinModule::AddCreateWndData

Este método inicializa y agrega una `_AtlCreateWndData` estructura.

```cpp
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```

### <a name="parameters"></a>Parámetros

*pData*<br/>
Puntero a la `_AtlCreateWndData` estructura que se va a inicializar y agregar al módulo actual.

*pObject*<br/>
Puntero al puntero **this** de un objeto.

### <a name="remarks"></a>Observaciones

Este método llama a [AtlWinModuleAddCreateWndData](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata) , que Inicializa una estructura [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) . Esta estructura almacenará el puntero **this** , que se usa para obtener la instancia de clase en los procedimientos de ventana.

## <a name="catlwinmodulecatlwinmodule"></a><a name="catlwinmodule"></a>CAtlWinModule::CAtlWinModule

El constructor.

```cpp
CAtlWinModule();
```

### <a name="remarks"></a>Observaciones

Si se produce un error de inicialización, se produce una excepción **EXCEPTION_NONCONTINUABLE** .

## <a name="catlwinmodulecatlwinmodule"></a><a name="dtor"></a>CAtlWinModule:: ~ CAtlWinModule

Destructor.

```cpp
~CAtlWinModule();
```

### <a name="remarks"></a>Observaciones

Libera todos los recursos asignados.

## <a name="catlwinmoduleextractcreatewnddata"></a><a name="extractcreatewnddata"></a>CAtlWinModule::ExtractCreateWndData

Este método devuelve un puntero a una `_AtlCreateWndData` estructura.

```cpp
void* ExtractCreateWndData();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la `_AtlCreateWndData` estructura agregada anteriormente con [CAtlWinModule:: AddCreateWndData](#addcreatewnddata)o null si no hay ningún objeto disponible.

## <a name="see-also"></a>Consulte también

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clases de módulo](../../atl/atl-module-classes.md)
