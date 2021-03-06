---
title: Clase CAtlDllModuleT
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
ms.openlocfilehash: e0896a28c24877465213a71ac5207c537c731003
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168777"
---
# <a name="catldllmodulet-class"></a>Clase CAtlDllModuleT

Esta clase representa el módulo para un archivo DLL.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `CAtlDllModuleT`.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlDllModuleT:: CAtlDllModuleT](#catldllmodulet)|El constructor.|
|[CAtlDllModuleT:: ~ CAtlDllModuleT](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlDllModuleT::D llCanUnloadNow](#dllcanunloadnow)|Comprueba si se puede descargar el archivo DLL.|
|[CAtlDllModuleT::D llGetClassObject](#dllgetclassobject)|Devuelve un generador de clases.|
|[CAtlDllModuleT::D llMain](#dllmain)|El punto de entrada opcional en una biblioteca de vínculos dinámicos (DLL).|
|[CAtlDllModuleT::D llRegisterServer](#dllregisterserver)|Agrega entradas al registro del sistema para los objetos de la DLL.|
|[CAtlDllModuleT::D llUnregisterServer](#dllunregisterserver)|Quita las entradas del registro del sistema para los objetos de la DLL.|
|[CAtlDllModuleT:: Getclassobject (](#getclassobject)|Devuelve un generador de clases. Invocado por [DllGetClassObject](#dllgetclassobject).|

## <a name="remarks"></a>Observaciones

`CAtlDllModuleT`representa el módulo para una biblioteca de vínculos dinámicos (DLL) y proporciona funciones utilizadas por todos los proyectos DLL. Esta especialización de la clase [CAtlModuleT](../../atl/reference/catlmodulet-class.md) incluye compatibilidad con el registro.

Para obtener más información sobre los módulos de ATL, vea [clases de módulo ATL](../../atl/atl-module-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlDllModuleT`

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

## <a name="catldllmoduletcatldllmodulet"></a><a name="catldllmodulet"></a>CAtlDllModuleT:: CAtlDllModuleT

El constructor.

```cpp
CAtlDllModuleT() throw();
```

## <a name="catldllmoduletcatldllmodulet"></a><a name="dtor"></a>CAtlDllModuleT:: ~ CAtlDllModuleT

Destructor.

```cpp
~CAtlDllModuleT() throw();
```

## <a name="catldllmoduletdllcanunloadnow"></a><a name="dllcanunloadnow"></a>CAtlDllModuleT::D llCanUnloadNow

Comprueba si se puede descargar el archivo DLL.

```cpp
HRESULT DllCanUnloadNow() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se puede descargar el archivo DLL o S_FALSE si no lo es.

## <a name="catldllmoduletdllgetclassobject"></a><a name="dllgetclassobject"></a>CAtlDllModuleT::D llGetClassObject

Devuelve el generador de clases.

```cpp
HRESULT DllGetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Parámetros

*rclsid*<br/>
CLSID del objeto que se va a crear.

*riid*<br/>
IID de la interfaz solicitada.

*PPV*<br/>
Puntero al puntero de interfaz identificado por *riid*. Si el objeto no admite esta interfaz, *PPV* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

## <a name="catldllmoduletdllmain"></a><a name="dllmain"></a>CAtlDllModuleT::D llMain

El punto de entrada opcional en una biblioteca de vínculos dinámicos (DLL).

```cpp
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```

### <a name="parameters"></a>Parámetros

*dwReason*<br/>
Si se establece en DLL_PROCESS_ATTACH, se deshabilitan las llamadas a las notificaciones de DLL_THREAD_ATTACH y DLL_THREAD_DETACH.

*lpReserved*<br/>
Reservado.

### <a name="return-value"></a>Valor devuelto

Siempre devuelve TRUE.

### <a name="remarks"></a>Observaciones

Deshabilitar las llamadas de notificación de DLL_THREAD_ATTACH y DLL_THREAD_DETACH puede ser una optimización útil para las aplicaciones multiproceso que tienen muchos archivos dll, que suelen crear y eliminar subprocesos, y cuyos archivos dll no necesitan estas notificaciones de nivel de subproceso de datos adjuntos o desasociación.

## <a name="catldllmoduletdllregisterserver"></a><a name="dllregisterserver"></a>CAtlDllModuleT::D llRegisterServer

Agrega entradas al registro del sistema para los objetos de la DLL.

```cpp
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Parámetros

*bRegTypeLib*<br/>
TRUE si se va a registrar la biblioteca de tipos. El valor predeterminado es TRUE.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

## <a name="catldllmoduletdllunregisterserver"></a><a name="dllunregisterserver"></a>CAtlDllModuleT::D llUnregisterServer

Quita las entradas del registro del sistema para los objetos de la DLL.

```cpp
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Parámetros

*bUnRegTypeLib*<br/>
TRUE si la biblioteca de tipos se va a quitar del registro. El valor predeterminado es TRUE.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

## <a name="catldllmoduletgetclassobject"></a><a name="getclassobject"></a>CAtlDllModuleT:: Getclassobject (

Crea un objeto del CLSID especificado.

```cpp
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Parámetros

*rclsid*<br/>
CLSID del objeto que se va a crear.

*riid*<br/>
IID de la interfaz solicitada.

*PPV*<br/>
Puntero al puntero de interfaz identificado por *riid*. Si el objeto no admite esta interfaz, *PPV* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Este método es llamado por [CAtlDllModuleT::D llgetclassobject](#dllgetclassobject) y se incluye por compatibilidad con versiones anteriores.

## <a name="see-also"></a>Consulte también

[Clase CAtlModuleT](../../atl/reference/catlmodulet-class.md)<br/>
[Clase CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clases de módulo](../../atl/atl-module-classes.md)
