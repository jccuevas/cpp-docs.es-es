---
title: Clase CAtlModuleT
ms.date: 11/04/2016
f1_keywords:
- CAtlModuleT
- ATLBASE/ATL::CAtlModuleT
- ATLBASE/ATL::CAtlModuleT::CAtlModuleT
- ATLBASE/ATL::CAtlModuleT::InitLibId
- ATLBASE/ATL::CAtlModuleT::RegisterAppId
- ATLBASE/ATL::CAtlModuleT::RegisterServer
- ATLBASE/ATL::CAtlModuleT::UnregisterAppId
- ATLBASE/ATL::CAtlModuleT::UnregisterServer
- ATLBASE/ATL::CAtlModuleT::UpdateRegistryAppId
helpviewer_keywords:
- CAtlModuleT class
ms.assetid: 9b74d02f-9117-47b1-a05e-c5945f83dd2b
ms.openlocfilehash: b07e60265570e66337a2d13007e9ad57c6f369e4
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167869"
---
# <a name="catlmodulet-class"></a>Clase CAtlModuleT

Esta clase implementa un módulo ATL.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
class ATL_NO_VTABLE CAtlModuleT : public CAtlModule
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `CAtlModuleT`.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlModuleT::CAtlModuleT](#catlmodulet)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlModuleT::InitLibId](#initlibid)|Inicializa el miembro de datos que contiene el GUID del módulo actual.|
|[CAtlModuleT::RegisterAppId](#registerappid)|Agrega el archivo EXE al registro.|
|[CAtlModuleT::RegisterServer](#registerserver)|Agrega el servicio al registro.|
|[CAtlModuleT::UnregisterAppId](#unregisterappid)|Quita el archivo EXE del registro.|
|[CAtlModuleT::UnregisterServer](#unregisterserver)|Quita el servicio del registro.|
|[CAtlModuleT::UpdateRegistryAppId](#updateregistryappid)|Actualiza la información del archivo EXE en el registro.|

## <a name="remarks"></a>Observaciones

`CAtlModuleT`, derivado de [CAtlModule](../../atl/reference/catlmodule-class.md), implementa un módulo ATL ejecutable (exe) o de servicio (exe). Un módulo ejecutable es un servidor local y fuera de proceso, mientras que un módulo de servicio es una aplicación de Windows que se ejecuta en segundo plano cuando se inicia Windows.

`CAtlModuleT`proporciona compatibilidad para la inicialización, el registro y la anulación del registro del módulo.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`CAtlModuleT`

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

## <a name="catlmoduletcatlmodulet"></a><a name="catlmodulet"></a>CAtlModuleT::CAtlModuleT

El constructor.

```cpp
CAtlModuleT() throw();
```

### <a name="remarks"></a>Observaciones

Llama a [CAtlModuleT:: InitLibId](#initlibid).

## <a name="catlmoduletinitlibid"></a><a name="initlibid"></a>CAtlModuleT::InitLibId

Inicializa el miembro de datos que contiene el GUID del módulo actual.

```cpp
static void InitLibId() throw();
```

### <a name="remarks"></a>Observaciones

Llamado por el constructor [CAtlModuleT:: CAtlModuleT](#catlmodulet).

## <a name="catlmoduletregisterappid"></a><a name="registerappid"></a>CAtlModuleT::RegisterAppId

Agrega el archivo EXE al registro.

```cpp
HRESULT RegisterAppId() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

## <a name="catlmoduletregisterserver"></a><a name="registerserver"></a>CAtlModuleT::RegisterServer

Agrega el servicio al registro.

```cpp
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*bRegTypeLib*<br/>
TRUE si se va a registrar la biblioteca de tipos. El valor predeterminado es FALSE.

*pCLSID*<br/>
Apunta al CLSID del objeto que se va a registrar. Si es NULL (valor predeterminado), se registrarán todos los objetos del mapa de objetos.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

## <a name="catlmoduletunregisterappid"></a><a name="unregisterappid"></a>CAtlModuleT::UnregisterAppId

Quita el archivo EXE del registro.

```cpp
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

## <a name="catlmoduletunregisterserver"></a><a name="unregisterserver"></a>CAtlModuleT::UnregisterServer

Quita el servicio del registro.

```cpp
HRESULT UnregisterServer(
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*bUnRegTypeLib*<br/>
TRUE si también se va a anular el registro de la biblioteca de tipos.

*pCLSID*<br/>
Apunta al CLSID del objeto del que se va a anular el registro. Si es NULL (valor predeterminado), se anulará el registro de todos los objetos del mapa de objetos.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

## <a name="catlmoduletupdateregistryappid"></a><a name="updateregistryappid"></a>CAtlModuleT::UpdateRegistryAppId

Actualiza la información del archivo EXE en el registro.

```cpp
static HRESULT WINAPI UpdateRegistryAppId(BOOL /* bRegister*/) throw();
```

### <a name="parameters"></a>Parámetros

*bRegister*<br/>
Reservado.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

## <a name="see-also"></a>Consulte también

[Clase CAtlModule](../../atl/reference/catlmodule-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clases de módulo](../../atl/atl-module-classes.md)
