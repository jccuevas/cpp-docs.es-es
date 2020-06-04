---
title: Funciones globales de registro de servidores
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlComModuleRegisterServer
- atlbase/ATL::AtlComModuleUnregisterServer
- atlbase/ATL::AtlComModuleRegisterClassObjects
- atlbase/ATL::AtlComModuleRevokeClassObjects
- atlbase/ATL::AtlComModuleGetClassObject
ms.assetid: c2f0a35d-857c-4538-a44d-c4ea0db63b06
ms.openlocfilehash: fb6353b52f487d0511c54223fe9e31dab88704b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325924"
---
# <a name="server-registration-global-functions"></a>Funciones globales de registro de servidores

Estas funciones proporcionan compatibilidad para registrar y anular el registro de objetos de servidor en el mapa de objetos.

> [!IMPORTANT]
> Las funciones enumeradas en la tabla siguiente no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

|||
|-|-|
|[AtlComModuleRegisterServer](#atlcommoduleregisterserver)|Esta función se invoca para registrar todos los objetos del mapa de objetos.|
|[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)|Esta función se invoca para anular el registro de todos los objetos del mapa de objetos.|
|[AtlComModuleRegisterClassObjects](#atlcommoduleregisterclassobjects)|Esta función se invoca para registrar los objetos de clase.|
|[AtlComModuleRevokeClassObjects](#atlcommodulerevokeclassobjects)|Esta función se llama para revocar objetos de clase de un módulo COM.|
|[AtlComModuleGetClassObject](#atlcommodulegetclassobject)|Esta función se llama para obtener el objeto de clase.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="atlcommoduleregisterserver"></a><a name="atlcommoduleregisterserver"></a>AtlComModuleRegisterServer

Esta función se invoca para registrar todos los objetos del mapa de objetos.

```
ATLINLINE ATLAPI AtlComModuleRegisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>Parámetros

*pComModule*<br/>
Puntero al módulo COM.

*bRegTypeLib*<br/>
TRUESi se va a registrar la biblioteca de tipos.

*pCLSID*<br/>
Señala al CLSID del objeto que se va a registrar. Si NULL, se registrarán todos los objetos del mapa de objetos.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

`AtlComModuleRegisterServer`recorre el mapa de objetos generado automáticamente ATL y registra cada objeto del mapa. Si *pCLSID* no es NULL, solo se registra el objeto al que hace referencia *pCLSID;* de lo contrario, todos los objetos están registrados.

[CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver)llama a esta función .

## <a name="atlcommoduleunregisterserver"></a><a name="atlcommoduleunregisterserver"></a>AtlComModuleUnregisterServer

Esta función se invoca para anular el registro de todos los objetos del mapa de objetos.

```
ATLINLINE ATLAPI AtlComModuleUnregisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>Parámetros

*pComModule*<br/>
Puntero al módulo COM.

*bUnRegTypeLib*<br/>
TRUESi se va a registrar la biblioteca de tipos.

*pCLSID*<br/>
Señala al CLSID del objeto que se va a anular el registro. Si NULL todos los objetos del mapa de objetos se anularán el registro.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

`AtlComModuleUnregisterServer`recorre el mapa de objetos ATL y anula el registro de cada objeto del mapa. Si *pCLSID* no es NULL, solo se anula el registro del objeto al que hace referencia *pCLSID;* de lo contrario, todos los objetos no están registrados.

[CAtlComModule::UnregisterServer](catlcommodule-class.md#unregisterserver)llama a esta función.

## <a name="atlcommoduleregisterclassobjects"></a><a name="atlcommoduleregisterclassobjects"></a>AtlComModuleRegisterClassObjects

Esta función se invoca para registrar los objetos de clase.

```
ATLINLINE ATLAPI AtlComModuleRegisterClassObjects(
    _ATL_COM_MODULE* pComModule,
    DWORD dwClsContext,
    DWORD dwFlags);
```

### <a name="parameters"></a>Parámetros

*pComModule*<br/>
Puntero al módulo COM.

*dwClsContext*<br/>
Especifica el contexto en el que se va a ejecutar el objeto de clase. Los valores posibles son CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER o CLSCTX_LOCAL_SERVER. Consulte [CLSCTX](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx) para obtener más detalles.

*dwFlags*<br/>
Determina los tipos de conexión al objeto de clase. Los valores posibles son REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE o REGCLS_MULTI_SEPARATE. Consulte [REGCLS](/windows/win32/api/combaseapi/ne-combaseapi-regcls) para obtener más detalles.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Esta función auxiliar es utilizada por [CComModule::RegisterClassObjects](ccommodule-class.md#registerclassobjects) (obsoleto en ATL 7.0) y [CAtlExeModuleT::RegisterClassObjects](catlexemodulet-class.md#registerclassobjects).

## <a name="atlcommodulerevokeclassobjects"></a><a name="atlcommodulerevokeclassobjects"></a>AtlComModuleRevokeClassObjects

Esta función se invoca para quitar el generador o generadores de clases de la tabla de objetos en ejecución.

```
ATLINLINE ATLAPI AtlComModuleRevokeClassObjects(_ATL_COM_MODULE* pComModule);
```

### <a name="parameters"></a>Parámetros

*pComModule*<br/>
Puntero al módulo COM.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Esta función auxiliar es utilizada por [CComModule::RevokeClassObjects](ccommodule-class.md#revokeclassobjects) (obsoleto en ATL 7.0) y [CAtlExeModuleT::RevokeClassObjects](catlexemodulet-class.md#revokeclassobjects).

## <a name="atlcommodulegetclassobject"></a><a name="atlcommodulegetclassobject"></a>AtlComModuleGetClassObject

Esta función se invoca para devolver el generador de clases.

```
ATLINLINE ATLAPI AtlComModuleGetClassObject(
    _ATL_COM_MODULE* pComModule,
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv);
```

### <a name="parameters"></a>Parámetros

*pComModule*<br/>
Puntero al módulo COM.

*rclsid*<br/>
El CLSID del objeto que se va a crear.

*riid*<br/>
El IID de la interfaz solicitada.

*Ppv*<br/>
Un puntero al puntero de interfaz identificado por *riid*. Si el objeto no admite esta interfaz, *ppv* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Esta función auxiliar es utilizada por [CComModule::GetClassObject](ccommodule-class.md#getclassobject) (obsoleto en ATL 7.0) y [CAtlDllModuleT::GetClassObject](catldllmodulet-class.md#getclassobject).

## <a name="see-also"></a>Consulte también

[Functions](../../atl/reference/atl-functions.md)
