---
title: Clase CAtlModule
ms.date: 11/04/2016
f1_keywords:
- CAtlModule
- ATLBASE/ATL::CAtlModule
- ATLBASE/ATL::CAtlModule::CAtlModule
- ATLBASE/ATL::CAtlModule::AddCommonRGSReplacements
- ATLBASE/ATL::CAtlModule::AddTermFunc
- ATLBASE/ATL::CAtlModule::GetGITPtr
- ATLBASE/ATL::CAtlModule::GetLockCount
- ATLBASE/ATL::CAtlModule::Lock
- ATLBASE/ATL::CAtlModule::Term
- ATLBASE/ATL::CAtlModule::Unlock
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceD
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceDHelper
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceS
- ATLBASE/ATL::CAtlModule::m_libid
- ATLBASE/ATL::CAtlModule::m_pGIT
helpviewer_keywords:
- CAtlModule class
ms.assetid: 63fe02f1-4c4b-4e7c-ae97-7ad7b4252415
ms.openlocfilehash: 10658b118c97afe99144c3a4d25e0297aba3727f
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168020"
---
# <a name="catlmodule-class"></a>Clase CAtlModule

Esta clase proporciona métodos usados por varias clases de módulo ATL.

## <a name="syntax"></a>Sintaxis

```cpp
class ATL_NO_VTABLE CAtlModule : public _ATL_MODULE
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlModule::CAtlModule](#catlmodule)|El constructor.|
|[CAtlModule:: ~ CAtlModule](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)|Invalide este método para agregar parámetros al mapa de reemplazo del componente de registro de ATL (registrador).|
|[CAtlModule::AddTermFunc](#addtermfunc)|Agrega una nueva función a la que se llamará cuando finalice el módulo.|
|[CAtlModule::GetGITPtr](#getgitptr)|Devuelve el puntero de interfaz global.|
|[CAtlModule::GetLockCount](#getlockcount)|Devuelve el recuento de bloqueos.|
|[CAtlModule:: Lock](#lock)|Incrementa el recuento de bloqueos.|
|[CAtlModule:: Term](#term)|Libera todos los miembros de datos.|
|[CAtlModule:: Unlock](#unlock)|Reduce el recuento de bloqueos.|
|[CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Ejecuta el script contenido en un recurso especificado para registrar o anular el registro de un objeto.|
|[CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)|Llama `UpdateRegistryFromResourceD` a este método para realizar la actualización del registro.|
|[CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|Ejecuta el script contenido en un recurso especificado para registrar o anular el registro de un objeto. Este método se vincula estáticamente al componente del registro de ATL.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlModule:: m_libid](#m_libid)|Contiene el GUID del módulo actual.|
|[CAtlModule:: m_pGIT](#m_pgit)|Puntero a la tabla de interfaz global.|

## <a name="remarks"></a>Observaciones

Esta clase la usan la clase [CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md), la [clase CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)y la [clase CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md) para proporcionar compatibilidad con aplicaciones dll, aplicaciones exe y servicios de Windows, respectivamente.

Para obtener más información sobre los módulos de ATL, vea [clases de módulo ATL](../../atl/atl-module-classes.md).

Esta clase reemplaza la clase de [CComModule](../../atl/reference/ccommodule-class.md) obsoleta utilizada en versiones anteriores de ATL.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

`CAtlModule`

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

## <a name="catlmoduleaddcommonrgsreplacements"></a><a name="addcommonrgsreplacements"></a>CAtlModule::AddCommonRGSReplacements

Invalide este método para agregar parámetros al mapa de reemplazo del componente de registro de ATL (registrador).

```cpp
virtual HRESULT AddCommonRGSReplacements(IRegistrarBase* /* pRegistrar*/) throw() = 0;
```

### <a name="parameters"></a>Parámetros

*pRegistrar*<br/>
Reservado.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Los parámetros reemplazables permiten que el cliente de un registrador especifique los datos en tiempo de ejecución. Para ello, el registrador mantiene un mapa de reemplazo en el que especifica los valores asociados a los parámetros reemplazables en el script. El registrador realiza estas entradas en tiempo de ejecución.

Vea el tema [uso de parámetros reemplazables (el preprocesador del registrador)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) para obtener más detalles.

## <a name="catlmoduleaddtermfunc"></a><a name="addtermfunc"></a>CAtlModule::AddTermFunc

Agrega una nueva función a la que se llamará cuando finalice el módulo.

```cpp
HRESULT AddTermFunc(_ATL_TERMFUNC* pFunc, DWORD_PTR dw) throw();
```

### <a name="parameters"></a>Parámetros

*pFunc*<br/>
Puntero a la función que se va a agregar.

*dw*<br/>
Datos definidos por el usuario que se pasan a la función.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

## <a name="catlmodulecatlmodule"></a><a name="catlmodule"></a>CAtlModule::CAtlModule

El constructor.

```cpp
CAtlModule() throw();
```

### <a name="remarks"></a>Observaciones

Inicializa los miembros de datos e inicia una sección crítica en torno al subproceso del módulo.

## <a name="catlmodulecatlmodule"></a><a name="dtor"></a>CAtlModule:: ~ CAtlModule

Destructor.

```cpp
~CAtlModule() throw();
```

### <a name="remarks"></a>Observaciones

Libera todos los miembros de datos.

## <a name="catlmodulegetgitptr"></a><a name="getgitptr"></a>CAtlModule::GetGITPtr

Recupera un puntero a la tabla de interfaz global.

```cpp
virtual HRESULT GetGITPtr(IGlobalInterfaceTable** ppGIT) throw();
```

### <a name="parameters"></a>Parámetros

*ppGIT*<br/>
Puntero a la variable que recibirá el puntero a la tabla de interfaz global.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un código de error en caso de error. E_POINTER se devuelve si *ppGIT* es igual a NULL.

### <a name="remarks"></a>Observaciones

Si el objeto de tabla de interfaz global no existe, se crea y su dirección se almacena en la variable miembro [CAtlModule:: m_pGIT](#m_pgit).

En las compilaciones de depuración, se producirá un error de aserción si *ppGIT* es igual a NULL o si no se puede obtener el puntero de tabla de interfaz global.

Consulte [IGlobalInterfaceTable](/windows/win32/api/objidl/nn-objidl-iglobalinterfacetable) para obtener información sobre la tabla de la interfaz global.

## <a name="catlmodulegetlockcount"></a><a name="getlockcount"></a>CAtlModule::GetLockCount

Devuelve el recuento de bloqueos.

```cpp
virtual LONG GetLockCount() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el recuento de bloqueos. Este valor puede ser útil para los diagnósticos y la depuración.

