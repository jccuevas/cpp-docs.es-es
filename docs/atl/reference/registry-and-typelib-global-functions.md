---
title: Funciones globales del registro y TypeLib | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- RegistryDataExchange function, global functions
ms.assetid: d58b8a4e-975c-4417-8b34-d3c847f679b3
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 9d454f2eac1b29785fe40a480fc43c7c34a861a3
ms.lasthandoff: 02/24/2017

---
# <a name="registry-and-typelib-global-functions"></a>Funciones globales Registry y TypeLib
Estas funciones proporcionan compatibilidad para cargar y registrar una biblioteca de tipos.  
  
> [!IMPORTANT]
>  Las funciones enumeradas en las tablas siguientes no se puede usar en aplicaciones que se ejecutan en el [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
|||  
|-|-|  
|[AtlRegisterTypeLib](#atlregistertypelib)|Esta función se invoca para registrar una biblioteca de tipos.|  
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|Esta función se invoca para anular el registro de una biblioteca de tipos|  
|[AtlLoadTypeLib](#atlloadtypelib)|Esta función se invoca para cargar una biblioteca de tipos.|  
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|Esta función se invoca para actualizar el Registro desde el recurso especificado.|  
|[RegistryDataExchange](#registrydataexchange)|Esta función se invoca para leer el Registro del sistema o escribir en él. Llamado por el [Macros de intercambio de datos del registro](../../atl/reference/registry-data-exchange-macros.md).|  
  
 Estas funciones controlan qué nodo en el registro del programa que se utiliza para almacenar información.  
  
|||  
|-|-|  
|[AtlGetPerUserRegistration](#atlgetperuserregistration)|Recupera si la aplicación redirige el acceso de registro a la **HKEY_CURRENT_USER** ( **HKCU**) nodo.|  
|[AtlSetPerUserRegistration](#atlsetperuserregistration)|Establece si la aplicación redirige el acceso de registro a la **HKEY_CURRENT_USER** ( **HKCU**) nodo.|  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h

## <a name="a-nameatlgetperuserregistrationa-atlgetperuserregistration"></a><a name="atlgetperuserregistration"></a>AtlGetPerUserRegistration
Use esta función para determinar si la aplicación redirige el acceso de registro a la **HKEY_CURRENT_USER** (**HKCU**) nodo.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
ATLINLINE ATLAPI AtlGetPerUserRegistration(bool* pEnabled);  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `pEnabled`  
 `TRUE`indica que la información del registro se dirige a la **HKCU** nodo; `FALSE` indica que la aplicación escribe la información del registro en el nodo predeterminado. El nodo predeterminado es **HKEY_CLASSES_ROOT** (**HKCR**).  
  
### <a name="return-value"></a>Valor devuelto  
 `S_OK`Si el método es correcto, de lo contrario la `HRESULT` código de error si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Redirección del registro no está habilitada de forma predeterminada. Si habilita esta opción, el acceso al registro se redirige a **HKEY_CURRENT_USER\Software\Classes**.  
  
 La redirección no es global. Los marcos de MFC y ATL se ven afectados por esta redirección del registro.  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  

##  <a name="a-nameatlregistertypeliba--atlregistertypelib"></a><a name="atlregistertypelib"></a>AtlRegisterTypeLib  
 Esta función se invoca para registrar una biblioteca de tipos.  
  
  
```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `hInstTypeLib`  
 El identificador de la instancia del módulo.  
  
 `lpszIndex`  
 Cadena con el formato "\\\N", donde N es el índice de entero, el tipo del recurso de biblioteca. Puede ser NULL si no hay ningún índice se requiere.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Se utiliza esta función auxiliar [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver) y [CAtlComModule::RegisterTypeLib](../../atl/reference/catlcommodule-class.md#registertypelib).  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h

## <a name="a-nameatlsetperuserregistrationa-atlsetperuserregistration"></a><a name="atlsetperuserregistration"></a>AtlSetPerUserRegistration
Establece si la aplicación redirige el acceso de registro a la **HKEY_CURRENT_USER** (**HKCU**) nodo.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
ATLINLINE ATLAPI AtlSetPerUserRegistration(bool bEnable);  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`indica que la información del registro se dirige a la **HKCU** nodo; `FALSE` indica que la aplicación escribe la información del registro en el nodo predeterminado. El nodo predeterminado es **HKEY_CLASSES_ROOT** (**HKCR**).  
  
### <a name="return-value"></a>Valor devuelto  
 `S_OK`Si el método es correcto, de lo contrario la `HRESULT` código de error si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Redirección del registro no está habilitada de forma predeterminada. Si habilita esta opción, el acceso al registro se redirige a **HKEY_CURRENT_USER\Software\Classes**.  
  
 La redirección no es global. Los marcos de MFC y ATL se ven afectados por esta redirección del registro.  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  

##  <a name="a-nameatlunregistertypeliba--atlunregistertypelib"></a><a name="atlunregistertypelib"></a>AtlUnRegisterTypeLib  
 Esta función se invoca para anular el registro de una biblioteca de tipos.  
  
### <a name="syntax"></a>Sintaxis  
```
ATLAPI AtlUnRegisterTypeLib(
    HINSTANCE hInstTypeLib, 
    LPCOLESTR lpszIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `hInstTypeLib`  
 El identificador de la instancia del módulo.  
  
 `lpszIndex`  
 Cadena con el formato "\\\N", donde N es el índice de entero, el tipo del recurso de biblioteca. Puede ser NULL si no hay ningún índice se requiere.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Se utiliza esta función auxiliar [CAtlComModule::UnRegisterTypeLib](../../atl/reference/catlcommodule-class.md#unregistertypelib) y [AtlComModuleUnregisterServer](#atlcommoduleunregisterserver).  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h

##  <a name="a-nameatlloadtypeliba--atlloadtypelib"></a><a name="atlloadtypelib"></a>AtlLoadTypeLib  
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
 Cadena con el formato "\\\N", donde N es el índice de entero, el tipo del recurso de biblioteca. Puede ser NULL si no hay ningún índice se requiere.  
  
 *pbstrPath*  
 En la devolución es correcta, contiene la ruta de acceso completa del módulo asociado a la biblioteca de tipos.  
  
 `ppTypeLib`  
 En la devolución es correcta, contiene un puntero a un puntero a la biblioteca de tipos cargados.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Se utiliza esta función auxiliar [AtlRegisterTypeLib](#atlregistertypelib) y [AtlUnRegisterTypeLib](#atlunregistertypelib).  
  
##  <a name="a-nameatlupdateregistryfromresourceda--atlupdateregistryfromresourced"></a><a name="atlupdateregistryfromresourced"></a>AtlUpdateRegistryFromResourceD  
 Esta función quedó en desuso en Visual Studio 2013 y se quitó en Visual Studio 2015.  
  
```
<removed>
```  
  
### <a name="parameters"></a>Parámetros  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameregistrydataexchangea--registrydataexchange"></a><a name="registrydataexchange"></a>RegistryDataExchange  
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
 Un valor de enumeración que indica qué operación debe realizar la función. Vea la tabla en la sección Comentarios para los valores permitidos.  
  
 `pItem`  
 Puntero a los datos que se leen o escriben en el registro. Los datos también pueden representar una clave que se va a eliminar del registro. El valor predeterminado es NULL.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Las macros [BEGIN_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map) y [END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map) expandir a una función que llama a `RegistryDataExchange`.  
  
 Los posibles valores enum que indican que debe realizar la operación de la función se muestran en la tabla siguiente:  
  
|Valor de enumeración|Operación|  
|----------------|---------------|  
|eReadFromReg|Leer datos del registro.|  
|eWriteToReg|Escribir datos en el registro.|  
|eDeleteFromReg|Elimine la clave del registro.|  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h

## <a name="see-also"></a>Vea también  
 [Funciones](atl-functions.md)
 [Macros de intercambio de datos del registro](registry-data-exchange-macros.md)






