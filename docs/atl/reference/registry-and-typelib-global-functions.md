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
ms.openlocfilehash: c5fdaceb47b6cd09dd9d66f26af1337a8dc6bbae
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78863234"
---
# <a name="registry-and-typelib-global-functions"></a>Funciones globales Registry y TypeLib

Estas funciones proporcionan compatibilidad para cargar y registrar una biblioteca de tipos.

> [!IMPORTANT]
>  Las funciones enumeradas en las tablas siguientes no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

|||
|-|-|
|[AfxRegCreateKey](#afxregcreatekey)|Crea la clave del registro especificada.|
|[AfxRegDeleteKey](#afxregdeletekey)|Elimina la clave del registro especificada.|
|[AfxRegisterPreviewHandler](#afxregisterpreviewhandler)|Una aplicación auxiliar para registrar un controlador de vista previa.|
|[AfxUnregisterPreviewHandler](#afxunregisterpreviewhandler)| Aplicación auxiliar para anular el registro de un controlador de vista previa. |
|[AtlRegisterTypeLib](#atlregistertypelib)|Esta función se invoca para registrar una biblioteca de tipos.|
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|Se llama a esta función para anular el registro de una biblioteca de tipos|
|[AfxRegOpenKey](#afxregopenkey)|Abre la clave del registro especificada.|
|[AfxRegOpenKeyEx](#afxregopenkeyex)|Abre la clave del registro especificada.|
|[AtlLoadTypeLib](#atlloadtypelib)|Esta función se invoca para cargar una biblioteca de tipos.|
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|Esta función se invoca para actualizar el Registro desde el recurso especificado.|
|[RegistryDataExchange](#registrydataexchange)|Esta función se invoca para leer el Registro del sistema o escribir en él. Llamado por las [macros de intercambio de datos del registro](../../atl/reference/registry-data-exchange-macros.md).|

Estas funciones controlan qué nodo del registro utiliza el programa para almacenar información.

|||
|-|-|
|[AtlGetPerUserRegistration](#atlgetperuserregistration)|Recupera si la aplicación redirige el acceso del registro al nodo **HKEY_CURRENT_USER** ( **HKCU**).|
|[AtlSetPerUserRegistration](#atlsetperuserregistration)|Establece si la aplicación redirige el acceso del registro al nodo **HKEY_CURRENT_USER** ( **HKCU**).|

### <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

## <a name="atlgetperuserregistration"></a>AtlGetPerUserRegistration

Utilice esta función para determinar si la aplicación redirige el acceso del registro al nodo **HKEY_CURRENT_USER** (**HKCU**).

### <a name="syntax"></a>Sintaxis

```
ATLINLINE ATLAPI AtlGetPerUserRegistration(bool* pEnabled);
```

### <a name="parameters"></a>Parámetros

*pEnabled*<br/>
enuncia TRUE indica que la información del registro se dirige al nodo **HKCU** ; FALSE indica que la aplicación escribe información del registro en el nodo predeterminado. El nodo predeterminado es **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="return-value"></a>Valor devuelto

S_OK si el método es correcto; de lo contrario, el código de error HRESULT si se produce un error.

### <a name="remarks"></a>Observaciones

La redirección del registro no está habilitada de forma predeterminada. Si habilita esta opción, el acceso al registro se redirige a **HKEY_CURRENT_USER \software\classes**.

La redirección no es global. Esta redirección del registro solo afecta a los marcos de trabajo MFC y ATL.

### <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

## <a name="afxregcreatekey"></a>AfxRegCreateKey

Crea la clave del registro especificada.

### <a name="syntax"></a>Sintaxis

```
LONG AFXAPI AfxRegCreateKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parámetros

*hKey*<br/>
Identificador de una clave del registro abierta.

*lpSubKey*<br/>
Nombre de una clave que esta función abre o crea.

*phkResult*<br/>
Puntero a una variable que recibe un identificador de la clave abierta o creada.

*pTM*<br/>
Puntero a un objeto de `CAtlTransactionManager`.

### <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en la función, el valor devuelto es un código de error distinto de cero definido en Winerror. h.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxpriv.h

## <a name="afxregdeletekey"></a>AfxRegDeleteKey

Elimina la clave del registro especificada.

### <a name="syntax"></a>Sintaxis

```
LONG AFXAPI AfxRegDeleteKey(HKEY hKey, LPCTSTR lpSubKey, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parámetros

*hKey*<br/>
Identificador de una clave del registro abierta.

*lpSubKey*<br/>
Nombre de la clave que se va a eliminar.

*pTM*<br/>
Puntero a un objeto de `CAtlTransactionManager`.

### <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en la función, el valor devuelto es un código de error distinto de cero definido en Winerror. h.

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

##  <a name="atlregistertypelib"></a>AtlRegisterTypeLib

Esta función se invoca para registrar una biblioteca de tipos.

```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>Parámetros

*hInstTypeLib*<br/>
Identificador de la instancia de módulo.

*lpszIndex*<br/>
Cadena con el formato "\\\n", donde N es el índice entero del recurso de biblioteca de tipos. Puede ser NULL si no se requiere ningún índice.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Esta función auxiliar la usan [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver) y [CAtlComModule:: RegisterTypeLib](../../atl/reference/catlcommodule-class.md#registertypelib).

### <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

## <a name="afxregopenkey"></a>AfxRegOpenKey

Abre la clave del registro especificada.

### <a name="syntax"></a>Sintaxis

```
LONG AFXAPI AfxRegOpenKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parámetros

*hKey*<br/>
Identificador de una clave del registro abierta.

*lpSubKey*<br/>
Nombre de una clave que esta función abre o crea.

*phkResult*<br/>
Puntero a una variable que recibe un identificador de la clave creada.

*pTM*<br/>
Puntero a un objeto de `CAtlTransactionManager`.

### <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en la función, el valor devuelto es un código de error distinto de cero definido en Winerror. h.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxpriv.h

## <a name="afxregopenkeyex"></a>AfxRegOpenKeyEx

Abre la clave del registro especificada.

### <a name="syntax"></a>Sintaxis

```
LONG AFXAPI AfxRegOpenKeyEx(HKEY hKey, LPCTSTR lpSubKey, DWORD ulOptions, REGSAM samDesired, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parámetros

*hKey*<br/>
Identificador de una clave del registro abierta.

*lpSubKey*<br/>
Nombre de una clave que esta función abre o crea.

*ulOptions*<br/>
Este parámetro está reservado y debe ser cero.

*samDesired*<br/>
Máscara que especifica los derechos de acceso deseados para la clave.

*phkResult*<br/>
Puntero a una variable que recibe un identificador de la clave abierta.

*pTM*<br/>
Puntero a un objeto de `CAtlTransactionManager`.

### <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en la función, el valor devuelto es un código de error distinto de cero definido en Winerror. h.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxpriv.h

## <a name="afxunregisterpreviewhandler"></a>AfxUnregisterPreviewHandler

Aplicación auxiliar para anular el registro de un controlador de vista previa.

### <a name="syntax"></a>Sintaxis

```
BOOL AFXAPI AfxUnRegisterPreviewHandler(LPCTSTR lpszCLSID);
```

### <a name="parameters"></a>Parámetros

*lpszCLSID*<br/>
Especifica el CLSID del controlador cuya registro se va a anular.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="atlsetperuserregistration"></a>AtlSetPerUserRegistration

Establece si la aplicación redirige el acceso del registro al nodo **HKEY_CURRENT_USER** (**HKCU**).

### <a name="syntax"></a>Sintaxis

```
ATLINLINE ATLAPI AtlSetPerUserRegistration(bool bEnable);
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
de TRUE indica que la información del registro se dirige al nodo **HKCU** ; FALSE indica que la aplicación escribe información del registro en el nodo predeterminado. El nodo predeterminado es **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="return-value"></a>Valor devuelto

S_OK si el método es correcto; de lo contrario, el código de error HRESULT si se produce un error.

### <a name="remarks"></a>Observaciones

La redirección del registro no está habilitada de forma predeterminada. Si habilita esta opción, el acceso al registro se redirige a **HKEY_CURRENT_USER \software\classes**.

La redirección no es global. Esta redirección del registro solo afecta a los marcos de trabajo MFC y ATL.

### <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

##  <a name="atlunregistertypelib"></a>AtlUnRegisterTypeLib

Esta función se invoca para anular el registro de una biblioteca de tipos.

### <a name="syntax"></a>Sintaxis

```
ATLAPI AtlUnRegisterTypeLib(
    HINSTANCE hInstTypeLib,
    LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>Parámetros

*hInstTypeLib*<br/>
Identificador de la instancia de módulo.

*lpszIndex*<br/>
Cadena con el formato "\\\n", donde N es el índice entero del recurso de biblioteca de tipos. Puede ser NULL si no se requiere ningún índice.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Esta función auxiliar la usan [CAtlComModule:: UnRegisterTypeLib](../../atl/reference/catlcommodule-class.md#unregistertypelib) y [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver).

### <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

##  <a name="atlloadtypelib"></a>AtlLoadTypeLib

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
Identificador del módulo asociado a la biblioteca de tipos.

*lpszIndex*<br/>
Cadena con el formato "\\\n", donde N es el índice entero del recurso de biblioteca de tipos. Puede ser NULL si no se requiere ningún índice.

*pbstrPath*<br/>
Contiene la ruta de acceso completa del módulo asociado a la biblioteca de tipos si la devolución es correcta.

*ppTypeLib*<br/>
Contiene un puntero a un puntero a la biblioteca de tipos cargados, si la devolución es correcta.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

[AtlRegisterTypeLib](#atlregistertypelib) y [AtlUnRegisterTypeLib](#atlunregistertypelib)usan esta función auxiliar.

##  <a name="atlupdateregistryfromresourced"></a>AtlUpdateRegistryFromResourceD

Esta función quedó en desuso en Visual Studio 2013 y se quitó en Visual Studio 2015.

```
<removed>
```

##  <a name="registrydataexchange"></a>RegistryDataExchange

Esta función se invoca para leer el Registro del sistema o escribir en él.

### <a name="syntax"></a>Sintaxis

```
HRESULT RegistryDataExchange(
    T* pT,
    enum RDXOperations rdxOp,
    void* pItem = NULL);
```

### <a name="parameters"></a>Parámetros

*Ptos*<br/>
Puntero al objeto actual.

*rdxOp*<br/>
Un valor de enumeración que indica qué operación debe realizar la función. Vea la tabla de la sección Comentarios para ver los valores permitidos.

*pItem*<br/>
Puntero a los datos que se van a leer o escribir en el registro. Los datos también pueden representar una clave que se va a eliminar del registro. El valor predeterminado es NULL.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Las macros [BEGIN_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map) y [END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map) expandan a una función que llama a `RegistryDataExchange`.

En la tabla siguiente se muestran los posibles valores de enumeración que indican la operación que debe realizar la función:

|Valor de enumeración|Operación|
|----------------|---------------|
|eReadFromReg|Leer datos del registro.|
|eWriteToReg|Escribir datos en el registro.|
|eDeleteFromReg|Elimine la clave del registro.|

### <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

## <a name="see-also"></a>Consulte también

[Funciones](atl-functions.md)<br/>
[Macros de intercambio de datos de Registro](registry-data-exchange-macros.md)
