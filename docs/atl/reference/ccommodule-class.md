---
title: CComModule (clase)
ms.date: 08/19/2019
f1_keywords:
- CComModule
- ATLBASE/ATL::CComModule
- ATLBASE/ATL::CComModule::GetClassObject
- ATLBASE/ATL::CComModule::GetModuleInstance
- ATLBASE/ATL::CComModule::GetResourceInstance
- ATLBASE/ATL::CComModule::GetTypeLibInstance
- ATLBASE/ATL::CComModule::Init
- ATLBASE/ATL::CComModule::RegisterClassHelper
- ATLBASE/ATL::CComModule::RegisterClassObjects
- ATLBASE/ATL::CComModule::RegisterServer
- ATLBASE/ATL::CComModule::RegisterTypeLib
- ATLBASE/ATL::CComModule::RevokeClassObjects
- ATLBASE/ATL::CComModule::Term
- ATLBASE/ATL::CComModule::UnregisterClassHelper
- ATLBASE/ATL::CComModule::UnregisterServer
- ATLBASE/ATL::CComModule::UpdateRegistryClass
- ATLBASE/ATL::CComModule::UpdateRegistryFromResourceD
- ATLBASE/ATL::CComModule::UpdateRegistryFromResourceS
- ATLBASE/ATL::CComModule::m_csObjMap
- ATLBASE/ATL::CComModule::m_csTypeInfoHolder
- ATLBASE/ATL::CComModule::m_csWindowCreate
- ATLBASE/ATL::CComModule::m_hInst
- ATLBASE/ATL::CComModule::m_hInstResource
- ATLBASE/ATL::CComModule::m_hInstTypeLib
- ATLBASE/ATL::CComModule::m_pObjMap
helpviewer_keywords:
- CComModule class
- DLL modules [C++], ATL
ms.assetid: f5face2c-8fd8-40e6-9ec3-54ab74701769
ms.openlocfilehash: 652c5f078ddbaf8d3e333f7003d6515a94dd8f83
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327757"
---
# <a name="ccommodule-class"></a>CComModule (clase)

