---
title: CAtlBaseModule (Clase)
ms.date: 11/04/2016
f1_keywords:
- CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule::CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule::AddResourceInstance
- ATLCORE/ATL::CAtlBaseModule::GetHInstanceAt
- ATLCORE/ATL::CAtlBaseModule::GetModuleInstance
- ATLCORE/ATL::CAtlBaseModule::GetResourceInstance
- ATLCORE/ATL::CAtlBaseModule::RemoveResourceInstance
- ATLCORE/ATL::CAtlBaseModule::SetResourceInstance
- ATLCORE/ATL::CAtlBaseModule::m_bInitFailed
helpviewer_keywords:
- CAtlBaseModule class
ms.assetid: 55ade80c-9b0c-4c51-933e-2158436c1096
ms.openlocfilehash: a55412eff18fd04ac4e41c0f001991c1cf725b9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321506"
---
# <a name="catlbasemodule-class"></a>CAtlBaseModule (Clase)

Se crea una instancia de esta clase en cada proyecto ATL.

## <a name="syntax"></a>Sintaxis

```
class CAtlBaseModule : public _ATL_BASE_MODULE
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlBaseModule::CAtlBaseModule](#catlbasemodule)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlBaseModule::AddResourceInstance](#addresourceinstance)|Agrega una instancia de recurso a la lista de identificadores almacenados.|
|[CAtlBaseModule::GetHInstanceAt](#gethinstanceat)|Devuelve un identificador a una instancia de recurso especificada.|
|[CAtlBaseModule::GetModuleInstance](#getmoduleinstance)|Devuelve la instancia `CAtlBaseModule` del módulo de un objeto.|
|[CAtlBaseModule::GetResourceInstance](#getresourceinstance)|Devuelve la instancia `CAtlBaseModule` de recurso de un objeto.|
|[CAtlBaseModule::RemoveResourceInstance](#removeresourceinstance)|Quita una instancia de recurso de la lista de identificadores almacenados.|
|[CAtlBaseModule::SetResourceInstance](#setresourceinstance)|Establece la instancia `CAtlBaseModule` de recurso de un objeto.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlBaseModule::m_bInitFailed](#m_binitfailed)|Variable que indica si la inicialización del módulo ha fallado.|

## <a name="remarks"></a>Observaciones

Una instancia `CAtlBaseModule` de _AtlBaseModule con nombre está presente en cada proyecto ATL, que contiene un identificador de la instancia del módulo, un identificador del módulo que contiene recursos (que de forma predeterminada, son uno y el mismo) y una matriz de identificadores a módulos que proporcionan recursos primarios. `CAtlBaseModule`se puede acceder de forma segura desde varios subprocesos.

Esta clase reemplaza la clase [CComModule](../../atl/reference/ccommodule-class.md) obsoleta utilizada en versiones anteriores de ATL.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)

`CAtlBaseModule`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcore.h

## <a name="catlbasemoduleaddresourceinstance"></a><a name="addresourceinstance"></a>CAtlBaseModule::AddResourceInstance

Agrega una instancia de recurso a la lista de identificadores almacenados.

```
bool AddResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parámetros

*hInst*<br/>
La instancia de recurso que se va a agregar.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el recurso se ha agregado correctamente, false en caso contrario.

## <a name="catlbasemodulecatlbasemodule"></a><a name="catlbasemodule"></a>CAtlBaseModule::CAtlBaseModule

El constructor.

```
CAtlBaseModule() throw();
```

### <a name="remarks"></a>Observaciones

Crea la clase `CAtlBaseModule`.

## <a name="catlbasemodulegethinstanceat"></a><a name="gethinstanceat"></a>CAtlBaseModule::GetHInstanceAt

Devuelve un identificador a una instancia de recurso especificada.

```
HINSTANCE GetHInstanceAt(int i) throw();
```

### <a name="parameters"></a>Parámetros

*Ⅰ*<br/>
El número de la instancia de recurso.

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador a la instancia de recurso o NULL si no existe ninguna instancia de recurso correspondiente.

## <a name="catlbasemodulegetmoduleinstance"></a><a name="getmoduleinstance"></a>CAtlBaseModule::GetModuleInstance

Devuelve la instancia `CAtlBaseModule` del módulo de un objeto.

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la instancia del módulo.

## <a name="catlbasemodulegetresourceinstance"></a><a name="getresourceinstance"></a>CAtlBaseModule::GetResourceInstance

Devuelve la instancia de recurso.

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la instancia de recurso.

## <a name="catlbasemodulem_binitfailed"></a><a name="m_binitfailed"></a>CAtlBaseModule::m_bInitFailed

Variable que indica si la inicialización del módulo ha fallado.

```
static bool m_bInitFailed;
```

### <a name="remarks"></a>Observaciones

True si el módulo se inicializó, false si no se pudo inicializar.

## <a name="catlbasemoduleremoveresourceinstance"></a><a name="removeresourceinstance"></a>CAtlBaseModule::RemoveResourceInstance

Quita una instancia de recurso de la lista de identificadores almacenados.

```
bool RemoveResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parámetros

*hInst*<br/>
La instancia de recurso que se va a quitar.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el recurso se quitó correctamente, false en caso contrario.

## <a name="catlbasemodulesetresourceinstance"></a><a name="setresourceinstance"></a>CAtlBaseModule::SetResourceInstance

Establece la instancia `CAtlBaseModule` de recurso de un objeto.

```
HINSTANCE SetResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parámetros

*hInst*<br/>
La nueva instancia de recurso.

### <a name="return-value"></a>Valor devuelto

Devuelve la instancia de recurso actualizada.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clases de módulo](../../atl/atl-module-classes.md)
