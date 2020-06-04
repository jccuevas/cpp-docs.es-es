---
title: Clase CAtlBaseModule
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
ms.openlocfilehash: d57d6e631cb287496a4ff5516e97e65ec0152e30
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168298"
---
# <a name="catlbasemodule-class"></a>Clase CAtlBaseModule

Se crea una instancia de esta clase en cada proyecto ATL.

## <a name="syntax"></a>Sintaxis

```cpp
class CAtlBaseModule : public _ATL_BASE_MODULE
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlBaseModule::CAtlBaseModule](#catlbasemodule)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlBaseModule::AddResourceInstance](#addresourceinstance)|Agrega una instancia de recurso a la lista de identificadores almacenados.|
|[CAtlBaseModule::GetHInstanceAt](#gethinstanceat)|Devuelve un identificador para una instancia de recurso especificada.|
|[CAtlBaseModule::GetModuleInstance](#getmoduleinstance)|Devuelve la instancia de módulo de `CAtlBaseModule` un objeto.|
|[CAtlBaseModule::GetResourceInstance](#getresourceinstance)|Devuelve la instancia de recurso de `CAtlBaseModule` un objeto.|
|[CAtlBaseModule::RemoveResourceInstance](#removeresourceinstance)|Quita una instancia de recurso de la lista de identificadores almacenados.|
|[CAtlBaseModule::SetResourceInstance](#setresourceinstance)|Establece la instancia de recurso de `CAtlBaseModule` un objeto.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlBaseModule:: m_bInitFailed](#m_binitfailed)|Variable que indica si se ha producido un error en la inicialización del módulo.|

## <a name="remarks"></a>Observaciones

Existe una instancia `CAtlBaseModule` de denominada _AtlBaseModule en cada proyecto ATL, que contiene un identificador para la instancia de módulo, un identificador para el módulo que contiene los recursos (que, de forma predeterminada, son uno y el mismo), y una matriz de identificadores para los módulos que proporcionan los recursos principales. `CAtlBaseModule`se puede tener acceso de forma segura desde varios subprocesos.

Esta clase reemplaza la clase de [CComModule](../../atl/reference/ccommodule-class.md) obsoleta utilizada en versiones anteriores de ATL.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)

`CAtlBaseModule`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcore. h

## <a name="catlbasemoduleaddresourceinstance"></a><a name="addresourceinstance"></a>CAtlBaseModule::AddResourceInstance

Agrega una instancia de recurso a la lista de identificadores almacenados.

```cpp
bool AddResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parámetros

*hInst*<br/>
Instancia de recurso que se va a agregar.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el recurso se ha agregado correctamente, false en caso contrario.

## <a name="catlbasemodulecatlbasemodule"></a><a name="catlbasemodule"></a>CAtlBaseModule::CAtlBaseModule

El constructor.

```cpp
CAtlBaseModule() throw();
```

### <a name="remarks"></a>Observaciones

Crea la clase `CAtlBaseModule`.

## <a name="catlbasemodulegethinstanceat"></a><a name="gethinstanceat"></a>CAtlBaseModule::GetHInstanceAt

Devuelve un identificador para una instancia de recurso especificada.

```cpp
HINSTANCE GetHInstanceAt(int i) throw();
```

### <a name="parameters"></a>Parámetros

*Configur*<br/>
Número de la instancia de recurso.

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador de la instancia de recurso o NULL si no existe ninguna instancia de recurso correspondiente.

## <a name="catlbasemodulegetmoduleinstance"></a><a name="getmoduleinstance"></a>CAtlBaseModule::GetModuleInstance

Devuelve la instancia de módulo de `CAtlBaseModule` un objeto.

```cpp
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la instancia del módulo.

## <a name="catlbasemodulegetresourceinstance"></a><a name="getresourceinstance"></a>CAtlBaseModule::GetResourceInstance

Devuelve la instancia de recurso.

```cpp
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la instancia de recurso.

## <a name="catlbasemodulem_binitfailed"></a><a name="m_binitfailed"></a>CAtlBaseModule:: m_bInitFailed

Variable que indica si se ha producido un error en la inicialización del módulo.

```cpp
static bool m_bInitFailed;
```

### <a name="remarks"></a>Observaciones

True si el módulo se inicializó, false si no se pudo inicializar.

## <a name="catlbasemoduleremoveresourceinstance"></a><a name="removeresourceinstance"></a>CAtlBaseModule::RemoveResourceInstance

Quita una instancia de recurso de la lista de identificadores almacenados.

```cpp
bool RemoveResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parámetros

*hInst*<br/>
Instancia de recurso que se va a quitar.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el recurso se ha quitado correctamente, false en caso contrario.

## <a name="catlbasemodulesetresourceinstance"></a><a name="setresourceinstance"></a>CAtlBaseModule::SetResourceInstance

Establece la instancia de recurso de `CAtlBaseModule` un objeto.

```cpp
HINSTANCE SetResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parámetros

*hInst*<br/>
Nueva instancia de recurso.

### <a name="return-value"></a>Valor devuelto

Devuelve la instancia de recurso actualizada.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clases de módulo](../../atl/atl-module-classes.md)
