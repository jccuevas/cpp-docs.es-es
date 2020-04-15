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
ms.openlocfilehash: bf64c073249b7426fafb430a708573d9d06d11fd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321409"
---
# <a name="catlmodulet-class"></a>Clase CAtlModuleT

Esta clase implementa un módulo ATL.

## <a name="syntax"></a>Sintaxis

```
template <class T>
class ATL_NO_VTABLE CAtlModuleT : public CAtlModule
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada `CAtlModuleT`de .

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlModuleT::CAtlModuleT](#catlmodulet)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlModuleT::InitlibId](#initlibid)|Inicializa el miembro de datos que contiene el GUID del módulo actual.|
|[CAtlModuleT::RegisterAppId](#registerappid)|Agrega el archivo EXE al registro.|
|[CAtlModuleT::RegisterServer](#registerserver)|Agrega el servicio al registro.|
|[CAtlModuleT::UnregisterAppId](#unregisterappid)|Quita el archivo EXE del registro.|
|[CAtlModuleT::UnregisterServer](#unregisterserver)|Quita el servicio del registro.|
|[CAtlModuleT::UpdateRegistryAppId](#updateregistryappid)|Actualiza la información EXE en el registro.|

## <a name="remarks"></a>Observaciones

`CAtlModuleT`, derivado de [CAtlModule](../../atl/reference/catlmodule-class.md), implementa un módulo ATL ejecutable (EXE) o de servicio (EXE). Un módulo ejecutable es un servidor local fuera de proceso, mientras que un módulo de servicio es una aplicación de Windows que se ejecuta en segundo plano cuando se inicia Windows.

`CAtlModuleT`proporciona soporte para inicializar, registrar y anular el registro del módulo.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`CAtlModuleT`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="catlmoduletcatlmodulet"></a><a name="catlmodulet"></a>CAtlModuleT::CAtlModuleT

El constructor.

```
CAtlModuleT() throw();
```

### <a name="remarks"></a>Observaciones

Llama a [CAtlModuleT::InitlibId](#initlibid).

## <a name="catlmoduletinitlibid"></a><a name="initlibid"></a>CAtlModuleT::InitlibId

Inicializa el miembro de datos que contiene el GUID del módulo actual.

```
static void InitLibId() throw();
```

### <a name="remarks"></a>Observaciones

Llamado por el constructor [CAtlModuleT::CAtlModuleT](#catlmodulet).

## <a name="catlmoduletregisterappid"></a><a name="registerappid"></a>CAtlModuleT::RegisterAppId

Agrega el archivo EXE al registro.

```
HRESULT RegisterAppId() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="catlmoduletregisterserver"></a><a name="registerserver"></a>CAtlModuleT::RegisterServer

Agrega el servicio al registro.

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*bRegTypeLib*<br/>
TRUESi se va a registrar la biblioteca de tipos. El valor predeterminado es FALSE.

*pCLSID*<br/>
Señala al CLSID del objeto que se va a registrar. Si NULL (el valor predeterminado), se registrarán todos los objetos del mapa de objetos.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="catlmoduletunregisterappid"></a><a name="unregisterappid"></a>CAtlModuleT::UnregisterAppId

Quita el archivo EXE del registro.

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="catlmoduletunregisterserver"></a><a name="unregisterserver"></a>CAtlModuleT::UnregisterServer

Quita el servicio del registro.

```
HRESULT UnregisterServer(
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*bUnRegTypeLib*<br/>
TRUESi la biblioteca de tipos también debe anular el registro.

*pCLSID*<br/>
Señala al CLSID del objeto que se va a anular el registro. Si NULL (el valor predeterminado), todos los objetos del mapa de objetos se anularán el registro.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="catlmoduletupdateregistryappid"></a><a name="updateregistryappid"></a>CAtlModuleT::UpdateRegistryAppId

Actualiza la información EXE en el registro.

```
static HRESULT WINAPI UpdateRegistryAppId(BOOL /* bRegister*/) throw();
```

### <a name="parameters"></a>Parámetros

*bRegistro*<br/>
Reservado.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="see-also"></a>Consulte también

[CAtlModule (clase)](../../atl/reference/catlmodule-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clases de módulo](../../atl/atl-module-classes.md)