## <a name="catlmodulelock"></a><a name="lock"></a>CAtlModule:: Lock

Incrementa el recuento de bloqueos.

```cpp
virtual LONG Lock() throw();
```

### <a name="return-value"></a>Valor devuelto

Incrementa el recuento de bloqueos y devuelve el valor actualizado. Este valor puede ser útil para los diagnósticos y la depuración.

## <a name="catlmodulem_libid"></a><a name="m_libid"></a>CAtlModule:: m_libid

Contiene el GUID del módulo actual.

```cpp
static GUID m_libid;
```

## <a name="catlmodulem_pgit"></a><a name="m_pgit"></a>CAtlModule:: m_pGIT

Puntero a la tabla de interfaz global.

```cpp
IGlobalInterfaceTable* m_pGIT;
```

## <a name="catlmoduleterm"></a><a name="term"></a>CAtlModule:: Term

Libera todos los miembros de datos.

```cpp
void Term() throw();
```

### <a name="remarks"></a>Observaciones

Libera todos los miembros de datos. El destructor llama a este método.

## <a name="catlmoduleunlock"></a><a name="unlock"></a>CAtlModule:: Unlock

Reduce el recuento de bloqueos.

```cpp
virtual LONG Unlock() throw();
```

### <a name="return-value"></a>Valor devuelto

Disminuye el recuento de bloqueos y devuelve el valor actualizado. Este valor puede ser útil para los diagnósticos y la depuración.

