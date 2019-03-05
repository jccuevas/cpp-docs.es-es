---
title: CAtlComModule (clase)
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
ms.openlocfilehash: 09adcb33ca9e6f8524063130d6aedca044d6ecb5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57275875"
---
# <a name="catlcommodule-class"></a>CAtlComModule (clase)

Esta clase implementa un módulo COM del servidor.

## <a name="syntax"></a>Sintaxis

```
class CAtlComModule : public _ATL_COM_MODULE
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CAtlComModule::CAtlComModule](#catlcommodule)|El constructor.|
|[CAtlComModule::~CAtlComModule](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CAtlComModule::RegisterServer](#registerserver)|Llame a este método para actualizar el registro del sistema para cada objeto de mapa de objetos.|
|[CAtlComModule::RegisterTypeLib](#registertypelib)|Llame a este método para registrar una biblioteca de tipos.|
|[CAtlComModule::UnregisterServer](#unregisterserver)|Llame a este método para anular el registro de cada objeto en el mapa de objetos.|
|[CAtlComModule::UnRegisterTypeLib](#unregistertypelib)|Llame a este método para anular el registro de una biblioteca de tipos.|

## <a name="remarks"></a>Comentarios

`CAtlComModule` implementa un módulo de servidor COM, lo que permite a un cliente tener acceso a los componentes del módulo.

Esta clase reemplaza el atributo obsolete [CComModule](../../atl/reference/ccommodule-class.md) clase utilizada en versiones anteriores de ATL. Consulte [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)

`CAtlComModule`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="catlcommodule"></a>  CAtlComModule::CAtlComModule

El constructor.

```
CAtlComModule() throw();
```

### <a name="remarks"></a>Comentarios

Inicializa el módulo.

##  <a name="dtor"></a>  CAtlComModule::~CAtlComModule

Destructor.

```
~CAtlComModule();
```

### <a name="remarks"></a>Comentarios

Libera todos los generadores de clases.

##  <a name="registerserver"></a>  CAtlComModule::RegisterServer

Llame a este método para actualizar el registro del sistema para cada objeto de mapa de objetos.

```
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Parámetros

*bRegTypeLib*<br/>
TRUE si la biblioteca de tipos es que se registrarán. El valor predeterminado es FALSE.

*pCLSID*<br/>
Señala el CLSID del objeto que se registrarán. Si es NULL (valor predeterminado), todos los objetos en el mapa de objetos que se registra.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Llama a la función global [AtlComModuleRegisterServer](server-registration-global-functions.md#atlcommoduleregisterserver).

##  <a name="registertypelib"></a>  CAtlComModule::RegisterTypeLib

Llame a este método para registrar una biblioteca de tipos.

```
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```

### <a name="parameters"></a>Parámetros

*lpszIndex*<br/>
Cadena con el formato "\\\N", donde N es el índice de entero del recurso de biblioteca de tipos.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Agrega información sobre una biblioteca de tipos para el registro del sistema. Si la instancia de módulo contiene varias bibliotecas de tipos, use la primera versión de este método para especificar qué biblioteca de tipos que se debe usar.

##  <a name="unregisterserver"></a>  CAtlComModule::UnregisterServer

Llame a este método para anular el registro de cada objeto en el mapa de objetos.

```
HRESULT UnregisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Parámetros

*bRegTypeLib*<br/>
TRUE si la biblioteca de tipos es se va a anular. El valor predeterminado es FALSE.

*pCLSID*<br/>
Señala el CLSID del objeto que se va a anular. Si es NULL (valor predeterminado), todos los objetos en el mapa de objetos se anulará.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Llama a la función global [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver).

##  <a name="unregistertypelib"></a>  CAtlComModule::UnRegisterTypeLib

Llame a este método para anular el registro de una biblioteca de tipos.

```
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```

### <a name="parameters"></a>Parámetros

*lpszIndex*<br/>
Cadena con el formato "\\\N", donde N es el índice de entero del recurso de biblioteca de tipos.

### <a name="remarks"></a>Comentarios

Quita la información sobre una biblioteca de tipos desde el registro del sistema. Si la instancia de módulo contiene varias bibliotecas de tipos, use la primera versión de este método para especificar qué biblioteca de tipos que se debe usar.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

## <a name="see-also"></a>Vea también

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
