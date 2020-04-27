---
title: Clase CAtlComModule
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
ms.openlocfilehash: 4b8c98630b27c35ed6a7e32318c6ebad8a82a5c5
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168837"
---
# <a name="catlcommodule-class"></a>Clase CAtlComModule

Esta clase implementa un módulo de servidor COM.

## <a name="syntax"></a>Sintaxis

```cpp
class CAtlComModule : public _ATL_COM_MODULE
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlComModule::CAtlComModule](#catlcommodule)|El constructor.|
|[CAtlComModule:: ~ CAtlComModule](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlComModule::RegisterServer](#registerserver)|Llame a este método para actualizar el registro del sistema para cada objeto del mapa de objetos.|
|[CAtlComModule::RegisterTypeLib](#registertypelib)|Llame a este método para registrar una biblioteca de tipos.|
|[CAtlComModule::UnregisterServer](#unregisterserver)|Llame a este método para anular el registro de cada objeto en el mapa de objetos.|
|[CAtlComModule::UnRegisterTypeLib](#unregistertypelib)|Llame a este método para anular el registro de una biblioteca de tipos.|

## <a name="remarks"></a>Observaciones

`CAtlComModule`implementa un módulo de servidor COM, lo que permite que un cliente tenga acceso a los componentes del módulo.

Esta clase reemplaza la clase de [CComModule](../../atl/reference/ccommodule-class.md) obsoleta utilizada en versiones anteriores de ATL. Vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)

`CAtlComModule`

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

## <a name="catlcommodulecatlcommodule"></a><a name="catlcommodule"></a>CAtlComModule::CAtlComModule

El constructor.

```cpp
CAtlComModule() throw();
```

### <a name="remarks"></a>Observaciones

Inicializa el módulo.

## <a name="catlcommodulecatlcommodule"></a><a name="dtor"></a>CAtlComModule:: ~ CAtlComModule

Destructor.

```cpp
~CAtlComModule();
```

### <a name="remarks"></a>Observaciones

Libera todos los generadores de clases.

## <a name="catlcommoduleregisterserver"></a><a name="registerserver"></a>CAtlComModule::RegisterServer

Llame a este método para actualizar el registro del sistema para cada objeto del mapa de objetos.

```cpp
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Parámetros

*bRegTypeLib*<br/>
TRUE si se va a registrar la biblioteca de tipos. El valor predeterminado es FALSE.

*pCLSID*<br/>
Apunta al CLSID del objeto que se va a registrar. Si es NULL (valor predeterminado), se registrarán todos los objetos del mapa de objetos.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Llama a la función global [AtlComModuleRegisterServer](server-registration-global-functions.md#atlcommoduleregisterserver).

## <a name="catlcommoduleregistertypelib"></a><a name="registertypelib"></a>CAtlComModule::RegisterTypeLib

Llame a este método para registrar una biblioteca de tipos.

```cpp
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```

### <a name="parameters"></a>Parámetros

*lpszIndex*<br/>
Cadena con el formato "\\\n", donde N es el índice entero del recurso typelib.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Agrega información sobre una biblioteca de tipos al registro del sistema. Si la instancia del módulo contiene varias bibliotecas de tipos, utilice la primera versión de este método para especificar la biblioteca de tipos que se debe usar.

## <a name="catlcommoduleunregisterserver"></a><a name="unregisterserver"></a>CAtlComModule::UnregisterServer

Llame a este método para anular el registro de cada objeto en el mapa de objetos.

```cpp
HRESULT UnregisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Parámetros

*bRegTypeLib*<br/>
TRUE si se va a anular el registro de la biblioteca de tipos. El valor predeterminado es FALSE.

*pCLSID*<br/>
Apunta al CLSID del objeto del que se va a anular el registro. Si es NULL (valor predeterminado), se anulará el registro de todos los objetos del mapa de objetos.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Llama a la función global [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver).

## <a name="catlcommoduleunregistertypelib"></a><a name="unregistertypelib"></a>CAtlComModule::UnRegisterTypeLib

Llame a este método para anular el registro de una biblioteca de tipos.

```cpp
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```

### <a name="parameters"></a>Parámetros

*lpszIndex*<br/>
Cadena con el formato "\\\n", donde N es el índice entero del recurso typelib.

### <a name="remarks"></a>Observaciones

Quita información sobre una biblioteca de tipos del registro del sistema. Si la instancia del módulo contiene varias bibliotecas de tipos, utilice la primera versión de este método para especificar la biblioteca de tipos que se debe usar.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

## <a name="see-also"></a>Consulte también

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
