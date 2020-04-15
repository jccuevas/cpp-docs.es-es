---
title: CAtlComModule (Clase)
ms.date: 11/04/2016
f1_keywords:
- CAtlComModule
- ATLBASE/ATL::CAtlComModule
- ATLBASE/ATL::CAtlComModule::CAtlComModule
- ATLBASE/ATL::CAtlComModule::RegisterServer
- ATLBASE/ATL::CAtlComModule::RegisterTypeLib
- ATLBASE/ATL::CAtlComModule::UnregisterServer
- ATLBASE/ATL::CAtlComModule::UnRegisterTypeLib
helpviewer_keywords:
- CAtlComModule class
ms.assetid: af5dd71a-a0d1-4a2e-9a24-154a03381c75
ms.openlocfilehash: 68fdb48edc9304d9d74df6f36bd208cfd35ff307
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321478"
---
# <a name="catlcommodule-class"></a>CAtlComModule (Clase)

Esta clase implementa un módulo de servidor COM.

## <a name="syntax"></a>Sintaxis

```
class CAtlComModule : public _ATL_COM_MODULE
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlComModule::CAtlComModule](#catlcommodule)|El constructor.|
|[CAtlComModule::-CAtlComModule](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlComModule::RegisterServer](#registerserver)|Llame a este método para actualizar el registro del sistema para cada objeto en el mapa de objetos.|
|[CAtlComModule::RegisterTypeLib](#registertypelib)|Llame a este método para registrar una biblioteca de tipos.|
|[CAtlComModule::UnregisterServer](#unregisterserver)|Llame a este método para anular el registro de cada objeto en el mapa de objetos.|
|[CAtlComModule::UnRegisterTypeLib](#unregistertypelib)|Llame a este método para anular el registro de una biblioteca de tipos.|

## <a name="remarks"></a>Observaciones

`CAtlComModule`implementa un módulo de servidor COM, lo que permite a un cliente acceder a los componentes del módulo.

Esta clase reemplaza la clase [CComModule](../../atl/reference/ccommodule-class.md) obsoleta utilizada en versiones anteriores de ATL. Consulte [Clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)

`CAtlComModule`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="catlcommodulecatlcommodule"></a><a name="catlcommodule"></a>CAtlComModule::CAtlComModule

El constructor.

```
CAtlComModule() throw();
```

### <a name="remarks"></a>Observaciones

Inicializa el módulo.

## <a name="catlcommodulecatlcommodule"></a><a name="dtor"></a>CAtlComModule::-CAtlComModule

Destructor.

```
~CAtlComModule();
```

### <a name="remarks"></a>Observaciones

Libera todas las fábricas de clase.

## <a name="catlcommoduleregisterserver"></a><a name="registerserver"></a>CAtlComModule::RegisterServer

Llame a este método para actualizar el registro del sistema para cada objeto en el mapa de objetos.

```
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Parámetros

*bRegTypeLib*<br/>
TRUESi se va a registrar la biblioteca de tipos. El valor predeterminado es FALSE.

*pCLSID*<br/>
Señala al CLSID del objeto que se va a registrar. Si NULL (el valor predeterminado), se registrarán todos los objetos del mapa de objetos.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Llama a la función global [AtlComModuleRegisterServer](server-registration-global-functions.md#atlcommoduleregisterserver).

## <a name="catlcommoduleregistertypelib"></a><a name="registertypelib"></a>CAtlComModule::RegisterTypeLib

Llame a este método para registrar una biblioteca de tipos.

```
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```

### <a name="parameters"></a>Parámetros

*lpszIndex*<br/>
Cadena con el\\formato " .N", donde N es el índice entero del recurso TYPELIB.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Agrega información sobre una biblioteca de tipos al registro del sistema. Si la instancia del módulo contiene varias bibliotecas de tipos, utilice la primera versión de este método para especificar qué biblioteca de tipos se debe utilizar.

## <a name="catlcommoduleunregisterserver"></a><a name="unregisterserver"></a>CAtlComModule::UnregisterServer

Llame a este método para anular el registro de cada objeto en el mapa de objetos.

```
HRESULT UnregisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Parámetros

*bRegTypeLib*<br/>
TRUESi se va a anular el registro de la biblioteca de tipos. El valor predeterminado es FALSE.

*pCLSID*<br/>
Señala al CLSID del objeto que se va a anular el registro. Si NULL (el valor predeterminado), todos los objetos del mapa de objetos se anularán el registro.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Llama a la función global [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver).

## <a name="catlcommoduleunregistertypelib"></a><a name="unregistertypelib"></a>CAtlComModule::UnRegisterTypeLib

Llame a este método para anular el registro de una biblioteca de tipos.

```
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```

### <a name="parameters"></a>Parámetros

*lpszIndex*<br/>
Cadena con el\\formato " .N", donde N es el índice entero del recurso TYPELIB.

### <a name="remarks"></a>Observaciones

Quita información sobre una biblioteca de tipos del registro del sistema. Si la instancia del módulo contiene varias bibliotecas de tipos, utilice la primera versión de este método para especificar qué biblioteca de tipos se debe utilizar.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="see-also"></a>Consulte también

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
