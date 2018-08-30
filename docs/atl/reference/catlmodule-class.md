---
title: CAtlModule (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAtlModule class
ms.assetid: 63fe02f1-4c4b-4e7c-ae97-7ad7b4252415
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4412e30316bd2d5f43eac4dddb062adb11dc6f6e
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210006"
---
# <a name="catlmodule-class"></a>CAtlModule (clase)
Esta clase proporciona métodos utilizados por varias clases de módulo ATL.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class ATL_NO_VTABLE CAtlModule : public _ATL_MODULE
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlModule::CAtlModule](#catlmodule)|El constructor.|  
|[CAtlModule:: ~ CAtlModule](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)|Invalide este método para agregar parámetros a la asignación de reemplazo de componente de registro de ATL (registrador).|  
|[CAtlModule::AddTermFunc](#addtermfunc)|Agrega una nueva función se llama cuando finaliza el módulo.|  
|[CAtlModule::GetGITPtr](#getgitptr)|Devuelve el puntero de interfaz Global.|  
|[CAtlModule::GetLockCount](#getlockcount)|Devuelve el recuento de bloqueos.|  
|[CAtlModule::Lock](#lock)|Incrementa el recuento de bloqueos.|  
|[CAtlModule::Term](#term)|Libera a todos los miembros de datos.|  
|[CAtlModule::Unlock](#unlock)|Reduce el recuento de bloqueos.|  
|[CAtlModule:: UpdateRegistryFromResourceD](#updateregistryfromresourced)|Se ejecuta la secuencia de comandos contenida en un recurso para registrar o anular el registro de un objeto especificado.|  
|[CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)|Este método es invocado por `UpdateRegistryFromResourceD` para realizar la actualización del registro.|  
|[CAtlModule:: UpdateRegistryFromResourceS](#updateregistryfromresources)|Se ejecuta la secuencia de comandos contenida en un recurso para registrar o anular el registro de un objeto especificado. Este método se vincula estáticamente para el componente de registro de ATL.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlModule::m_libid](#m_libid)|Contiene el GUID del módulo actual.|  
|[CAtlModule::m_pGIT](#m_pgit)|Puntero a la tabla de interfaz Global.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase se utiliza por [CAtlDllModuleT (clase)](../../atl/reference/catldllmodulet-class.md), [CAtlExeModuleT (clase)](../../atl/reference/catlexemodulet-class.md), y [CAtlServiceModuleT (clase)](../../atl/reference/catlservicemodulet-class.md) para proporcionar compatibilidad con las aplicaciones de la DLL, aplicaciones EXE, y Servicios de Windows, respectivamente.  
  
 Para obtener más información sobre los módulos de ATL, vea [clases de módulo ATL](../../atl/atl-module-classes.md).  
  
 Esta clase reemplaza el atributo obsolete [CComModule (clase)](../../atl/reference/ccommodule-class.md) usado en versiones anteriores de ATL.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 `CAtlModule`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="addcommonrgsreplacements"></a>  CAtlModule::AddCommonRGSReplacements  
 Invalide este método para agregar parámetros a la asignación de reemplazo de componente de registro de ATL (registrador).  
  
```
virtual HRESULT AddCommonRGSReplacements(IRegistrarBase* /* pRegistrar*/) throw() = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 *pRegistrar*  
 Reservado.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Parámetros reemplazables permiten que un cliente del registrador especificar los datos de tiempo de ejecución. Para ello, el registrador mantiene un mapa de reemplazo en el que escribe los valores asociados con los parámetros reemplazables en el script. El registrador realiza estas entradas en tiempo de ejecución.  
  
 Vea el tema [utilizar parámetros reemplazables (el preprocesador del registrador)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) para obtener más detalles.  
  
##  <a name="addtermfunc"></a>  CAtlModule::AddTermFunc  
 Agrega una nueva función se llama cuando finaliza el módulo.  
  
```
HRESULT AddTermFunc(_ATL_TERMFUNC* pFunc, DWORD_PTR dw) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *pFunc*  
 Puntero a la función para agregar.  
  
 *almacenamiento de datos*  
 Datos definidos por el usuario, se pasa a la función.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
##  <a name="catlmodule"></a>  CAtlModule::CAtlModule  
 El constructor.  
  
```
CAtlModule() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Inicializa a los miembros de datos e inicia una sección crítica en torno a los subprocesos del módulo.  
  
##  <a name="dtor"></a>  CAtlModule:: ~ CAtlModule  
 Destructor.  
  
```
~CAtlModule() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera a todos los miembros de datos.  
  
##  <a name="getgitptr"></a>  CAtlModule::GetGITPtr  
 Recupera un puntero a la tabla de interfaz Global.  
  
```
virtual HRESULT GetGITPtr(IGlobalInterfaceTable** ppGIT) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *ppGIT*  
 Puntero a la variable que recibirá el puntero a la tabla de interfaz Global.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un código de error en caso de error. Si se devuelve E_POINTER *ppGIT* es igual a NULL.  
  
### <a name="remarks"></a>Comentarios  
 Si no existe el objeto de tabla de interfaz Global, se crea y se almacena su dirección en la variable miembro [CAtlModule::m_pGIT](#m_pgit).  
  
 En las compilaciones de depuración, se producirá un error de aserción si *ppGIT* es igual a NULL, o si no se puede obtener el puntero de la tabla de interfaz Global.  
  
 Consulte [IGlobalInterfaceTable](/windows/desktop/api/objidl/nn-objidl-iglobalinterfacetable) para obtener información sobre la tabla de interfaz Global.  
  
##  <a name="getlockcount"></a>  CAtlModule::GetLockCount  
 Devuelve el recuento de bloqueos.  
  
```
virtual LONG GetLockCount() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el recuento de bloqueos. Este valor puede ser útil para el diagnóstico y depuración.  
  
##  <a name="lock"></a>  CAtlModule::Lock  
 Incrementa el recuento de bloqueos.  
  
```
virtual LONG Lock() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Incrementa el recuento de bloqueos y devuelve el valor actualizado. Este valor puede ser útil para el diagnóstico y depuración.  
  
##  <a name="m_libid"></a>  CAtlModule::m_libid  
 Contiene el GUID del módulo actual.  
  
```
static GUID m_libid;
```  
  
##  <a name="m_pgit"></a>  CAtlModule::m_pGIT  
 Puntero a la tabla de interfaz Global.  
  
```
IGlobalInterfaceTable* m_pGIT;
```  
  
##  <a name="term"></a>  CAtlModule::Term  
 Libera a todos los miembros de datos.  
  
```
void Term() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera a todos los miembros de datos. El destructor llama a este método.  
  
##  <a name="unlock"></a>  CAtlModule::Unlock  
 Reduce el recuento de bloqueos.  
  
```
virtual LONG Unlock() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Disminuye el recuento de bloqueos y devuelve el valor actualizado. Este valor puede ser útil para el diagnóstico y depuración.  
  
##  <a name="updateregistryfromresourced"></a>  CAtlModule:: UpdateRegistryFromResourceD  
 Se ejecuta la secuencia de comandos contenida en un recurso para registrar o anular el registro de un objeto especificado.  
  
```
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
 *lpszRes*  
 Un nombre de recurso.  
  
 *nResID*  
 Un identificador de recurso.  
  
 *bInscríbase al*  
 TRUE si se debe registrar el objeto; FALSE en caso contrario.  
  
 *pMapEntries*  
 Un puntero al mapa de reemplazo almacenar valores asociados con parámetros reemplazables del script. ATL utiliza automáticamente el módulo %. Para usar parámetros reemplazables adicionales, consulte [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). En caso contrario, utilice el valor predeterminado es NULL.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Se ejecuta la secuencia de comandos contenida en el recurso especificado por *lpszRes o nResID*. Si *bInscríbase al* es TRUE, este método registra el objeto en el registro del sistema; en caso contrario, se quita el objeto desde el registro.  
  
 Para vincular estáticamente para el componente de registro de ATL (registrador), consulte [CAtlModule:: UpdateRegistryFromResourceS](#updateregistryfromresources).  
  
 Este método llama a [CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper) y [IRegistrar::ResourceUnregister](iregistrar-class.md#resourceunregister).  
  
##  <a name="updateregistryfromresourcedhelper"></a>  CAtlModule::UpdateRegistryFromResourceDHelper  
 Este método es invocado por `UpdateRegistryFromResourceD` para realizar la actualización del registro.  
  
```
inline HRESULT WINAPI UpdateRegistryFromResourceDHelper(  
    LPCOLESTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszRes*  
 Un nombre de recurso.  
  
 *bInscríbase al*  
 Indica si se debe registrar el objeto.  
  
 *pMapEntries*  
 Un puntero al mapa de reemplazo almacenar valores asociados con parámetros reemplazables del script. ATL utiliza automáticamente el módulo %. Para usar parámetros reemplazables adicionales, consulte [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). En caso contrario, utilice el valor predeterminado es NULL.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método proporciona la implementación de [CAtlModule:: UpdateRegistryFromResourceD](#updateregistryfromresourced).  
  
##  <a name="updateregistryfromresources"></a>  CAtlModule:: UpdateRegistryFromResourceS  
 Se ejecuta la secuencia de comandos contenida en un recurso para registrar o anular el registro de un objeto especificado. Este método se vincula estáticamente para el componente de registro de ATL.  
  
```
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
 *nResID*  
 Un identificador de recurso.  
  
 *lpszRes*  
 Un nombre de recurso.  
  
 *bInscríbase al*  
 Indica si se debe registrar el script del recurso.  
  
 *pMapEntries*  
 Un puntero al mapa de reemplazo almacenar valores asociados con parámetros reemplazables del script. ATL utiliza automáticamente el módulo %. Para usar parámetros reemplazables adicionales, consulte [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). En caso contrario, utilice el valor predeterminado es NULL.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Similar a [CAtlModule:: UpdateRegistryFromResourceD](#updateregistryfromresourced) excepto `CAtlModule::UpdateRegistryFromResourceS` crea un vínculo estático para el componente de registro de ATL (registrador).  
  
## <a name="see-also"></a>Vea también  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)   
 [Información general de clases](../../atl/atl-class-overview.md)   
 [Clases de módulo](../../atl/atl-module-classes.md)   
 [Componente de registro (registrador)](../../atl/atl-registry-component-registrar.md)  
