---
title: Funciones globales de registro de servidor
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlComModuleRegisterServer
- atlbase/ATL::AtlComModuleUnregisterServer
- atlbase/ATL::AtlComModuleRegisterClassObjects
- atlbase/ATL::AtlComModuleRevokeClassObjects
- atlbase/ATL::AtlComModuleGetClassObject
ms.assetid: c2f0a35d-857c-4538-a44d-c4ea0db63b06
ms.openlocfilehash: 2088bd938aeac70193165cdbd43bd10203ecc49e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62197463"
---
# <a name="server-registration-global-functions"></a>Funciones globales de registro de servidor

Estas funciones proporcionan compatibilidad para registrar y anular el registro de objetos de servidor en el mapa de objetos.

> [!IMPORTANT]
>  Las funciones enumeradas en la tabla siguiente no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

|||
|-|-|
|[AtlComModuleRegisterServer](#atlcommoduleregisterserver)|Esta función se invoca para registrar todos los objetos del mapa de objetos.|
|[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)|Esta función se invoca para anular el registro de todos los objetos del mapa de objetos.|
|[AtlComModuleRegisterClassObjects](#atlcommoduleregisterclassobjects)|Esta función se invoca para registrar los objetos de clase.|
|[AtlComModuleRevokeClassObjects](#atlcommodulerevokeclassobjects)|Esta función se invoca para revocar los objetos de clase desde un módulo COM.|
|[AtlComModuleGetClassObject](#atlcommodulegetclassobject)|Esta función se llama para obtener el objeto de clase.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="atlcommoduleregisterserver"></a>  AtlComModuleRegisterServer

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
TRUE si la biblioteca de tipos es que se registrarán.

*pCLSID*<br/>
Señala el CLSID del objeto que se registrarán. Si es NULL, se registrarán todos los objetos en el mapa de objetos.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

`AtlComModuleRegisterServer` recorre el mapa de objetos ATL generado automáticamente y se registra cada objeto en el mapa. Si *pTypeInfo* no es NULL y, a continuación, solo el objeto al que hace referencia *pTypeInfo* está registrado; en caso contrario, todos los objetos están registrados.

Esta función se invoca [CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver).

##  <a name="atlcommoduleunregisterserver"></a>  AtlComModuleUnregisterServer

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
TRUE si la biblioteca de tipos es que se registrarán.

*pCLSID*<br/>
Señala el CLSID del objeto que se va a anular. Si NULL se anula todos los objetos en el mapa de objetos.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

`AtlComModuleUnregisterServer` recorre el mapa de objetos ATL y anula el registro de cada objeto en el mapa. Si *pTypeInfo* no es NULL y, a continuación, solo el objeto al que hace referencia *pTypeInfo* no está registrada; en caso contrario, todos los objetos se eliminan del registrados.

Esta función se invoca [CAtlComModule::UnregisterServer](catlcommodule-class.md#unregisterserver).

##  <a name="atlcommoduleregisterclassobjects"></a>  AtlComModuleRegisterClassObjects

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
Especifica el contexto en el que se ejecutará el objeto de clase. Los valores posibles son CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER o CLSCTX_LOCAL_SERVER. Consulte [CLSCTX](/windows/desktop/api/wtypesbase/ne-wtypesbase-tagclsctx) para obtener más detalles.

*dwFlags*<br/>
Determina los tipos de conexión para el objeto de clase. Los valores posibles son REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE o REGCLS_MULTI_SEPARATE. Consulte [REGCLS](/windows/desktop/api/combaseapi/ne-combaseapi-tagregcls) para obtener más detalles.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Esta función auxiliar utilizan [CComModule::RegisterClassObjects](ccommodule-class.md#registerclassobjects) (obsoleto en ATL 7.0) y [CAtlExeModuleT::RegisterClassObjects](catlexemodulet-class.md#registerclassobjects).

##  <a name="atlcommodulerevokeclassobjects"></a>  AtlComModuleRevokeClassObjects

Esta función se invoca para quitar el generador o generadores de clases de la tabla de objetos en ejecución.

```
ATLINLINE ATLAPI AtlComModuleRevokeClassObjects(_ATL_COM_MODULE* pComModule);
```

### <a name="parameters"></a>Parámetros

*pComModule*<br/>
Puntero al módulo COM.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Esta función auxiliar utilizan [CComModule::RevokeClassObjects](ccommodule-class.md#revokeclassobjects) (obsoleto en ATL 7.0) y [CAtlExeModuleT::RevokeClassObjects](catlexemodulet-class.md#revokeclassobjects).

##  <a name="atlcommodulegetclassobject"></a>  AtlComModuleGetClassObject

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
IID de la interfaz solicitada.

*ppv*<br/>
Un puntero al puntero de interfaz identificado por *riid*. Si el objeto no admite esta interfaz, *ppv* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Esta función auxiliar utilizan [CComModule::GetClassObject](ccommodule-class.md#getclassobject) (obsoleto en ATL 7.0) y [CAtlDllModuleT::GetClassObject](catldllmodulet-class.md#getclassobject).

## <a name="see-also"></a>Vea también

[Funciones](../../atl/reference/atl-functions.md)
