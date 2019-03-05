---
title: CAtlBaseModule (clase)
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
ms.openlocfilehash: d382d1fe7d50a2fdeefc9b477625580792de7d6f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284767"
---
# <a name="catlbasemodule-class"></a>CAtlBaseModule (clase)

Esta clase se crean instancias en todos los proyectos ATL.

## <a name="syntax"></a>Sintaxis

```
class CAtlBaseModule : public _ATL_BASE_MODULE
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CAtlBaseModule::CAtlBaseModule](#catlbasemodule)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CAtlBaseModule::AddResourceInstance](#addresourceinstance)|Agrega una instancia de recursos a la lista de identificadores almacenados.|
|[CAtlBaseModule::GetHInstanceAt](#gethinstanceat)|Devuelve un identificador para una instancia del recurso especificado.|
|[CAtlBaseModule::GetModuleInstance](#getmoduleinstance)|Devuelve la instancia de módulo desde un `CAtlBaseModule` objeto.|
|[CAtlBaseModule::GetResourceInstance](#getresourceinstance)|Devuelve la instancia del recurso desde un `CAtlBaseModule` objeto.|
|[CAtlBaseModule::RemoveResourceInstance](#removeresourceinstance)|Quita una instancia de recursos de la lista de identificadores almacenados.|
|[CAtlBaseModule::SetResourceInstance](#setresourceinstance)|Establece la instancia del recurso de un `CAtlBaseModule` objeto.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CAtlBaseModule::m_bInitFailed](#m_binitfailed)|Una variable que indica si la inicialización del módulo no ha podido.|

## <a name="remarks"></a>Comentarios

Una instancia de `CAtlBaseModule` _AtlBaseModule con nombre está presente en todos los proyectos ATL, que contiene un identificador de la instancia de módulo, un identificador para el módulo que contiene recursos (que de forma predeterminada, son del mismo) y una matriz de identificadores de módulos para proporcionar principal recursos. `CAtlBaseModule` se puede acceder de forma segura desde varios subprocesos.

Esta clase reemplaza el atributo obsolete [CComModule](../../atl/reference/ccommodule-class.md) clase utilizada en versiones anteriores de ATL.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)

`CAtlBaseModule`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcore.h

##  <a name="addresourceinstance"></a>  CAtlBaseModule::AddResourceInstance

Agrega una instancia de recursos a la lista de identificadores almacenados.

```
bool AddResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parámetros

*hInst*<br/>
Para agregar la instancia del recurso.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el recurso correctamente se agregan, false en caso contrario.

##  <a name="catlbasemodule"></a>  CAtlBaseModule::CAtlBaseModule

El constructor.

```
CAtlBaseModule() throw();
```

### <a name="remarks"></a>Comentarios

Crea la clase `CAtlBaseModule`.

##  <a name="gethinstanceat"></a>  CAtlBaseModule::GetHInstanceAt

Devuelve un identificador para una instancia del recurso especificado.

```
HINSTANCE GetHInstanceAt(int i) throw();
```

### <a name="parameters"></a>Parámetros

*i*<br/>
El número de la instancia del recurso.

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador para la instancia de recurso, o NULL si no existe ninguna instancia de recurso correspondiente.

##  <a name="getmoduleinstance"></a>  CAtlBaseModule::GetModuleInstance

Devuelve la instancia de módulo desde un `CAtlBaseModule` objeto.

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la instancia de módulo.

##  <a name="getresourceinstance"></a>  CAtlBaseModule::GetResourceInstance

Devuelve la instancia del recurso.

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la instancia del recurso.

##  <a name="m_binitfailed"></a>  CAtlBaseModule::m_bInitFailed

Una variable que indica si la inicialización del módulo no ha podido.

```
static bool m_bInitFailed;
```

### <a name="remarks"></a>Comentarios

True si el módulo inicializa, false si no pudo inicializar.

##  <a name="removeresourceinstance"></a>  CAtlBaseModule::RemoveResourceInstance

Quita una instancia de recursos de la lista de identificadores almacenados.

```
bool RemoveResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parámetros

*hInst*<br/>
Para quitar la instancia del recurso.

### <a name="return-value"></a>Valor devuelto

Devuelve true si se ha quitado correctamente el recurso.

##  <a name="setresourceinstance"></a>  CAtlBaseModule::SetResourceInstance

Establece la instancia del recurso de un `CAtlBaseModule` objeto.

```
HINSTANCE SetResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parámetros

*hInst*<br/>
La nueva instancia de recurso.

### <a name="return-value"></a>Valor devuelto

Devuelve la instancia de recurso actualizado.

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clases de módulo](../../atl/atl-module-classes.md)
