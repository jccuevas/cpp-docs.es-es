---
title: Clase CAtlDllModulet
ms.date: 11/04/2016
f1_keywords:
- CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::DllCanUnloadNow
- ATLBASE/ATL::CAtlDllModuleT::DllGetClassObject
- ATLBASE/ATL::CAtlDllModuleT::DllMain
- ATLBASE/ATL::CAtlDllModuleT::DllRegisterServer
- ATLBASE/ATL::CAtlDllModuleT::DllUnregisterServer
- ATLBASE/ATL::CAtlDllModuleT::GetClassObject
helpviewer_keywords:
- CAtlDllModuleT class
ms.assetid: 351d5767-8257-4878-94be-45a85e31a72d
ms.openlocfilehash: 7a5f8e7e489c8e0d573569ac7c4a8fb63f652732
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319011"
---
# <a name="catldllmodulet-class"></a>Clase CAtlDllModulet

Esta clase representa el módulo para un archivo DLL.

## <a name="syntax"></a>Sintaxis

```
template <class T>
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada `CAtlDllModuleT`de .

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtldllModulet::CAtlDllModuleT](#catldllmodulet)|El constructor.|
|[CAtlDllModulet::-CAtlDllModuleT](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlDllModuleT::DllCanUnloadNow](#dllcanunloadnow)|Comprueba si se puede descargar el archivo DLL.|
|[CAtlDllModuleT::DllGetClassObject](#dllgetclassobject)|Devuelve un generador de clases.|
|[CAtlDllModuleT::DllMain](#dllmain)|El punto de entrada opcional en una biblioteca de vínculos dinámicos (DLL).|
|[CAtlDllModuleT::DllRegisterServer](#dllregisterserver)|Agrega entradas al registro del sistema para los objetos del archivo DLL.|
|[CAtlDllModuleT::DllUnregisterServer](#dllunregisterserver)|Quita las entradas del registro del sistema para los objetos del archivo DLL.|
|[CAtlDllModuleT::GetClassObject](#getclassobject)|Devuelve un generador de clases. Invoked by [DllGetClassObject](#dllgetclassobject).|

## <a name="remarks"></a>Observaciones

`CAtlDllModuleT`representa el módulo de una biblioteca de vínculos dinámicos (DLL) y proporciona funciones utilizadas por todos los proyectos DLL. Esta especialización de la clase [CAtlModuleT](../../atl/reference/catlmodulet-class.md) incluye compatibilidad con el registro.

Para obtener más información sobre los módulos de ATL, consulte Clases de [módulo ATL](../../atl/atl-module-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlDllModuleT`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="catldllmoduletcatldllmodulet"></a><a name="catldllmodulet"></a>CAtldllModulet::CAtlDllModuleT

El constructor.

```
CAtlDllModuleT() throw();
```

## <a name="catldllmoduletcatldllmodulet"></a><a name="dtor"></a>CAtlDllModulet::-CAtlDllModuleT

Destructor.

```
~CAtlDllModuleT() throw();
```

## <a name="catldllmoduletdllcanunloadnow"></a><a name="dllcanunloadnow"></a>CAtlDllModuleT::DllCanUnloadNow

Comprueba si se puede descargar el archivo DLL.

```
HRESULT DllCanUnloadNow() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si el archivo DLL se puede descargar o S_FALSE si no se puede.

## <a name="catldllmoduletdllgetclassobject"></a><a name="dllgetclassobject"></a>CAtlDllModuleT::DllGetClassObject

Devuelve el generador de clases.

```
HRESULT DllGetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Parámetros

*rclsid*<br/>
El CLSID del objeto que se va a crear.

*riid*<br/>
El IID de la interfaz solicitada.

*Ppv*<br/>
Un puntero al puntero de interfaz identificado por *riid*. Si el objeto no admite esta interfaz, *ppv* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="catldllmoduletdllmain"></a><a name="dllmain"></a>CAtlDllModuleT::DllMain

El punto de entrada opcional en una biblioteca de vínculos dinámicos (DLL).

```
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```

### <a name="parameters"></a>Parámetros

*dwReason*<br/>
Si se establece en DLL_PROCESS_ATTACH, las llamadas de notificación DLL_THREAD_ATTACH y DLL_THREAD_DETACH están deshabilitadas.

*lpReserved*<br/>
Reservado.

### <a name="return-value"></a>Valor devuelto

Siempre devuelve TRUE.

### <a name="remarks"></a>Observaciones

Deshabilitar las llamadas de notificación DLL_THREAD_ATTACH y DLL_THREAD_DETACH puede ser una optimización útil para aplicaciones multiproceso que tienen muchos archivos DLL, que con frecuencia crean y eliminan subprocesos y cuyos archivos DLL no necesitan estas notificaciones de nivel de subproceso de datos adjuntos o desapego.

## <a name="catldllmoduletdllregisterserver"></a><a name="dllregisterserver"></a>CAtlDllModuleT::DllRegisterServer

Agrega entradas al registro del sistema para los objetos del archivo DLL.

```
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Parámetros

*bRegTypeLib*<br/>
TRUESi se va a registrar la biblioteca de tipos. El valor predeterminado es TRUE.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="catldllmoduletdllunregisterserver"></a><a name="dllunregisterserver"></a>CAtlDllModuleT::DllUnregisterServer

Quita las entradas del registro del sistema para los objetos del archivo DLL.

```
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Parámetros

*bUnRegTypeLib*<br/>
TRUESi la biblioteca de tipos se va a quitar del registro. El valor predeterminado es TRUE.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="catldllmoduletgetclassobject"></a><a name="getclassobject"></a>CAtlDllModuleT::GetClassObject

Crea un objeto del CLSID especificado.

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Parámetros

*rclsid*<br/>
El CLSID del objeto que se va a crear.

*riid*<br/>
El IID de la interfaz solicitada.

*Ppv*<br/>
Un puntero al puntero de interfaz identificado por *riid*. Si el objeto no admite esta interfaz, *ppv* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

[CAtlDllModuleT::DllGetClassObject](#dllgetclassobject) llama a este método y se incluye por compatibilidad con versiones anteriores.

## <a name="see-also"></a>Consulte también

[Clase CAtlModuleT](../../atl/reference/catlmodulet-class.md)<br/>
[Clase CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clases de módulo](../../atl/atl-module-classes.md)
