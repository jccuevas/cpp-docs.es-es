---
title: CAtlWinModule (clase)
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
ms.openlocfilehash: 40385fd592563837546b483bb80978cde6a56555
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321272"
---
# <a name="catlwinmodule-class"></a>CAtlWinModule (clase)

Esta clase proporciona compatibilidad con los componentes de ventanas ATL.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CAtlWinModule : public _ATL_WIN_MODULE
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlWinModule::CAtlWinModule](#catlwinmodule)|El constructor.|
|[CAtlWinModule::-CAtlWinModule](#dtor)|Destructor.|

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

**Encabezado:** atlbase.h

## <a name="catlwinmoduleaddcreatewnddata"></a><a name="addcreatewnddata"></a>CAtlWinModule::AddCreateWndData

Este método inicializa y `_AtlCreateWndData` agrega una estructura.

```
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```

### <a name="parameters"></a>Parámetros

*pData*<br/>
Puntero a `_AtlCreateWndData` la estructura que se va a inicializar y agregar al módulo actual.

*pObject*<br/>
Puntero a un objeto **de este** puntero.

### <a name="remarks"></a>Observaciones

Este método llama a [AtlWinModuleAddCreateWndData](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata) que inicializa una [estructura _AtlCreateWndData.](../../atl/reference/atlcreatewnddata-structure.md) Esta estructura almacenará el puntero **this,** utilizado para obtener la instancia de clase en procedimientos de ventana.

## <a name="catlwinmodulecatlwinmodule"></a><a name="catlwinmodule"></a>CAtlWinModule::CAtlWinModule

El constructor.

```
CAtlWinModule();
```

### <a name="remarks"></a>Observaciones

Si se produce un error en la inicialización, se genera **una** EXCEPTION_NONCONTINUABLE excepción.

## <a name="catlwinmodulecatlwinmodule"></a><a name="dtor"></a>CAtlWinModule::-CAtlWinModule

Destructor.

```
~CAtlWinModule();
```

### <a name="remarks"></a>Observaciones

Libera todos los recursos asignados.

## <a name="catlwinmoduleextractcreatewnddata"></a><a name="extractcreatewnddata"></a>CAtlWinModule::ExtractCreateWndData

Este método devuelve un `_AtlCreateWndData` puntero a una estructura.

```
void* ExtractCreateWndData();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero `_AtlCreateWndData` a la estructura agregada anteriormente con [CAtlWinModule::AddCreateWndData](#addcreatewnddata)o NULL si no hay ningún objeto disponible.

## <a name="see-also"></a>Consulte también

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clases de módulo](../../atl/atl-module-classes.md)
