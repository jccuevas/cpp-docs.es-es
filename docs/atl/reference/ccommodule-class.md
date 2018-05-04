---
title: CComModule (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CComModule class
- DLL modules [C++], ATL
ms.assetid: f5face2c-8fd8-40e6-9ec3-54ab74701769
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05b4ec763f6ee719e96627be3dc81a1e9b56c2c1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="ccommodule-class"></a>CComModule (clase)
A partir de ATL 7.0, `CComModule` está en desuso: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CComModule : public _ATL_MODULE
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComModule::GetClassObject](#getclassobject)|Crea un objeto de CLSID especificado. Para las DLL solo.|  
|[CComModule::GetModuleInstance](#getmoduleinstance)|Devuelve `m_hInst`.|  
|[CComModule::GetResourceInstance](#getresourceinstance)|Devuelve `m_hInstResource`.|  
|[CComModule::GetTypeLibInstance](#gettypelibinstance)|Devuelve `m_hInstTypeLib`.|  
|[Ejecución](#init)|Inicializa a los miembros de datos.|  
|[CComModule::RegisterClassHelper](#registerclasshelper)|Entra en el registro de clase estándar de un objeto en el registro del sistema.|  
|[CComModule::RegisterClassObjects](#registerclassobjects)|Registra el objeto de clase. Para archivos exe solo.|  
|[CComModule::RegisterServer](#registerserver)|Actualiza el registro del sistema para cada objeto del mapa de objetos.|  
|[CComModule::RegisterTypeLib](#registertypelib)|Registra una biblioteca de tipos.|  
|[CComModule::RevokeClassObjects](#revokeclassobjects)|Revoca el objeto de clase. Para archivos exe solo.|  
|[CComModule:: term](#term)|Miembros de datos de versiones.|  
|[CComModule::UnregisterClassHelper](#unregisterclasshelper)|Quita el registro de clase estándar de un objeto desde el registro del sistema.|  
|[CComModule::UnregisterServer](#unregisterserver)|Anula el registro de cada objeto del mapa de objetos.|  
|[CComModule::UpdateRegistryClass](#updateregistryclass)|Registra o anula el registro de registro de clase estándar de un objeto.|  
|[CComModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Se ejecuta la secuencia de comandos contenida en un recurso para registrar o anular el registro de un objeto especificado.|  
|[CComModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|Estáticamente vínculos para el componente de registro de ATL. Se ejecuta la secuencia de comandos contenida en un recurso para registrar o anular el registro de un objeto especificado.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComModule::m_csObjMap](#m_csobjmap)|Se garantiza un acceso sincronizado a la información de asignación de objeto.|  
|[CComModule::m_csTypeInfoHolder](#m_cstypeinfoholder)|Se garantiza un acceso sincronizado a la información de la biblioteca de tipos.|  
|[CComModule::m_csWindowCreate](#m_cswindowcreate)|Se garantiza un acceso sincronizado a información de clase de ventana y datos estáticos que se usan durante la creación de la ventana.|  
|[CComModule::m_hInst](#m_hinst)|Contiene el identificador de la instancia del módulo.|  
|[CComModule::m_hInstResource](#m_hinstresource)|De forma predeterminada, contiene el identificador de la instancia del módulo.|  
|[CComModule::m_hInstTypeLib](#m_hinsttypelib)|De forma predeterminada, contiene el identificador de la instancia del módulo.|  
|[CComModule::m_pObjMap](#m_pobjmap)|Señala al mapa de objetos mantenida por la instancia del módulo.|  
  
## <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Esta clase está en desuso y los asistentes para generación de código ATL ahora utilizan el [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) y [CAtlModule](../../atl/reference/catlmodule-class.md) las clases derivadas. Vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más información. La siguiente información es para su uso con las aplicaciones creadas con versiones anteriores de ATL. `CComModule` sigue siendo parte de ATL para hacia atrás capacidad.  
  
 `CComModule` implementa un módulo de servidor COM, lo que permite un cliente tener acceso a los componentes del módulo. `CComModule` es compatible con los módulos de (locales) de EXE y DLL (en proceso).  
  
 Un `CComModule` instancia utiliza un mapa de objetos para mantener un conjunto de definiciones de objeto de clase. Esta asignación de objeto se implementa como una matriz de `_ATL_OBJMAP_ENTRY` las estructuras y contiene información para:  
  
-   Escribir y quitar descripciones de los objetos en el registro del sistema.  
  
-   Crear instancias de objetos a través de un generador de clases.  
  
-   Establecer la comunicación entre un cliente y el objeto raíz en el componente.  
  
-   Realizar la administración de la duración de objetos de clase.  
  
 Al ejecutar el Asistente para aplicaciones COM de ATL, el asistente genera automáticamente `_Module`, una instancia global de `CComModule` o una clase derivada de ella. Para obtener más información sobre el Asistente para proyectos ATL, vea el artículo [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md).  
  
 Además `CComModule`, ATL proporciona [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), que implementa un módulo de modelo apartamento para servicios de Windows y los archivos exe. Derivar su módulo de `CComAutoThreadModule` cuando desee crear objetos en varios contenedores.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 `CComModule`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="getclassobject"></a>  CComModule::GetClassObject  
 A partir de ATL 7.0, `CComModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
HRESULT GetClassObject(  
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `rclsid`  
 [in] El CLSID del objeto que se va a crear.  
  
 `riid`  
 [in] El IID de la interfaz solicitada.  
  
 `ppv`  
 [out] Un puntero al puntero de interfaz identificado por `riid`. Si el objeto no admite esta interfaz, `ppv` está establecido en **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Crea un objeto del CLSID especificado y recupera un puntero de interfaz a este objeto.  
  
 `GetClassObject` solo está disponible para archivos DLL.  
  
##  <a name="getmoduleinstance"></a>  CComModule::GetModuleInstance  
 A partir de ATL 7.0, `CComModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
HINSTANCE GetModuleInstance() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El `HINSTANCE` identificación de este módulo.  
  
### <a name="remarks"></a>Comentarios  
 Devuelve el [m_hInst](#m_hinst) miembro de datos.  
  
##  <a name="getresourceinstance"></a>  CComModule::GetResourceInstance  
 A partir de ATL 7.0, `CComModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
HINSTANCE GetResourceInstance() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una clase `HINSTANCE`.  
  
### <a name="remarks"></a>Comentarios  
 Devuelve el [m_hInstResource](#m_hinstresource) miembro de datos.  
  
##  <a name="gettypelibinstance"></a>  CComModule::GetTypeLibInstance  
 A partir de ATL 7.0, `CComModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
HINSTANCE GetTypeLibInstance() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una clase `HINSTANCE`.  
  
### <a name="remarks"></a>Comentarios  
 Devuelve el [m_hInstTypeLib](#m_hinsttypelib) miembro de datos.  
  
##  <a name="init"></a>  Ejecución  
 A partir de ATL 7.0, `CComModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 [in] Un puntero a una matriz de entradas de asignación de objeto.  
  
 `h`  
 [in] El `HINSTANCE` pasado a **DLLMain** o `WinMain`.  
  
 `plibid`  
 [in] Un puntero a LIBID de la biblioteca de tipos asociado al proyecto.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Inicializa a todos los miembros de datos.  
  
##  <a name="m_csobjmap"></a>  CComModule::m_csObjMap  
 A partir de ATL 7.0, `CComModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
CRITICAL_SECTION m_csObjMap;
```  
  
### <a name="remarks"></a>Comentarios  
 Se garantiza un acceso sincronizado a la asignación de objeto.  
  
##  <a name="m_cstypeinfoholder"></a>  CComModule::m_csTypeInfoHolder  
 A partir de ATL 7.0, `CComModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
CRITICAL_SECTION m_csTypeInfoHolder;
```  
  
### <a name="remarks"></a>Comentarios  
 Se garantiza un acceso sincronizado a la biblioteca de tipos.  
  
##  <a name="m_cswindowcreate"></a>  CComModule::m_csWindowCreate  
 A partir de ATL 7.0, `CComModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
CRITICAL_SECTION m_csWindowCreate;
```  
  
### <a name="remarks"></a>Comentarios  
 Se garantiza un acceso sincronizado a la información de clase de ventana y a los datos estáticos que se usan durante la creación de la ventana.  
  
##  <a name="m_hinst"></a>  CComModule::m_hInst  
 A partir de ATL 7.0, `CComModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
HINSTANCE m_hInst;
```  
  
### <a name="remarks"></a>Comentarios  
 Contiene el identificador de la instancia del módulo.  
  
 El [Init](#init) método establece `m_hInst` para el identificador pasado a **DLLMain** o `WinMain`.  
  
##  <a name="m_hinstresource"></a>  CComModule::m_hInstResource  
 A partir de ATL 7.0, `CComModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
HINSTANCE m_hInstResource;
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, contiene el identificador de la instancia del módulo.  
  
 El [Init](#init) método establece `m_hInstResource` para el identificador pasado a **DLLMain** o `WinMain`. Puede establecer explícitamente `m_hInstResource` al identificador a un recurso.  
  
 El [GetResourceInstance](#getresourceinstance) método devuelve el identificador almacenado en `m_hInstResource`.  
  
##  <a name="m_hinsttypelib"></a>  CComModule::m_hInstTypeLib  
 A partir de ATL 7.0, `CComModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
HINSTANCE m_hInstTypeLib;
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, contiene el identificador de la instancia del módulo.  
  
 El [Init](#init) método establece `m_hInstTypeLib` para el identificador pasado a **DLLMain** o `WinMain`. Puede establecer explícitamente `m_hInstTypeLib` al identificador de una biblioteca de tipos.  
  
 El [GetTypeLibInstance](#gettypelibinstance) método devuelve el identificador almacenado en `m_hInstTypeLib`.  
  
##  <a name="m_pobjmap"></a>  CComModule::m_pObjMap  
 A partir de ATL 7.0, `CComModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```  
  
### <a name="remarks"></a>Comentarios  
 Señala al mapa de objetos mantenida por la instancia del módulo.  
  
##  <a name="registerclasshelper"></a>  CComModule::RegisterClassHelper  
 A partir de ATL 7.0, `CComModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
ATL_DEPRECATED HRESULT RegisterClassHelper(  
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags);
```  
  
### <a name="parameters"></a>Parámetros  
 `clsid`  
 [in] Identificador CLSID del objeto que se registrará.  
  
 `lpszProgID`  
 [in] El ProgID asociado al objeto.  
  
 `lpszVerIndProgID`  
 [in] El ProgID independientes de la versión asociado al objeto.  
  
 `nDescID`  
 [in] El identificador de un recurso de cadena para la descripción del objeto.  
  
 `dwFlags`  
 [in] Especifica el modelo de subprocesos para escribir en el registro. Los valores posibles son **THREADFLAGS_APARTMENT**, **THREADFLAGS_BOTH**, o **AUTPRXFLAG**.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Entra en el registro de clase estándar de un objeto en el registro del sistema.  
  
 El [UpdateRegistryClass](#updateregistryclass) llamadas al método `RegisterClassHelper`.  
  
##  <a name="registerclassobjects"></a>  CComModule::RegisterClassObjects  
 A partir de ATL 7.0, `CComModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `dwClsContext`  
 [in] Especifica el contexto en el que se ejecutará el objeto de clase. Los valores posibles son **CLSCTX_INPROC_SERVER**, **CLSCTX_INPROC_HANDLER**, o **CLSCTX_LOCAL_SERVER**. Para obtener una descripción de estos valores, consulte [CLSCTX](http://msdn.microsoft.com/library/windows/desktop/ms693716) del SDK de Windows.  
  
 `dwFlags`  
 [in] Determina los tipos de conexión para el objeto de clase. Los valores posibles son **REGCLS_SINGLEUSE**, **REGCLS_MULTIPLEUSE**, o **REGCLS_MULTI_SEPARATE**. Para obtener una descripción de estos valores, consulte [REGCLS](http://msdn.microsoft.com/library/windows/desktop/ms679697) del SDK de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Registra un objeto de clase EXE con OLE para que otras aplicaciones puedan conectarse a él. Este método solo está disponible para archivos exe.  
  
##  <a name="registerserver"></a>  CComModule::RegisterServer  
 A partir de ATL 7.0, `CComModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,  
    const CLSID* pCLSID = NULL) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `bRegTypeLib`  
 [in] Indica si se registrará la biblioteca de tipos. El valor predeterminado es **FALSE**.  
  
 `pCLSID`  
 [in] Señala al CLSID del objeto que se va a registrar. Si **NULL** (el valor predeterminado), se registrará todos los objetos del mapa de objetos.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 En función de la `pCLSID` parámetro, actualiza el registro del sistema para un objeto de clase único o para todos los objetos del mapa de objetos.  
  
 Si `bRegTypeLib` es **TRUE**, también se actualizará la información de la biblioteca de tipos.  
  
 Vea [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) para obtener información sobre cómo agregar una entrada al mapa de objetos.  
  
 `RegisterServer` se llama de forma automática **DLLRegisterServer** de un archivo DLL o mediante `WinMain` para un archivo EXE ejecutar con la **/regserver** opción de línea de comandos.  
  
##  <a name="registertypelib"></a>  CComModule::RegisterTypeLib  
 A partir de ATL 7.0, `CComModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszIndex`  
 [in] Cadena con el formato `"\\N"`, donde `N` es el índice de entero del recurso de biblioteca de tipos.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Agrega información sobre una biblioteca de tipos para el registro del sistema.  
  
 Si la instancia del módulo que contiene varias bibliotecas de tipos, utilice la segunda versión de este método para especificar qué biblioteca de tipos se debe usar.  
  
##  <a name="revokeclassobjects"></a>  CComModule::RevokeClassObjects  
 A partir de ATL 7.0, `CComModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
HRESULT RevokeClassObjects() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Quita el objeto de clase. Este método solo está disponible para archivos exe.  
  
##  <a name="term"></a>  CComModule:: term  
 A partir de ATL 7.0, `CComModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
void Term() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera a todos los miembros de datos.  
  
##  <a name="unregisterclasshelper"></a>  CComModule::UnregisterClassHelper  
 A partir de ATL 7.0, `CComModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
ATL_DEPRECATED HRESULT UnregisterClassHelper(  
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```  
  
### <a name="parameters"></a>Parámetros  
 `clsid`  
 [in] Identificador CLSID del objeto se va a anular.  
  
 `lpszProgID`  
 [in] El ProgID asociado al objeto.  
  
 `lpszVerIndProgID`  
 [in] El ProgID independientes de la versión asociado al objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Quita el registro de clase estándar de un objeto desde el registro del sistema.  
  
 El [UpdateRegistryClass](#updateregistryclass) llamadas al método `UnregisterClassHelper`.  
  
##  <a name="unregisterserver"></a>  CComModule::UnregisterServer  
 A partir de ATL 7.0, `CComModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```  
  
### <a name="parameters"></a>Parámetros  
 `bUnRegTypeLib`  
 Si **TRUE**, también se anula el registrada de la biblioteca de tipos.  
  
 `pCLSID`  
 Señala el CLSID del objeto que se puede anular el registro. Si **NULL** (el valor predeterminado), todos los objetos del mapa de objetos se cancelará.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 En función de la `pCLSID` anula el registro de parámetro, un objeto de clase único o todos los objetos del mapa de objetos.  
  
 `UnregisterServer` se llama de forma automática **DllRegisterServer** de un archivo DLL o mediante `WinMain` para un archivo EXE ejecutar con la **/UnregServer** opción de línea de comandos.  
  
 Vea [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) para obtener información sobre cómo agregar una entrada al mapa de objetos.  
  
##  <a name="updateregistryclass"></a>  CComModule::UpdateRegistryClass  
 A partir de ATL 7.0, `CComModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
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
 `clsid`  
 Identificador CLSID del objeto que se registra o anula el registro.  
  
 `lpszProgID`  
 El ProgID asociado al objeto.  
  
 `lpszVerIndProgID`  
 El ProgID independientes de la versión asociado al objeto.  
  
 `nDescID`  
 El identificador del recurso de cadena para la descripción del objeto.  
  
 `szDesc`  
 Una cadena que contiene la descripción del objeto.  
  
 `dwFlags`  
 Especifica el modelo de subprocesos para escribir en el registro. Los valores posibles son **THREADFLAGS_APARTMENT**, **THREADFLAGS_BOTH**, o **AUTPRXFLAG**.  
  
 `bRegister`  
 Indica si el objeto debe registrarse.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Si `bRegister` es **TRUE**, este método escribe el registro de la clase estándar del objeto en el registro del sistema.  
  
 Si `bRegister` es **FALSE**, quita el registro del objeto.  
  
 Dependiendo del valor de `bRegister`, `UpdateRegistryClass` llama a [RegisterClassHelper](#registerclasshelper) o [UnregisterClassHelper](#unregisterclasshelper).  
  
 Mediante la especificación de la [DECLARE_REGISTRY](registry-macros.md#declare_registry) macro, `UpdateRegistryClass` se invocará automáticamente cuando se procesa la asignación de objeto.  
  
##  <a name="updateregistryfromresourced"></a>  CComModule::UpdateRegistryFromResourceD  
 A partir de ATL 7.0, `CComModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
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
 `lpszRes`  
 [in] Un nombre de recurso.  
  
 `nResID`  
 [in] Un identificador de recurso.  
  
 `bRegister`  
 [in] Indica si el objeto debe registrarse.  
  
 `pMapEntries`  
 [in] Un puntero a la asignación de reemplazo almacenar valores asociados con parámetros reemplazables de la secuencia de comandos. ATL utiliza automáticamente `%MODULE%`. Para usar parámetros reemplazables adicionales, vea la sección Comentarios para obtener más información. De lo contrario, utilice la **NULL** valor predeterminado.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Se ejecuta la secuencia de comandos contenida en el recurso especificado por `lpszRes` o `nResID`.  
  
 Si `bRegister` es **TRUE**, este método registra el objeto en el registro del sistema; en caso contrario, anula el registro del objeto.  
  
 Mediante la especificación de la [macros DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) o [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) macro, `UpdateRegistryFromResourceD` se invocará automáticamente cuando se procesa la asignación de objeto.  
  
> [!NOTE]
>  Para sustituir los valores de reemplazo en tiempo de ejecución, no se especifica la `DECLARE_REGISTRY_RESOURCE` o `DECLARE_REGISTRY_RESOURCEID` macro. En su lugar, cree una matriz de **_ATL_REGMAP_ENTRIES** estructuras, donde cada entrada contiene un marcador de posición variable emparejado con un valor para reemplazar el marcador de posición en tiempo de ejecución. A continuación, llame a `UpdateRegistryFromResourceD`, pasar la matriz el `pMapEntries` parámetro. Esto agrega todos los valores de reemplazo de la **_ATL_REGMAP_ENTRIES** estructuras al mapa de reemplazo del registrador.  
  
> [!NOTE]
>  Para vincular estáticamente para el componente de registro de ATL (registrador), consulte [UpdateRegistryFromResourceS](#updateregistryfromresources).  
  
 Para obtener más información sobre los parámetros reemplazables y secuencias de comandos, vea el artículo [el componente de registro de ATL (registrador)](../../atl/atl-registry-component-registrar.md).  
  
##  <a name="updateregistryfromresources"></a>  CComModule::UpdateRegistryFromResourceS  
 A partir de ATL 7.0, `CComModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
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
 `lpszRes`  
 [in] Un nombre de recurso.  
  
 `nResID`  
 [in] Un identificador de recurso.  
  
 `bRegister`  
 [in] Indica si se debe registrar el script del recurso.  
  
 `pMapEntries`  
 [in] Un puntero a la asignación de reemplazo almacenar valores asociados con parámetros reemplazables de la secuencia de comandos. ATL utiliza automáticamente `%MODULE%`. Para usar parámetros reemplazables adicionales, vea la sección Comentarios para obtener más información. De lo contrario, utilice la **NULL** valor predeterminado.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Similar a [UpdateRegistryFromResourceD](#updateregistryfromresourced) excepto `UpdateRegistryFromResourceS` crea un vínculo estático para el componente de registro de ATL (registrador).  
  
 `UpdateRegistryFromResourceS` se invocará automáticamente cuando se procesa la asignación de objeto, siempre que agregue `#define _ATL_STATIC_REGISTRY` a stdafx.h.  
  
> [!NOTE]
>  Para sustituir los valores de reemplazo en tiempo de ejecución, no se especifica la [macros DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) o [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) macro. En su lugar, cree una matriz de **_ATL_REGMAP_ENTRIES** estructuras, donde cada entrada contiene un marcador de posición variable emparejado con un valor para reemplazar el marcador de posición en tiempo de ejecución. A continuación, llame a `UpdateRegistryFromResourceS`, pasar la matriz el `pMapEntries` parámetro. Esto agrega todos los valores de reemplazo de la **_ATL_REGMAP_ENTRIES** estructuras al mapa de reemplazo del registrador.  
  
 Para obtener más información sobre los parámetros reemplazables y secuencias de comandos, vea el artículo [el componente de registro de ATL (registrador)](../../atl/atl-registry-component-registrar.md).  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)
