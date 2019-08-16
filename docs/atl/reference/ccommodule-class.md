---
title: CComModule (clase)
ms.date: 11/04/2016
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
ms.openlocfilehash: 53138081a6d712f775a2cc8f1e6905c45d95d34d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497114"
---
# <a name="ccommodule-class"></a>CComModule (clase)

A partir de ATL 7,0 `CComModule` , está en desuso: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CComModule : public _ATL_MODULE
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComModule::GetClassObject](#getclassobject)|Crea un objeto de un CLSID especificado. Solo para archivos dll.|
|[CComModule::GetModuleInstance](#getmoduleinstance)|Devuelve `m_hInst`.|
|[CComModule::GetResourceInstance](#getresourceinstance)|Devuelve `m_hInstResource`.|
|[CComModule::GetTypeLibInstance](#gettypelibinstance)|Devuelve `m_hInstTypeLib`.|
|[CComModule::Init](#init)|Inicializa los miembros de datos.|
|[CComModule::RegisterClassHelper](#registerclasshelper)|Escribe el registro de clase estándar de un objeto en el registro del sistema.|
|[CComModule::RegisterClassObjects](#registerclassobjects)|Registra el objeto de clase. Solo para archivos exe.|
|[CComModule::RegisterServer](#registerserver)|Actualiza el registro del sistema para cada objeto del mapa de objetos.|
|[CComModule::RegisterTypeLib](#registertypelib)|Registra una biblioteca de tipos.|
|[CComModule::RevokeClassObjects](#revokeclassobjects)|Revoca el objeto de clase. Solo para archivos exe.|
|[CComModule::Term](#term)|Libera los miembros de datos.|
|[CComModule::UnregisterClassHelper](#unregisterclasshelper)|Quita el registro de clase estándar de un objeto del registro del sistema.|
|[CComModule::UnregisterServer](#unregisterserver)|Anula el registro de cada objeto en el mapa de objetos.|
|[CComModule::UpdateRegistryClass](#updateregistryclass)|Registra o anula el registro del registro de clase estándar de un objeto.|
|[CComModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Ejecuta el script contenido en un recurso especificado para registrar o anular el registro de un objeto.|
|[CComModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|Vincula estáticamente al componente del registro ATL. Ejecuta el script contenido en un recurso especificado para registrar o anular el registro de un objeto.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComModule::m_csObjMap](#m_csobjmap)|Garantiza el acceso sincronizado a la información del mapa de objetos.|
|[CComModule::m_csTypeInfoHolder](#m_cstypeinfoholder)|Garantiza el acceso sincronizado a la información de la biblioteca de tipos.|
|[CComModule::m_csWindowCreate](#m_cswindowcreate)|Garantiza el acceso sincronizado a la información de clase de ventana y a los datos estáticos que se usan durante la creación de la ventana.|
|[CComModule::m_hInst](#m_hinst)|Contiene el identificador de la instancia del módulo.|
|[CComModule::m_hInstResource](#m_hinstresource)|De forma predeterminada, contiene el identificador de la instancia de módulo.|
|[CComModule::m_hInstTypeLib](#m_hinsttypelib)|De forma predeterminada, contiene el identificador de la instancia de módulo.|
|[CComModule::m_pObjMap](#m_pobjmap)|Apunta a la asignación de objetos mantenida por la instancia del módulo.|

## <a name="remarks"></a>Comentarios

> [!NOTE]
>  Esta clase está en desuso y los asistentes de generación de código ATL usan las clases derivadas [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) y [CAtlModule](../../atl/reference/catlmodule-class.md) . Vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más información. La información siguiente es para su uso con las aplicaciones creadas con versiones anteriores de ATL. `CComModule`sigue siendo parte de ATL para la funcionalidad de versiones anteriores.

`CComModule`implementa un módulo de servidor COM, lo que permite que un cliente tenga acceso a los componentes del módulo. `CComModule`admite los módulos DLL (en proceso) y EXE (local).

Una `CComModule` instancia de utiliza un mapa de objetos para mantener un conjunto de definiciones de objetos de clase. Este mapa de objetos se implementa como una matriz `_ATL_OBJMAP_ENTRY` de estructuras y contiene información de:

- Escribir y quitar descripciones de objetos en el registro del sistema.

- Crear instancias de objetos a través de un generador de clases.

- Establecer la comunicación entre un cliente y el objeto raíz en el componente.

- Realizar la administración de la duración de los objetos de clase.

Cuando se ejecuta ATL com AppWizard, el asistente genera `_Module`automáticamente una instancia global de `CComModule` o una clase derivada de ella. Para obtener más información sobre el Asistente para proyectos ATL, vea el artículo [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md).

Además `CComModule`de, ATL proporciona [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), que implementa un módulo de modelo de apartamento para los servicios exe y Windows. Derive el módulo de `CComAutoThreadModule` cuando desee crear objetos en varios apartamentos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CComModule`

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

##  <a name="getclassobject"></a>  CComModule::GetClassObject

A partir de ATL 7,0 `CComModule` , está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Parámetros

*rclsid*<br/>
de CLSID del objeto que se va a crear.

*riid*<br/>
de IID de la interfaz solicitada.

*ppv*<br/>
enuncia Puntero al puntero de interfaz identificado por *riid*. Si el objeto no admite esta interfaz, *PPV* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Crea un objeto del CLSID especificado y recupera un puntero de interfaz a este objeto.

`GetClassObject`solo está disponible para los archivos dll.

##  <a name="getmoduleinstance"></a>  CComModule::GetModuleInstance

A partir de ATL 7,0 `CComModule` , está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Valor devuelto

HINSTANCE que identifica este módulo.

### <a name="remarks"></a>Comentarios

Devuelve el miembro de datos [m_hInst](#m_hinst) .

##  <a name="getresourceinstance"></a>  CComModule::GetResourceInstance

A partir de ATL 7,0 `CComModule` , está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Valor devuelto

HINSTANCE.

### <a name="remarks"></a>Comentarios

Devuelve el miembro de datos [m_hInstResource](#m_hinstresource) .

##  <a name="gettypelibinstance"></a>  CComModule::GetTypeLibInstance

A partir de ATL 7,0 `CComModule` , está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HINSTANCE GetTypeLibInstance() const throw();
```

### <a name="return-value"></a>Valor devuelto

HINSTANCE.

### <a name="remarks"></a>Comentarios

Devuelve el miembro de datos [m_hInstTypeLib](#m_hinsttypelib) .

##  <a name="init"></a>  CComModule::Init

A partir de ATL 7,0 `CComModule` , está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
de Puntero a una matriz de entradas de asignación de objetos.

*h*<br/>
de HInstance que se pasa `DLLMain` a `WinMain`o.

*plibid*<br/>
de Puntero al LIBId de la biblioteca de tipos asociada al proyecto.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Inicializa todos los miembros de datos.

##  <a name="m_csobjmap"></a>  CComModule::m_csObjMap

A partir de ATL 7,0 `CComModule` , está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
CRITICAL_SECTION m_csObjMap;
```

### <a name="remarks"></a>Comentarios

Garantiza el acceso sincronizado al mapa de objetos.

##  <a name="m_cstypeinfoholder"></a>  CComModule::m_csTypeInfoHolder

A partir de ATL 7,0 `CComModule` , está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
CRITICAL_SECTION m_csTypeInfoHolder;
```

### <a name="remarks"></a>Comentarios

Garantiza el acceso sincronizado a la biblioteca de tipos.

##  <a name="m_cswindowcreate"></a>  CComModule::m_csWindowCreate

A partir de ATL 7,0 `CComModule` , está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
CRITICAL_SECTION m_csWindowCreate;
```

### <a name="remarks"></a>Comentarios

Garantiza el acceso sincronizado a la información de la clase de ventana y a los datos estáticos que se usan durante la creación de la ventana.

##  <a name="m_hinst"></a>  CComModule::m_hInst

A partir de ATL 7,0 `CComModule` , está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HINSTANCE m_hInst;
```

### <a name="remarks"></a>Comentarios

Contiene el identificador de la instancia del módulo.

El método [init](#init) establece `m_hInst` en el identificador que se pasa `WinMain`a `DLLMain` o.

##  <a name="m_hinstresource"></a>  CComModule::m_hInstResource

A partir de ATL 7,0 `CComModule` , está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HINSTANCE m_hInstResource;
```

### <a name="remarks"></a>Comentarios

De forma predeterminada, contiene el identificador de la instancia de módulo.

El método [init](#init) establece `m_hInstResource` en el identificador que se pasa `WinMain`a `DLLMain` o. Puede establecer `m_hInstResource` explícitamente en el identificador de un recurso.

El método [GetResourceInstance](#getresourceinstance) devuelve el identificador almacenado en `m_hInstResource`.

##  <a name="m_hinsttypelib"></a>  CComModule::m_hInstTypeLib

A partir de ATL 7,0 `CComModule` , está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HINSTANCE m_hInstTypeLib;
```

### <a name="remarks"></a>Comentarios

De forma predeterminada, contiene el identificador de la instancia de módulo.

El método [init](#init) establece `m_hInstTypeLib` en el identificador que se pasa `WinMain`a `DLLMain` o. Puede establecer `m_hInstTypeLib` explícitamente en el identificador de una biblioteca de tipos.

El método [GetTypeLibInstance](#gettypelibinstance) devuelve el identificador almacenado en `m_hInstTypeLib`.

##  <a name="m_pobjmap"></a>  CComModule::m_pObjMap

A partir de ATL 7,0 `CComModule` , está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```

### <a name="remarks"></a>Comentarios

Apunta a la asignación de objetos mantenida por la instancia del módulo.

##  <a name="registerclasshelper"></a>  CComModule::RegisterClassHelper

A partir de ATL 7,0 `CComModule` , está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

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
de CLSID del objeto que se va a registrar.

*lpszProgID*<br/>
de Identificador de programa (ProgID) asociado al objeto.

*lpszVerIndProgID*<br/>
de ProgID independiente de la versión asociado al objeto.

*nDescID*<br/>
de Identificador de un recurso de cadena para la descripción del objeto.

*dwFlags*<br/>
de Especifica el modelo de subprocesos que se va a especificar en el registro. Los valores posibles son THREADFLAGS_APARTMENT, THREADFLAGS_BOTH o AUTPRXFLAG.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Escribe el registro de clase estándar de un objeto en el registro del sistema.

El método [UpdateRegistryClass](#updateregistryclass) llama `RegisterClassHelper`a.

##  <a name="registerclassobjects"></a>  CComModule::RegisterClassObjects

A partir de ATL 7,0 `CComModule` , está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>Parámetros

*dwClsContext*<br/>
de Especifica el contexto en el que se va a ejecutar el objeto de clase. Los valores posibles son CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER o CLSCTX_LOCAL_SERVER. Para obtener una descripción de estos valores, consulte [CLSCTX](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx) en el Windows SDK.

*dwFlags*<br/>
de Determina los tipos de conexión para el objeto de clase. Los valores posibles son REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE o REGCLS_MULTI_SEPARATE. Para obtener una descripción de estos valores, consulte [REGCLS](/windows/win32/api/combaseapi/ne-combaseapi-regcls) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Registra un objeto de clase EXE con OLE para que otras aplicaciones puedan conectarse a él. Este método solo está disponible para los archivos exe.

##  <a name="registerserver"></a>  CComModule::RegisterServer

A partir de ATL 7,0 `CComModule` , está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*bRegTypeLib*<br/>
de Indica si se va a registrar la biblioteca de tipos. El valor predeterminado es FALSE.

*pCLSID*<br/>
de Apunta al CLSID del objeto que se va a registrar. Si es NULL (valor predeterminado), se registrarán todos los objetos del mapa de objetos.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Dependiendo del parámetro *pCLSID* , actualiza el registro del sistema para un objeto de una sola clase o para todos los objetos del mapa de objetos.

Si *bRegTypeLib* es true, también se actualizará la información de la biblioteca de tipos.

Consulte [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) para obtener información sobre cómo agregar una entrada al mapa de objetos.

`RegisterServer`se llamará automáticamente `DLLRegisterServer` a para un archivo dll `WinMain` o para una ejecución de exe con `/RegServer` la opción de línea de comandos.

##  <a name="registertypelib"></a>  CComModule::RegisterTypeLib

A partir de ATL 7,0 `CComModule` , está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```

### <a name="parameters"></a>Parámetros

*lpszIndex*<br/>
de Cadena con el formato `"\\N"`, donde `N` es el índice entero del recurso typelib.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Agrega información sobre una biblioteca de tipos al registro del sistema.

Si la instancia del módulo contiene varias bibliotecas de tipos, utilice la segunda versión de este método para especificar la biblioteca de tipos que se debe usar.

##  <a name="revokeclassobjects"></a>  CComModule::RevokeClassObjects

A partir de ATL 7,0 `CComModule` , está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Quita el objeto de clase. Este método solo está disponible para los archivos exe.

##  <a name="term"></a>  CComModule::Term

A partir de ATL 7,0 `CComModule` , está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
void Term() throw();
```

### <a name="remarks"></a>Comentarios

Libera todos los miembros de datos.

##  <a name="unregisterclasshelper"></a>  CComModule::UnregisterClassHelper

A partir de ATL 7,0 `CComModule` , está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
ATL_DEPRECATED HRESULT UnregisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```

### <a name="parameters"></a>Parámetros

*clsid*<br/>
de CLSID del objeto cuya registro se va a anular.

*lpszProgID*<br/>
de Identificador de programa (ProgID) asociado al objeto.

*lpszVerIndProgID*<br/>
de ProgID independiente de la versión asociado al objeto.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Quita el registro de clase estándar de un objeto del registro del sistema.

El método [UpdateRegistryClass](#updateregistryclass) llama `UnregisterClassHelper`a.

##  <a name="unregisterserver"></a>  CComModule::UnregisterServer

A partir de ATL 7,0 `CComModule` , está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```

### <a name="parameters"></a>Parámetros

*bUnRegTypeLib*<br/>
Si es TRUE, también se anula el registro de la biblioteca de tipos.

*pCLSID*<br/>
Apunta al CLSID del objeto del que se va a anular el registro. Si es NULL (valor predeterminado), se anulará el registro de todos los objetos del mapa de objetos.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Dependiendo del parámetro *pCLSID* , anula el registro de un objeto de una sola clase o de todos los objetos del mapa de objetos.

`UnregisterServer`se llamará automáticamente `DLLUnregisterServer` a para un archivo dll `WinMain` o para una ejecución de exe con `/UnregServer` la opción de línea de comandos.

Consulte [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) para obtener información sobre cómo agregar una entrada al mapa de objetos.

##  <a name="updateregistryclass"></a>  CComModule::UpdateRegistryClass

A partir de ATL 7,0 `CComModule` , está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

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
CLSID del objeto que se va a registrar o del que se va a anular el registro.

*lpszProgID*<br/>
Identificador de programa (ProgID) asociado al objeto.

*lpszVerIndProgID*<br/>
ProgID independiente de la versión asociado al objeto.

*nDescID*<br/>
Identificador del recurso de cadena para la descripción del objeto.

*szDesc*<br/>
Cadena que contiene la descripción del objeto.

*dwFlags*<br/>
Especifica el modelo de subprocesos que se va a especificar en el registro. Los valores posibles son THREADFLAGS_APARTMENT, THREADFLAGS_BOTH o AUTPRXFLAG.

*bRegister*<br/>
Indica si se debe registrar el objeto.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Si *bRegister* es true, este método escribe el registro de clase estándar del objeto en el registro del sistema.

Si *bRegister* es false, quita el registro del objeto.

Dependiendo del valor de *bRegister*, `UpdateRegistryClass` llama a [RegisterClassHelper](#registerclasshelper) o [UnregisterClassHelper](#unregisterclasshelper).

Al especificar la macro [DECLARE_REGISTRY](registry-macros.md#declare_registry) , `UpdateRegistryClass` se invocará automáticamente cuando se procese el mapa de objetos.

##  <a name="updateregistryfromresourced"></a>  CComModule::UpdateRegistryFromResourceD

A partir de ATL 7,0 `CComModule` , está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

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
de Nombre del recurso.

*nResID*<br/>
de IDENTIFICADOR de recurso.

*bRegister*<br/>
de Indica si se debe registrar el objeto.

*pMapEntries*<br/>
de Un puntero a la asignación de reemplazo que almacena los valores asociados a los parámetros reemplazables del script. ATL utiliza `%MODULE%`automáticamente. Para usar parámetros reemplazables adicionales, vea la sección Comentarios para obtener más información. De lo contrario, use el valor predeterminado NULL.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Ejecuta el script contenido en el recurso especificado por *lpszRes* o *nResID*.

Si *bRegister* es true, este método registra el objeto en el registro del sistema; de lo contrario, anula el registro del objeto.

Al especificar la macro [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) o [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) , `UpdateRegistryFromResourceD` se invocará automáticamente cuando se procese el mapa de objetos.

> [!NOTE]
>  Para sustituir los valores de reemplazo en tiempo de ejecución, no especifique la macro DECLARE_REGISTRY_RESOURCE o DECLARE_REGISTRY_RESOURCEID. En su lugar, cree una matriz `_ATL_REGMAP_ENTRIES` de estructuras, donde cada entrada contiene un marcador de posición de variable emparejado con un valor para reemplazar el marcador de posición en tiempo de ejecución. A continuación `UpdateRegistryFromResourceD`, llame a, pasando la matriz para el parámetro *pMapEntries* . Esto agrega todos los valores de reemplazo de `_ATL_REGMAP_ENTRIES` las estructuras al mapa de reemplazo del registrador.

> [!NOTE]
>  Para vincular estáticamente al componente del registro de ATL (registrador), vea [UpdateRegistryFromResourceS](#updateregistryfromresources).

Para obtener más información sobre los parámetros reemplazables y los scripts, vea el artículo [el componente de registro de ATL (registrador)](../../atl/atl-registry-component-registrar.md).

##  <a name="updateregistryfromresources"></a>  CComModule::UpdateRegistryFromResourceS

A partir de ATL 7,0 `CComModule` , está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

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
de Nombre del recurso.

*nResID*<br/>
de IDENTIFICADOR de recurso.

*bRegister*<br/>
de Indica si se debe registrar el script de recursos.

*pMapEntries*<br/>
de Un puntero a la asignación de reemplazo que almacena los valores asociados a los parámetros reemplazables del script. ATL utiliza `%MODULE%`automáticamente. Para usar parámetros reemplazables adicionales, vea la sección Comentarios para obtener más información. De lo contrario, use el valor predeterminado NULL.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Similar a [UpdateRegistryFromResourceD](#updateregistryfromresourced) , `UpdateRegistryFromResourceS` excepto que crea un vínculo estático al componente del registro de ATL (registrador).

`UpdateRegistryFromResourceS`se invocará automáticamente cuando se procese el mapa de objetos, siempre que se `#define _ATL_STATIC_REGISTRY` agregue a Stdafx. h.

> [!NOTE]
>  Para sustituir los valores de reemplazo en tiempo de ejecución, no especifique la macro [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) o [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) . En su lugar, cree una matriz `_ATL_REGMAP_ENTRIES` de estructuras, donde cada entrada contiene un marcador de posición de variable emparejado con un valor para reemplazar el marcador de posición en tiempo de ejecución. A continuación `UpdateRegistryFromResourceS`, llame a, pasando la matriz para el parámetro *pMapEntries* . Esto agrega todos los valores de reemplazo de `_ATL_REGMAP_ENTRIES` las estructuras al mapa de reemplazo del registrador.

Para obtener más información sobre los parámetros reemplazables y los scripts, vea el artículo [el componente de registro de ATL (registrador)](../../atl/atl-registry-component-registrar.md).

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)