A partir de ATL `CComModule` 7.0, está en desuso: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CComModule : public _ATL_MODULE
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComModule::GetClassObject](#getclassobject)|Crea un objeto de un CLSID especificado. Sólo para archivos DLL.|
|[CComModule::GetModuleInstance](#getmoduleinstance)|Devuelve `m_hInst`.|
|[CComModule::GetResourceInstance](#getresourceinstance)|Devuelve `m_hInstResource`.|
|[CComModule::GetTypeLibInstance](#gettypelibinstance)|Devuelve `m_hInstTypeLib`.|
|[CComModule::Init](#init)|Inicializa los miembros de datos.|
|[CComModule::RegisterClassHelper](#registerclasshelper)|Introduce el registro de claseestándar de un objeto en el registro del sistema.|
|[CComModule::RegisterClassObjects](#registerclassobjects)|Registra el objeto de clase. Sólo para EXEs.|
|[CComModule::RegisterServer](#registerserver)|Actualiza el registro del sistema para cada objeto del mapa de objetos.|
|[CComModule::RegisterTypeLib](#registertypelib)|Registra una biblioteca de tipos.|
|[CComModule::RevokeClassObjects](#revokeclassobjects)|Revoca el objeto de clase. Sólo para EXEs.|
|[CComModule::Term](#term)|Libera miembros de datos.|
|[CComModule::UnregisterClassHelper](#unregisterclasshelper)|Quita el registro de clase estándar de un objeto del registro del sistema.|
|[CComModule::UnregisterServer](#unregisterserver)|Anula el registro de cada objeto del mapa de objetos.|
|[CComModule::UpdateRegistryClass](#updateregistryclass)|Registra o anula el registro de clase estándar de un objeto.|
|[CComModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Ejecuta el script contenido en un recurso especificado para registrar o anular el registro de un objeto.|
|[CComModule::UpdateRegistryFromResources](#updateregistryfromresources)|Enlaces estáticos al componente de registro ATL. Ejecuta el script contenido en un recurso especificado para registrar o anular el registro de un objeto.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComModule::m_csObjMap](#m_csobjmap)|Garantiza el acceso sincronizado a la información del mapa de objetos.|
|[CComModule::m_csTypeInfoHolder](#m_cstypeinfoholder)|Garantiza el acceso sincronizado a la información de la biblioteca de tipos.|
|[CComModule::m_csWindowCreate](#m_cswindowcreate)|Garantiza el acceso sincronizado a la información de clase de ventana y a los datos estáticos utilizados durante la creación de ventanas.|
|[CComModule::m_hInst](#m_hinst)|Contiene el identificador de la instancia del módulo.|
|[CComModule::m_hInstResource](#m_hinstresource)|De forma predeterminada, contiene el identificador de la instancia del módulo.|
|[CComModule::m_hInstTypeLib](#m_hinsttypelib)|De forma predeterminada, contiene el identificador de la instancia del módulo.|
|[CComModule::m_pObjMap](#m_pobjmap)|Señala al mapa de objetos mantenido por la instancia del módulo.|

## <a name="remarks"></a>Observaciones

> [!NOTE]
> Esta clase está en desuso y los asistentes de generación de código ATL ahora usan las clases derivadas [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) y [CAtlModule.](../../atl/reference/catlmodule-class.md) Consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más información. La información siguiente es para su uso con aplicaciones creadas con versiones anteriores de ATL. `CComModule`sigue siendo parte de ATL para la capacidad hacia atrás.

`CComModule`implementa un módulo de servidor COM, lo que permite a un cliente acceder a los componentes del módulo. `CComModule`admite módulos DLL (en proceso) y EXE (local).

Una `CComModule` instancia utiliza un mapa de objetos para mantener un conjunto de definiciones de objetos de clase. Este mapa de objetos se `_ATL_OBJMAP_ENTRY` implementa como una matriz de estructuras y contiene información para:

- Introducir y eliminar descripciones de objetos en el registro del sistema.

- Creación de instancias de objetos a través de una fábrica de clases.

- Establecer la comunicación entre un cliente y el objeto raíz en el componente.

- Realizar la administración de la duración de los objetos de clase.

Al ejecutar ATL COM AppWizard, el `_Module`asistente genera `CComModule` automáticamente , una instancia global de o una clase derivada de ella. Para obtener más información sobre el Asistente para proyectos ATL, vea el artículo [Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md).

Además `CComModule`de , ATL proporciona [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), que implementa un módulo de modelo de apartamento para los servicios DE EX Y Windows. Derive el `CComAutoThreadModule` módulo de cuando desee crear objetos en varios apartamentos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CComModule`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="ccommodulegetclassobject"></a><a name="getclassobject"></a>CComModule::GetClassObject

A partir de ATL `CComModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Parámetros

*rclsid*<br/>
[en] El CLSID del objeto que se va a crear.

*riid*<br/>
[en] El IID de la interfaz solicitada.

*Ppv*<br/>
[fuera] Un puntero al puntero de interfaz identificado por *riid*. Si el objeto no admite esta interfaz, *ppv* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Crea un objeto del CLSID especificado y recupera un puntero de interfaz a este objeto.

`GetClassObject`solo está disponible para dll.

## <a name="ccommodulegetmoduleinstance"></a><a name="getmoduleinstance"></a>CComModule::GetModuleInstance

A partir de ATL `CComModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Valor devuelto

El HINSTANCE que identifica este módulo.

### <a name="remarks"></a>Observaciones

Devuelve [el](#m_hinst) m_hInst miembro de datos.

## <a name="ccommodulegetresourceinstance"></a><a name="getresourceinstance"></a>CComModule::GetResourceInstance

A partir de ATL `CComModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Valor devuelto

Una HINSTANCE.

### <a name="remarks"></a>Observaciones

Devuelve [el](#m_hinstresource) m_hInstResource miembro de datos.

## <a name="ccommodulegettypelibinstance"></a><a name="gettypelibinstance"></a>CComModule::GetTypeLibInstance

A partir de ATL `CComModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HINSTANCE GetTypeLibInstance() const throw();
```

### <a name="return-value"></a>Valor devuelto

Una HINSTANCE.

### <a name="remarks"></a>Observaciones

Devuelve el [m_hInstTypeLib](#m_hinsttypelib) miembro de datos.

## <a name="ccommoduleinit"></a><a name="init"></a>CComModule::Init

A partir de ATL `CComModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
[en] Puntero a una matriz de entradas de mapa de objetos.

*H*<br/>
[en] La HINSTANCE `DLLMain` pasó `WinMain`a o .

*plibid*<br/>
[en] Puntero al LIBID de la biblioteca de tipos asociada al proyecto.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Inicializa todos los miembros de datos.

## <a name="ccommodulem_csobjmap"></a><a name="m_csobjmap"></a>CComModule::m_csObjMap

A partir de ATL `CComModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
CRITICAL_SECTION m_csObjMap;
```

### <a name="remarks"></a>Observaciones

Garantiza el acceso sincronizado al mapa de objetos.

## <a name="ccommodulem_cstypeinfoholder"></a><a name="m_cstypeinfoholder"></a>CComModule::m_csTypeInfoHolder

A partir de ATL `CComModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
CRITICAL_SECTION m_csTypeInfoHolder;
```

### <a name="remarks"></a>Observaciones

Garantiza el acceso sincronizado a la biblioteca de tipos.

## <a name="ccommodulem_cswindowcreate"></a><a name="m_cswindowcreate"></a>CComModule::m_csWindowCreate

A partir de ATL `CComModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
CRITICAL_SECTION m_csWindowCreate;
```

### <a name="remarks"></a>Observaciones

Garantiza el acceso sincronizado a la información de clase de ventana y a los datos estáticos utilizados durante la creación de ventanas.

## <a name="ccommodulem_hinst"></a><a name="m_hinst"></a>CComModule::m_hInst

A partir de ATL `CComModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HINSTANCE m_hInst;
```

### <a name="remarks"></a>Observaciones

Contiene el identificador de la instancia del módulo.

El método [Init](#init) se establece en `m_hInst` el identificador pasado a `DLLMain` o `WinMain`.

## <a name="ccommodulem_hinstresource"></a><a name="m_hinstresource"></a>CComModule::m_hInstResource

A partir de ATL `CComModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HINSTANCE m_hInstResource;
```

### <a name="remarks"></a>Observaciones

De forma predeterminada, contiene el identificador de la instancia del módulo.

El método [Init](#init) se establece en `m_hInstResource` el identificador pasado a `DLLMain` o `WinMain`. Puede establecer `m_hInstResource` explícitamente en el identificador de un recurso.

El método [GetResourceInstance](#getresourceinstance) devuelve `m_hInstResource`el identificador almacenado en .

## <a name="ccommodulem_hinsttypelib"></a><a name="m_hinsttypelib"></a>CComModule::m_hInstTypeLib

A partir de ATL `CComModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HINSTANCE m_hInstTypeLib;
```

### <a name="remarks"></a>Observaciones

De forma predeterminada, contiene el identificador de la instancia del módulo.

El método [Init](#init) se establece en `m_hInstTypeLib` el identificador pasado a `DLLMain` o `WinMain`. Puede establecer `m_hInstTypeLib` explícitamente en el identificador en una biblioteca de tipos.

El método [GetTypeLibInstance](#gettypelibinstance) devuelve `m_hInstTypeLib`el identificador almacenado en .

## <a name="ccommodulem_pobjmap"></a><a name="m_pobjmap"></a>CComModule::m_pObjMap

A partir de ATL `CComModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```

### <a name="remarks"></a>Observaciones

Señala al mapa de objetos mantenido por la instancia del módulo.

## <a name="ccommoduleregisterclasshelper"></a><a name="registerclasshelper"></a>CComModule::RegisterClassHelper

A partir de ATL `CComModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
ATL_DEPRECATED HRESULT RegisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags);
```

### <a name="parameters"></a>Parámetros

*clsid*<br/>
[en] EL CLSID del objeto que se va a registrar.

*lpszProgID*<br/>
[en] El ProgID asociado al objeto.

*lpszVerIndProgID*<br/>
[en] El ProgID independiente de la versión asociado al objeto.

*nDescID*<br/>
[en] Identificador de un recurso de cadena para la descripción del objeto.

*dwFlags*<br/>
[en] Especifica el modelo de subprocesamiento que se va a escribir en el registro. Los valores posibles son THREADFLAGS_APARTMENT, THREADFLAGS_BOTH o AUTPRXFLAG.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Introduce el registro de claseestándar de un objeto en el registro del sistema.

El método [UpdateRegistryClass](#updateregistryclass) llama al `RegisterClassHelper`método .

## <a name="ccommoduleregisterclassobjects"></a><a name="registerclassobjects"></a>CComModule::RegisterClassObjects

A partir de ATL `CComModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>Parámetros

*dwClsContext*<br/>
[en] Especifica el contexto en el que se va a ejecutar el objeto de clase. Los valores posibles son CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER o CLSCTX_LOCAL_SERVER. Para obtener una descripción de estos valores, vea [CLSCTX](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx) en el Windows SDK.

*dwFlags*<br/>
[en] Determina los tipos de conexión al objeto de clase. Los valores posibles son REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE o REGCLS_MULTI_SEPARATE. Para obtener una descripción de estos valores, vea [REGCLS](/windows/win32/api/combaseapi/ne-combaseapi-regcls) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Registra un objeto de clase EXE con OLE para que otras aplicaciones puedan conectarse a él. Este método solo está disponible para los EXE.

## <a name="ccommoduleregisterserver"></a><a name="registerserver"></a>CComModule::RegisterServer

A partir de ATL `CComModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*bRegTypeLib*<br/>
[en] Indica si se registrará la biblioteca de tipos. El valor predeterminado es FALSE.

*pCLSID*<br/>
[en] Señala al CLSID del objeto que se va a registrar. Si NULL (el valor predeterminado), se registrarán todos los objetos del mapa de objetos.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Según el parámetro *pCLSID,* actualiza el registro del sistema para un único objeto de clase o para todos los objetos del mapa de objetos.

Si *bRegTypeLib* es TRUE, la información de la biblioteca de tipos también se actualizará.

Consulte [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) para obtener información sobre cómo agregar una entrada al mapa de objetos.

`RegisterServer`se llamará automáticamente `DLLRegisterServer` por un `WinMain` archivo DLL o `/RegServer` por una ejecución EXE con la opción de línea de comandos.

## <a name="ccommoduleregistertypelib"></a><a name="registertypelib"></a>CComModule::RegisterTypeLib

A partir de ATL `CComModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```

### <a name="parameters"></a>Parámetros

*lpszIndex*<br/>
[en] String en `"\\N"`el `N` formato , donde está el índice entero del recurso TYPELIB.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Agrega información sobre una biblioteca de tipos al registro del sistema.

Si la instancia del módulo contiene varias bibliotecas de tipos, utilice la segunda versión de este método para especificar qué biblioteca de tipos se debe utilizar.

## <a name="ccommodulerevokeclassobjects"></a><a name="revokeclassobjects"></a>CComModule::RevokeClassObjects

A partir de ATL `CComModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Quita el objeto de clase. Este método solo está disponible para los EXE.

## <a name="ccommoduleterm"></a><a name="term"></a>CComModule::Term

A partir de ATL `CComModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
void Term() throw();
```

### <a name="remarks"></a>Observaciones

Libera todos los miembros de datos.

## <a name="ccommoduleunregisterclasshelper"></a><a name="unregisterclasshelper"></a>CComModule::UnregisterClassHelper

A partir de ATL `CComModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
ATL_DEPRECATED HRESULT UnregisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```

### <a name="parameters"></a>Parámetros

*clsid*<br/>
[en] EL CLSID del objeto que se va a anular el registro.

*lpszProgID*<br/>
[en] El ProgID asociado al objeto.

*lpszVerIndProgID*<br/>
[en] El ProgID independiente de la versión asociado al objeto.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Quita el registro de clase estándar de un objeto del registro del sistema.

El método [UpdateRegistryClass](#updateregistryclass) llama al `UnregisterClassHelper`método .

## <a name="ccommoduleunregisterserver"></a><a name="unregisterserver"></a>CComModule::UnregisterServer

A partir de ATL `CComModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```

### <a name="parameters"></a>Parámetros

*bUnRegTypeLib*<br/>
Si es TRUE, la biblioteca de tipos también está sin registrar.

*pCLSID*<br/>
Señala al CLSID del objeto que se va a anular el registro. Si NULL (el valor predeterminado), todos los objetos del mapa de objetos se anularán el registro.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Según el parámetro *pCLSID,* anula el registro de un único objeto de clase o de todos los objetos del mapa de objetos.

`UnregisterServer`se llamará automáticamente `DLLUnregisterServer` por un `WinMain` archivo DLL o `/UnregServer` por una ejecución EXE con la opción de línea de comandos.

Consulte [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) para obtener información sobre cómo agregar una entrada al mapa de objetos.

## <a name="ccommoduleupdateregistryclass"></a><a name="updateregistryclass"></a>CComModule::UpdateRegistryClass

A partir de ATL `CComModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
ATL_DEPRECATED HRESULT UpdateRegistryClass(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags,
    BOOL bRegister);

ATL_DEPRECATED HRESULT UpdateRegistryClass(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    LPCTSTR szDesc,
    DWORD dwFlags,
    BOOL bRegister);
```

### <a name="parameters"></a>Parámetros

*clsid*<br/>
EL CLSID del objeto que se va a registrar o anular el registro.

*lpszProgID*<br/>
El ProgID asociado al objeto.

*lpszVerIndProgID*<br/>
El ProgID independiente de la versión asociado al objeto.

*nDescID*<br/>
Identificador del recurso de cadena para la descripción del objeto.

*szDesc*<br/>
Cadena que contiene la descripción del objeto.

*dwFlags*<br/>
Especifica el modelo de subprocesamiento que se va a escribir en el registro. Los valores posibles son THREADFLAGS_APARTMENT, THREADFLAGS_BOTH o AUTPRXFLAG.

*bRegistro*<br/>
Indica si se debe registrar el objeto.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Si *bRegister* es TRUE, este método escribe el registro de clase estándar del objeto en el registro del sistema.

Si *bRegister* es FALSE, quita el registro del objeto.

En función del valor `UpdateRegistryClass` de *bRegister*, llama a [RegisterClassHelper](#registerclasshelper) o [UnregisterClassHelper](#unregisterclasshelper).

Al especificar la macro `UpdateRegistryClass` [DECLARE_REGISTRY,](registry-macros.md#declare_registry) se invocará automáticamente cuando se procese el mapa de objetos.

## <a name="ccommoduleupdateregistryfromresourced"></a><a name="updateregistryfromresourced"></a>CComModule::UpdateRegistryFromResourceD

A partir de ATL `CComModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
virtual HRESULT UpdateRegistryFromResourceD(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

virtual HRESULT UpdateRegistryFromResourceD(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw ();
```

### <a name="parameters"></a>Parámetros

*lpszRes*<br/>
[en] Un nombre de recurso.

*nResID*<br/>
[en] Un identificador de recurso.

*bRegistro*<br/>
[en] Indica si se debe registrar el objeto.

*pMapEntries*<br/>
[en] Puntero al mapa de reemplazo que almacena los valores asociados con los parámetros reemplazables del script. ATL utiliza `%MODULE%`automáticamente . Para utilizar parámetros reemplazables adicionales, consulte Comentarios para obtener más información. De lo contrario, use el valor predeterminado NULL.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Ejecuta el script contenido en el recurso especificado por *lpszRes* o *nResID*.

Si *bRegister* es TRUE, este método registra el objeto en el registro del sistema; de lo contrario, anula el registro del objeto.

Al especificar la [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) o `UpdateRegistryFromResourceD` [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) macro, se invocará automáticamente cuando se procese el mapa de objetos.

> [!NOTE]
> Para sustituir los valores de sustitución en tiempo de ejecución, no especifique la macro DECLARE_REGISTRY_RESOURCE o DECLARE_REGISTRY_RESOURCEID. En su lugar, `_ATL_REGMAP_ENTRIES` cree una matriz de estructuras, donde cada entrada contiene un marcador de posición variable emparejado con un valor para reemplazar el marcador de posición en tiempo de ejecución. A `UpdateRegistryFromResourceD`continuación, llame a , pasando la matriz para el *pMapEntries* parámetro. Esto agrega todos los valores `_ATL_REGMAP_ENTRIES` de reemplazo en las estructuras al mapa de reemplazo del registrador.

> [!NOTE]
> Para vincular estáticamente al componente de registro ATL (Registrar), vea [UpdateRegistryFromResourceS](#updateregistryfromresources).

Para obtener más información acerca de los parámetros reemplazables y el scripting, consulte el artículo [Componente del Registro ATL (Registrar).](../../atl/atl-registry-component-registrar.md)

## <a name="ccommoduleupdateregistryfromresources"></a><a name="updateregistryfromresources"></a>CComModule::UpdateRegistryFromResources

A partir de ATL `CComModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
virtual HRESULT UpdateRegistryFromResourceS(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

virtual HRESULT UpdateRegistryFromResourceS(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*lpszRes*<br/>
[en] Un nombre de recurso.

*nResID*<br/>
[en] Un identificador de recurso.

*bRegistro*<br/>
[en] Indica si se debe registrar el script de recursos.

*pMapEntries*<br/>
[en] Puntero al mapa de reemplazo que almacena los valores asociados con los parámetros reemplazables del script. ATL utiliza `%MODULE%`automáticamente . Para utilizar parámetros reemplazables adicionales, consulte Comentarios para obtener más información. De lo contrario, use el valor predeterminado NULL.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Similar a [UpdateRegistryFromResourceD](#updateregistryfromresourced) excepto `UpdateRegistryFromResourceS` crea un vínculo estático al componente de registro ATL (Registrar).

`UpdateRegistryFromResourceS`Se invocará automáticamente cuando se procese `#define _ATL_STATIC_REGISTRY` el mapa de objetos, siempre que agregue a su *pch.h* *(stdafx.h* en Visual Studio 2017 y versiones anteriores).

> [!NOTE]
> Para sustituir los valores de sustitución en tiempo de ejecución, no especifique la [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) o [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) macro. En su lugar, `_ATL_REGMAP_ENTRIES` cree una matriz de estructuras, donde cada entrada contiene un marcador de posición variable emparejado con un valor para reemplazar el marcador de posición en tiempo de ejecución. A `UpdateRegistryFromResourceS`continuación, llame a , pasando la matriz para el *pMapEntries* parámetro. Esto agrega todos los valores `_ATL_REGMAP_ENTRIES` de reemplazo en las estructuras al mapa de reemplazo del registrador.

Para obtener más información acerca de los parámetros reemplazables y el scripting, consulte el artículo [Componente del Registro ATL (Registrar).](../../atl/atl-registry-component-registrar.md)

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
