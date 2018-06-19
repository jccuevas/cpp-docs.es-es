---
title: Funciones globales Registry y TypeLib | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- RegistryDataExchange function, global functions
ms.assetid: d58b8a4e-975c-4417-8b34-d3c847f679b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb0a89ecf8bb81e515703abe819bb1edfbf80d59
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365512"
---
# <a name="registry-and-typelib-global-functions"></a>Funciones globales Registry y TypeLib
Estas funciones proporcionan compatibilidad para cargar y registrar una biblioteca de tipos.  
  
> [!IMPORTANT]
>  Las funciones se enumeran en las tablas siguientes no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
|||  
|-|-|  
|[AfxRegCreateKey](#afxrefcreatekey)|Crea la clave del registro especificada.|
|[AfxRegDeleteKey](#afxrefdeletekey)|Elimina la clave del registro especificada.|
|[AfxRegisterPreviewHandler](#afxregisterpreviewhandler)|Una aplicación auxiliar para registrar un controlador de vista previa.|
|[AfxUnregisterPreviewHandler](#afxunregisterpreviewhandler)| Una aplicación auxiliar para anular el registro de un controlador de vista previa. |
|[AtlRegisterTypeLib](#atlregistertypelib)|Esta función se invoca para registrar una biblioteca de tipos.|  
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|Esta función se invoca para anular el registro de una biblioteca de tipos|  
|[AfxRegOpenKey](#afxregopenkey)|Abre la clave del registro especificada.|
|[AfxRegOpenKeyEx](#afxregopenkeyex)|Abre la clave del registro especificada.|
|[AtlLoadTypeLib](#atlloadtypelib)|Esta función se invoca para cargar una biblioteca de tipos.|  
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|Esta función se invoca para actualizar el Registro desde el recurso especificado.|  
|[RegistryDataExchange](#registrydataexchange)|Esta función se invoca para leer el Registro del sistema o escribir en él. Llamado por el [Macros de intercambio de datos de registro](../../atl/reference/registry-data-exchange-macros.md).|  
  
 Estas funciones controlan qué nodo en el registro del programa que se usa para almacenar información.  
  
|||  
|-|-|  
|[AtlGetPerUserRegistration](#atlgetperuserregistration)|Recupera si la aplicación redirige el acceso de registro a la **HKEY_CURRENT_USER** ( **HKCU**) nodo.|  
|[AtlSetPerUserRegistration](#atlsetperuserregistration)|Establece si la aplicación redirige el acceso de registro a la **HKEY_CURRENT_USER** ( **HKCU**) nodo.|  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h

## <a name="atlgetperuserregistration"></a> AtlGetPerUserRegistration
Utilice esta función para determinar si la aplicación redirige el acceso de registro a la **HKEY_CURRENT_USER** (**HKCU**) nodo.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
ATLINLINE ATLAPI AtlGetPerUserRegistration(bool* pEnabled);  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `pEnabled`  
 `TRUE` indica que la información de registro se dirige a la **HKCU** nodo; `FALSE` indica que la aplicación escribe información de registro en el nodo de forma predeterminada. El nodo de valor predeterminado es **HKEY_CLASSES_ROOT** (**HKCR**).  
  
### <a name="return-value"></a>Valor devuelto  
 `S_OK` Si el método es correcto, de lo contrario la `HRESULT` código de error si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Redirección del registro no está habilitada de forma predeterminada. Si habilita esta opción, el acceso al registro se redirige a **HKEY_CURRENT_USER\Software\Classes**.  
  
 La redirección no es global. Solo los marcos de trabajo MFC y ATL se ven afectados por esta redirección del registro.  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  

 ## <a name="afxregcreatekey"></a> AfxRegCreateKey
 Crea la clave del registro especificada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
LONG AFXAPI AfxRegCreateKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);  
```  
  
### <a name="parameters"></a>Parámetros  
 `hKey`  
 Un identificador a una clave del registro abierta.  
  
 `lpSubKey`  
 El nombre de una clave que esta función se abre o se crea.  
  
 `phkResult`  
 Un puntero a una variable que recibe un identificador de la clave creado o abierto.  
  
 `pTM`  
 Puntero a un `CAtlTransactionManager` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en la función, el valor devuelto es un código de error distinto de cero definido en Winerror.h.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxpriv.h  

## <a name="afxregdeletekey"></a> AfxRegDeleteKey
Elimina la clave del registro especificada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
LONG AFXAPI AfxRegDeleteKey(HKEY hKey, LPCTSTR lpSubKey, CAtlTransactionManager* pTM = NULL);  
```  
  
### <a name="parameters"></a>Parámetros  
 `hKey`  
 Un identificador a una clave del registro abierta.  
  
 `lpSubKey`  
 El nombre de la clave que se va a eliminar.  
  
 `pTM`  
 Puntero a un `CAtlTransactionManager` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en la función, el valor devuelto es un código de error distinto de cero definido en Winerror.h.  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxpriv.h  

## <a name="afxregisterpreviewhandler"></a>
Una aplicación auxiliar para registrar un controlador de vista previa.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
BOOL AFXAPI AfxRegisterPreviewHandler(LPCTSTR lpszCLSID, LPCTSTR lpszShortTypeName, LPCTSTR lpszFilterExt);  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszCLSID`  
 Especifica el CLSID del controlador.  
  
 `lpszShortTypeName`  
 Especifica el valor ProgID del controlador.  
  
 `lpszFilterExt`  
 Especifica la extensión de archivo registrado con este controlador.  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdisp.h   

##  <a name="atlregistertypelib"></a>  AtlRegisterTypeLib  
 Esta función se invoca para registrar una biblioteca de tipos.  
  
  
```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `hInstTypeLib`  
 El identificador para la instancia del módulo.  
  
 `lpszIndex`  
 Cadena con el formato "\\\N", donde N es el índice de entero que el tipo del recurso de biblioteca. Puede ser NULL si no se requiere ningún índice.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Esta función auxiliar es usada por [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver) y [CAtlComModule::RegisterTypeLib](../../atl/reference/catlcommodule-class.md#registertypelib).  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h

 ## <a name="afxregopenkey"></a> AfxRegOpenKey
 Abre la clave del registro especificada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
LONG AFXAPI AfxRegOpenKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);  
```  
  
### <a name="parameters"></a>Parámetros  
 `hKey`  
 Un identificador a una clave del registro abierta.  
  
 `lpSubKey`  
 El nombre de una clave que esta función se abre o se crea.  
  
 `phkResult`  
 Un puntero a una variable que recibe un identificador de la clave creada.  
  
 `pTM`  
 Puntero a un `CAtlTransactionManager` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en la función, el valor devuelto es un código de error distinto de cero definido en Winerror.h.  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxpriv.h  

## <a name="afxregopenkeyex"></a>  AfxRegOpenKeyEx
Abre la clave del registro especificada. 

### <a name="syntax"></a>Sintaxis  
  
```  
LONG AFXAPI AfxRegOpenKeyEx(HKEY hKey, LPCTSTR lpSubKey, DWORD ulOptions, REGSAM samDesired, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);  
```  
  
### <a name="parameters"></a>Parámetros  
 `hKey`  
 Un identificador a una clave del registro abierta.  
  
 `lpSubKey`  
 El nombre de una clave que esta función se abre o se crea.  
  
 `ulOptions`  
 Este parámetro está reservado y debe ser cero.  
  
 `samDesired`  
 Máscara que especifica los derechos de acceso deseado a la clave.  
  
 `phkResult`  
 Un puntero a una variable que recibe un identificador de la clave abierta.  
  
 `pTM`  
 Puntero a un `CAtlTransactionManager` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en la función, el valor devuelto es un código de error distinto de cero definido en Winerror.h.  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxpriv.h  

 ## <a name="afxunregisterpreviewhandler"></a> AfxUnregisterPreviewHandler
 Una aplicación auxiliar para anular el registro de un controlador de vista previa.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
BOOL AFXAPI AfxUnRegisterPreviewHandler(LPCTSTR lpszCLSID);  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszCLSID`  
 Especifica el CLSID del controlador se va a anular.  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdisp.h  

## <a name="atlsetperuserregistration"></a> AtlSetPerUserRegistration
Establece si la aplicación redirige el acceso de registro a la **HKEY_CURRENT_USER** (**HKCU**) nodo.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
ATLINLINE ATLAPI AtlSetPerUserRegistration(bool bEnable);  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE` indica que la información de registro se dirige a la **HKCU** nodo; `FALSE` indica que la aplicación escribe información de registro en el nodo de forma predeterminada. El nodo de valor predeterminado es **HKEY_CLASSES_ROOT** (**HKCR**).  
  
### <a name="return-value"></a>Valor devuelto  
 `S_OK` Si el método es correcto, de lo contrario la `HRESULT` código de error si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Redirección del registro no está habilitada de forma predeterminada. Si habilita esta opción, el acceso al registro se redirige a **HKEY_CURRENT_USER\Software\Classes**.  
  
 La redirección no es global. Solo los marcos de trabajo MFC y ATL se ven afectados por esta redirección del registro.  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  

##  <a name="atlunregistertypelib"></a>  AtlUnRegisterTypeLib  
 Esta función se invoca para anular el registro de una biblioteca de tipos.  
  
### <a name="syntax"></a>Sintaxis  
```
ATLAPI AtlUnRegisterTypeLib(
    HINSTANCE hInstTypeLib, 
    LPCOLESTR lpszIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `hInstTypeLib`  
 El identificador para la instancia del módulo.  
  
 `lpszIndex`  
 Cadena con el formato "\\\N", donde N es el índice de entero que el tipo del recurso de biblioteca. Puede ser NULL si no se requiere ningún índice.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Esta función auxiliar es usada por [CAtlComModule::UnRegisterTypeLib](../../atl/reference/catlcommodule-class.md#unregistertypelib) y [AtlComModuleUnregisterServer](#atlcommoduleunregisterserver).  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h

##  <a name="atlloadtypelib"></a>  AtlLoadTypeLib  
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
 `hInstTypeLib`  
 Identificador del módulo asociado a la biblioteca de tipos.  
  
 `lpszIndex`  
 Cadena con el formato "\\\N", donde N es el índice de entero que el tipo del recurso de biblioteca. Puede ser NULL si no se requiere ningún índice.  
  
 *pbstrPath*  
 En la devolución es correcta, contiene la ruta de acceso completa del módulo asociado a la biblioteca de tipos.  
  
 `ppTypeLib`  
 En la devolución es correcta, contiene un puntero a un puntero a la biblioteca de tipos cargados.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Esta función auxiliar es usada por [AtlRegisterTypeLib](#atlregistertypelib) y [AtlUnRegisterTypeLib](#atlunregistertypelib).  
  
##  <a name="atlupdateregistryfromresourced"></a>  AtlUpdateRegistryFromResourceD  
 Esta función quedó en desuso en Visual Studio 2013 y se quitó en Visual Studio 2015.  
  
```
<removed>
```  
  

  
##  <a name="registrydataexchange"></a>  RegistryDataExchange  
 Esta función se invoca para leer el Registro del sistema o escribir en él.  

### <a name="syntax"></a>Sintaxis  
```
HRESULT RegistryDataExchange(
    T* pT,
    enum RDXOperations rdxOp,
    void* pItem = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *pT*  
 Un puntero al objeto actual.  
  
 *rdxOp*  
 Un valor de enumeración que indica la operación que debe realizar la función. Vea la tabla en la sección Comentarios para los valores permitidos.  
  
 `pItem`  
 Puntero a los datos que va a ser de lectura o escritura en el registro. Los datos también pueden representar una clave que se va a eliminar del registro. El valor predeterminado es NULL.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Las macros [BEGIN_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map) y [END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map) expandir a una función que llama a `RegistryDataExchange`.  
  
 Los posibles valores enum que indican que debe realizar la operación de la función se muestran en la tabla siguiente:  
  
|Valor de enumeración|Operación|  
|----------------|---------------|  
|eReadFromReg|Leer datos desde el registro.|  
|eWriteToReg|Escribir datos en el registro.|  
|eDeleteFromReg|Elimine la clave del registro.|  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h

## <a name="see-also"></a>Vea también  
 [Funciones](atl-functions.md) [Macros de intercambio de datos de registro](registry-data-exchange-macros.md)





