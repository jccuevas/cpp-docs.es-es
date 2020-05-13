---
title: Funciones globales Registry y TypeLib
ms.date: 03/27/2019
f1_keywords:
- atlbase/ATL::AtlGetPerUserRegistration
- afxpriv/ATL::AfxRegCreateKey
- afxpriv/ATL::AfxRegDeleteKey
- atlbase/ATL::AtlRegisterTypeLib
- afxpriv/ATL::AfxRegOpenKey
- afxpriv/ATL::AfxRegOpenKeyEx
- afxdisp/ATL::AfxUnregisterPreviewHandler
- atlbase/ATL::AtlSetPerUserRegistration
- atlbase/ATL::AtlUnRegisterTypeLib
- atlbase/ATL::AtlLoadTypeLib
- atlbase/ATL::AtlUpdateRegistryFromResourceD
- atlbase/ATL::RegistryDataExchange
helpviewer_keywords:
- RegistryDataExchange function, global functions
ms.assetid: d58b8a4e-975c-4417-8b34-d3c847f679b3
ms.openlocfilehash: 69df927ddd04c19d10703854aa8c8948894309d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326086"
---
# <a name="registry-and-typelib-global-functions"></a>Funciones globales Registry y TypeLib

Estas funciones proporcionan compatibilidad para cargar y registrar una biblioteca de tipos.

> [!IMPORTANT]
> Las funciones enumeradas en las tablas siguientes no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