## <a name="catlmoduleupdateregistryfromresourced"></a><a name="updateregistryfromresourced"></a>CAtlModule::UpdateRegistryFromResourceD

Ejecuta el script contenido en un recurso especificado para registrar o anular el registro de un objeto.

```cpp
HRESULT WINAPI UpdateRegistryFromResourceD(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

HRESULT WINAPI UpdateRegistryFromResourceD(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*lpszRes*<br/>
Nombre del recurso.

*nResID*<br/>
IDENTIFICADOR de recurso.

*bRegister*<br/>
TRUE si se debe registrar el objeto; De lo contrario, FALSE.

*pMapEntries*<br/>
Un puntero a la asignación de reemplazo que almacena los valores asociados a los parámetros reemplazables del script. ATL utiliza automáticamente% MODULE%. Para usar parámetros reemplazables adicionales, vea [CAtlModule:: AddCommonRGSReplacements](#addcommonrgsreplacements). De lo contrario, use el valor predeterminado NULL.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Ejecuta el script contenido en el recurso especificado por *lpszRes o nResID*. Si *bRegister* es true, este método registra el objeto en el registro del sistema; en caso contrario, quita el objeto del registro.

Para vincular estáticamente al componente del registro de ATL (registrador), vea [CAtlModule:: UpdateRegistryFromResourceS](#updateregistryfromresources).

Este método llama a [CAtlModule:: UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper) y [IRegistrar:: ResourceUnregister](iregistrar-class.md#resourceunregister).

## <a name="catlmoduleupdateregistryfromresourcedhelper"></a><a name="updateregistryfromresourcedhelper"></a>CAtlModule::UpdateRegistryFromResourceDHelper

Llama `UpdateRegistryFromResourceD` a este método para realizar la actualización del registro.

```cpp
inline HRESULT WINAPI UpdateRegistryFromResourceDHelper(
    LPCOLESTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*lpszRes*<br/>
Nombre del recurso.

*bRegister*<br/>
Indica si se debe registrar el objeto.

*pMapEntries*<br/>
Un puntero a la asignación de reemplazo que almacena los valores asociados a los parámetros reemplazables del script. ATL utiliza automáticamente% MODULE%. Para usar parámetros reemplazables adicionales, vea [CAtlModule:: AddCommonRGSReplacements](#addcommonrgsreplacements). De lo contrario, use el valor predeterminado NULL.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Este método proporciona la implementación de [CAtlModule:: UpdateRegistryFromResourceD](#updateregistryfromresourced).

## <a name="catlmoduleupdateregistryfromresources"></a><a name="updateregistryfromresources"></a>CAtlModule::UpdateRegistryFromResourceS

Ejecuta el script contenido en un recurso especificado para registrar o anular el registro de un objeto. Este método se vincula estáticamente al componente del registro de ATL.

```cpp
HRESULT WINAPI UpdateRegistryFromResourceS(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

HRESULT WINAPI UpdateRegistryFromResourceS(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*nResID*<br/>
IDENTIFICADOR de recurso.

*lpszRes*<br/>
Nombre del recurso.

*bRegister*<br/>
Indica si se debe registrar el script de recursos.

*pMapEntries*<br/>
Un puntero a la asignación de reemplazo que almacena los valores asociados a los parámetros reemplazables del script. ATL utiliza automáticamente% MODULE%. Para usar parámetros reemplazables adicionales, vea [CAtlModule:: AddCommonRGSReplacements](#addcommonrgsreplacements). De lo contrario, use el valor predeterminado NULL.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Similar a [CAtlModule:: UpdateRegistryFromResourceD](#updateregistryfromresourced) , `CAtlModule::UpdateRegistryFromResourceS` salvo que crea un vínculo estático al componente del registro de ATL (registrador).

## <a name="see-also"></a>Consulte también

[_ATL_MODULE](atl-typedefs.md#_atl_module)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clases de módulo](../../atl/atl-module-classes.md)<br/>
[Componente de registro (Registrador)](../../atl/atl-registry-component-registrar.md)