|||
|-|-|
|[AfxRegCreateKey](#afxregcreatekey)|Crea la clave del Registro especificada.|
|[AfxRegDeleteKey](#afxregdeletekey)|Elimina la clave del Registro especificada.|
|[AfxRegisterPreviewHandler](#afxregisterpreviewhandler)|Una aplicación auxiliar para registrar un controlador de vista previa.|
|[AfxUnregisterPreviewHandler](#afxunregisterpreviewhandler)| Una aplicación auxiliar para anular el registro de un controlador de vista previa. |
|[AtlRegisterTypeLib](#atlregistertypelib)|Esta función se invoca para registrar una biblioteca de tipos.|
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|Esta función se llama para anular el registro de una biblioteca de tipos|
|[AfxRegOpenKey](#afxregopenkey)|Abre la clave del Registro especificada.|
|[AfxRegOpenKeyEx](#afxregopenkeyex)|Abre la clave del Registro especificada.|
|[AtlLoadTypeLib](#atlloadtypelib)|Esta función se invoca para cargar una biblioteca de tipos.|
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|Esta función se invoca para actualizar el Registro desde el recurso especificado.|
|[RegistryDataExchange](#registrydataexchange)|Esta función se invoca para leer el Registro del sistema o escribir en él. Llamado por las macros de intercambio de [datos del registro](../../atl/reference/registry-data-exchange-macros.md).|

Estas funciones controlan qué nodo del registro utiliza el programa para almacenar información.

|||
|-|-|
|[AtlGetPerUserRegistration](#atlgetperuserregistration)|Recupera si la aplicación redirige el acceso del Registro al nodo **HKEY_CURRENT_USER** ( **HKCU**).|
|[AtlGetPerUserRegistration](#atlsetperuserregistration)|Establece si la aplicación redirige el acceso del Registro al nodo **HKEY_CURRENT_USER** ( **HKCU**).|

### <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="atlgetperuserregistration"></a><a name="atlgetperuserregistration"></a>AtlGetPerUserRegistration

Utilice esta función para determinar si la aplicación redirige el acceso del Registro al nodo **HKEY_CURRENT_USER** (**HKCU**).

### <a name="syntax"></a>Sintaxis

```
ATLINLINE ATLAPI AtlGetPerUserRegistration(bool* pEnabled);
```

### <a name="parameters"></a>Parámetros

*Penabled*<br/>
[fuera] TRUE indica que la información del Registro se dirige al nodo **HKCU;** FALSE indica que la aplicación escribe información del Registro en el nodo predeterminado. El nodo predeterminado es **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="return-value"></a>Valor devuelto

S_OK si el método se realiza correctamente, de lo contrario se produce el código de error HRESULT si se produce un error.

### <a name="remarks"></a>Observaciones

La redirección del registro no está habilitada de forma predeterminada. Si habilita esta opción, el acceso al Registro se redirige a **HKEY_CURRENT_USER, Software y Clases**.

La redirección no es global. Esta redirección del Registro solo afecta a los marcos MFC y ATL.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="afxregcreatekey"></a><a name="afxregcreatekey"></a>AfxRegCreateKey

Crea la clave del Registro especificada.

### <a name="syntax"></a>Sintaxis

```
LONG AFXAPI AfxRegCreateKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parámetros

*hKey*<br/>
Identificador de una clave de registro abierta.

*lpSubKey*<br/>
El nombre de una clave que esta función abre o crea.

*phkResult*<br/>
Puntero a una variable que recibe un identificador de la clave abierta o creada.

*Ptm*<br/>
Puntero a `CAtlTransactionManager` un objeto.

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto se ERROR_SUCCESS. Si se produce un error en la función, el valor devuelto es un código de error distinto de cero definido en Winerror.h.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxpriv.h

## <a name="afxregdeletekey"></a><a name="afxregdeletekey"></a>AfxRegDeleteKey

Elimina la clave del Registro especificada.

### <a name="syntax"></a>Sintaxis

```
LONG AFXAPI AfxRegDeleteKey(HKEY hKey, LPCTSTR lpSubKey, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parámetros

*hKey*<br/>
Identificador de una clave de registro abierta.

*lpSubKey*<br/>
El nombre de la clave que se va a eliminar.

*Ptm*<br/>
Puntero a `CAtlTransactionManager` un objeto.

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto se ERROR_SUCCESS. Si se produce un error en la función, el valor devuelto es un código de error distinto de cero definido en Winerror.h.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxpriv.h

## <a name="afxregisterpreviewhandler"></a>

Una aplicación auxiliar para registrar un controlador de vista previa.

### <a name="syntax"></a>Sintaxis

```
BOOL AFXAPI AfxRegisterPreviewHandler(LPCTSTR lpszCLSID, LPCTSTR lpszShortTypeName, LPCTSTR lpszFilterExt);
```

### <a name="parameters"></a>Parámetros

*lpszCLSID*<br/>
Especifica el CLSID del controlador.

*lpszShortTypeName*<br/>
Especifica el ProgID del controlador.

*lpszFilterExt*<br/>
Especifica la extensión de archivo registrada con este controlador.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="atlregistertypelib"></a><a name="atlregistertypelib"></a>AtlRegisterTypeLib

Esta función se invoca para registrar una biblioteca de tipos.

```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>Parámetros

*hInstTypeLib*<br/>
El identificador de la instancia del módulo.

*lpszIndex*<br/>
Cadena con el\\formato " .N", donde N es el índice entero del recurso de biblioteca de tipos. Puede ser NULL si no se requiere ningún índice.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Esta función auxiliar es utilizada por [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver) y [CAtlComModule::RegisterTypeLib](../../atl/reference/catlcommodule-class.md#registertypelib).

### <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="afxregopenkey"></a><a name="afxregopenkey"></a>AfxRegOpenKey

Abre la clave del Registro especificada.

### <a name="syntax"></a>Sintaxis

```
LONG AFXAPI AfxRegOpenKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parámetros

*hKey*<br/>
Identificador de una clave de registro abierta.

*lpSubKey*<br/>
El nombre de una clave que esta función abre o crea.

*phkResult*<br/>
Puntero a una variable que recibe un identificador de la clave creada.

*Ptm*<br/>
Puntero a `CAtlTransactionManager` un objeto.

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto se ERROR_SUCCESS. Si se produce un error en la función, el valor devuelto es un código de error distinto de cero definido en Winerror.h.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxpriv.h

## <a name="afxregopenkeyex"></a><a name="afxregopenkeyex"></a>AfxRegOpenKeyEx

Abre la clave del Registro especificada.

### <a name="syntax"></a>Sintaxis

```
LONG AFXAPI AfxRegOpenKeyEx(HKEY hKey, LPCTSTR lpSubKey, DWORD ulOptions, REGSAM samDesired, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parámetros

*hKey*<br/>
Identificador de una clave de registro abierta.

*lpSubKey*<br/>
El nombre de una clave que esta función abre o crea.

*ulOptions*<br/>
Este parámetro está reservado y debe ser cero.

*samDesired*<br/>
Máscara que especifica los derechos de acceso deseados a la clave.

*phkResult*<br/>
Puntero a una variable que recibe un identificador de la clave abierta.

*Ptm*<br/>
Puntero a `CAtlTransactionManager` un objeto.

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto se ERROR_SUCCESS. Si se produce un error en la función, el valor devuelto es un código de error distinto de cero definido en Winerror.h.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxpriv.h

## <a name="afxunregisterpreviewhandler"></a><a name="afxunregisterpreviewhandler"></a>AfxUnregisterPreviewHandler

Una aplicación auxiliar para anular el registro de un controlador de vista previa.

### <a name="syntax"></a>Sintaxis

```
BOOL AFXAPI AfxUnRegisterPreviewHandler(LPCTSTR lpszCLSID);
```

### <a name="parameters"></a>Parámetros

*lpszCLSID*<br/>
Especifica el CLSID del controlador que se va a anular el registro.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="atlsetperuserregistration"></a><a name="atlsetperuserregistration"></a>AtlSetPerUserRegistration

Establece si la aplicación redirige el acceso del Registro al nodo **HKEY_CURRENT_USER** (**HKCU**).

### <a name="syntax"></a>Sintaxis

```
ATLINLINE ATLAPI AtlSetPerUserRegistration(bool bEnable);
```

### <a name="parameters"></a>Parámetros

*bHabilitar*<br/>
[en] TRUE indica que la información del Registro se dirige al nodo **HKCU;** FALSE indica que la aplicación escribe información del Registro en el nodo predeterminado. El nodo predeterminado es **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="return-value"></a>Valor devuelto

S_OK si el método se realiza correctamente, de lo contrario se produce el código de error HRESULT si se produce un error.

### <a name="remarks"></a>Observaciones

La redirección del registro no está habilitada de forma predeterminada. Si habilita esta opción, el acceso al Registro se redirige a **HKEY_CURRENT_USER, Software y Clases**.

La redirección no es global. Esta redirección del Registro solo afecta a los marcos MFC y ATL.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="atlunregistertypelib"></a><a name="atlunregistertypelib"></a>AtlUnRegisterTypeLib

Esta función se invoca para anular el registro de una biblioteca de tipos.

### <a name="syntax"></a>Sintaxis

```
ATLAPI AtlUnRegisterTypeLib(
    HINSTANCE hInstTypeLib,
    LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>Parámetros

*hInstTypeLib*<br/>
El identificador de la instancia del módulo.

*lpszIndex*<br/>
Cadena con el\\formato " .N", donde N es el índice entero del recurso de biblioteca de tipos. Puede ser NULL si no se requiere ningún índice.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Esta función auxiliar es utilizada por [CAtlComModule::UnRegisterTypeLib](../../atl/reference/catlcommodule-class.md#unregistertypelib) y [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver).

### <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="atlloadtypelib"></a><a name="atlloadtypelib"></a>AtlLoadTypeLib

Esta función se invoca para cargar una biblioteca de tipos.

### <a name="syntax"></a>Sintaxis

```
ATLINLINE ATLAPI AtlLoadTypeLib(
    HINSTANCE hInstTypeLib,
    LPCOLESTR lpszIndex,
    BSTR* pbstrPath,
    ITypeLib** ppTypeLib);
```

### <a name="parameters"></a>Parámetros

*hInstTypeLib*<br/>
Controle el módulo asociado a la biblioteca de tipos.

*lpszIndex*<br/>
Cadena con el\\formato " .N", donde N es el índice entero del recurso de biblioteca de tipos. Puede ser NULL si no se requiere ningún índice.

*pbstrPath*<br/>
En la devolución correcta, contiene la ruta de acceso completa del módulo asociado a la biblioteca de tipos.

*ppTypeLib*<br/>
Si se devuelve correctamente, contiene un puntero a un puntero a la biblioteca de tipos cargada.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Esta función auxiliar es utilizada por [AtlRegisterTypeLib](#atlregistertypelib) y [AtlUnRegisterTypeLib](#atlunregistertypelib).

## <a name="atlupdateregistryfromresourced"></a><a name="atlupdateregistryfromresourced"></a>AtlUpdateRegistryFromResourceD

Esta función quedó en desuso en Visual Studio 2013 y se quitó en Visual Studio 2015.

```
<removed>
```

## <a name="registrydataexchange"></a><a name="registrydataexchange"></a>RegistryDataExchange

Esta función se invoca para leer el Registro del sistema o escribir en él.

### <a name="syntax"></a>Sintaxis

```
HRESULT RegistryDataExchange(
    T* pT,
    enum RDXOperations rdxOp,
    void* pItem = NULL);
```

### <a name="parameters"></a>Parámetros

*Pt*<br/>
Un puntero al objeto actual.

*rdxOp*<br/>
Un valor de enumeración que indica qué operación debe realizar la función. Consulte la tabla en la sección Comentarios para ver los valores permitidos.

*pItem*<br/>
Puntero a los datos que se van a leer o escribir en el registro. Los datos también pueden representar una clave que se va a eliminar del registro. El valor predeterminado es NULL.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Las macros [BEGIN_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map) y [END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map) expandir `RegistryDataExchange`a una función que llama a .

Los posibles valores de enumeración que indican la operación que debe realizar la función se muestran en la tabla siguiente:

|Valor de enumeración|Operación|
|----------------|---------------|
|eReadFromReg|Leer datos del registro.|
|eWriteToReg|Escribir datos en el registro.|
|eDeleteFromReg|Elimine la clave del registro.|

### <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="see-also"></a>Consulte también

[Functions](atl-functions.md)<br/>
[Macros de intercambio de datos del registro](registry-data-exchange-macros.md)
