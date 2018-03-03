---
title: COleObjectFactory (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleObjectFactory
- AFXDISP/COleObjectFactory
- AFXDISP/COleObjectFactory::COleObjectFactory
- AFXDISP/COleObjectFactory::GetClassID
- AFXDISP/COleObjectFactory::IsLicenseValid
- AFXDISP/COleObjectFactory::IsRegistered
- AFXDISP/COleObjectFactory::Register
- AFXDISP/COleObjectFactory::RegisterAll
- AFXDISP/COleObjectFactory::Revoke
- AFXDISP/COleObjectFactory::RevokeAll
- AFXDISP/COleObjectFactory::UnregisterAll
- AFXDISP/COleObjectFactory::UpdateRegistry
- AFXDISP/COleObjectFactory::UpdateRegistryAll
- AFXDISP/COleObjectFactory::GetLicenseKey
- AFXDISP/COleObjectFactory::OnCreateObject
- AFXDISP/COleObjectFactory::VerifyLicenseKey
- AFXDISP/COleObjectFactory::VerifyUserLicense
dev_langs:
- C++
helpviewer_keywords:
- COleObjectFactory [MFC], COleObjectFactory
- COleObjectFactory [MFC], GetClassID
- COleObjectFactory [MFC], IsLicenseValid
- COleObjectFactory [MFC], IsRegistered
- COleObjectFactory [MFC], Register
- COleObjectFactory [MFC], RegisterAll
- COleObjectFactory [MFC], Revoke
- COleObjectFactory [MFC], RevokeAll
- COleObjectFactory [MFC], UnregisterAll
- COleObjectFactory [MFC], UpdateRegistry
- COleObjectFactory [MFC], UpdateRegistryAll
- COleObjectFactory [MFC], GetLicenseKey
- COleObjectFactory [MFC], OnCreateObject
- COleObjectFactory [MFC], VerifyLicenseKey
- COleObjectFactory [MFC], VerifyUserLicense
ms.assetid: ab179c1e-4af2-44aa-a576-37c48149b427
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f853939ae7960dd865f560d480366ff95a73a990
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="coleobjectfactory-class"></a>COleObjectFactory (clase)
Implementa el generador de clases OLE, que crea objetos OLE tales como servidores, objetos de automatización y documentos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleObjectFactory : public CCmdTarget  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleObjectFactory::COleObjectFactory](#coleobjectfactory)|Construye un objeto `COleObjectFactory`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleObjectFactory::GetClassID](#getclassid)|Devuelve la OLE identificador de clase de los objetos que crea este generador.|  
|[COleObjectFactory::IsLicenseValid](#islicensevalid)|Determina si la licencia del control es válida.|  
|[COleObjectFactory::IsRegistered](#isregistered)|Indica si el generador de objetos está registrado con la DLL del sistema OLE.|  
|[COleObjectFactory::Register](#register)|Registra este generador de objetos con la archivos DLL del sistema OLE.|  
|[COleObjectFactory:: RegisterAll](#registerall)|Registra todos los generadores de objetos de la aplicación con archivos DLL del sistema OLE.|  
|[COleObjectFactory::Revoke](#revoke)|Revoca el registro del generador de este objeto con las DLL del sistema OLE.|  
|[COleObjectFactory::RevokeAll](#revokeall)|Revoca los registros de generadores del objeto de la aplicación con las DLL del sistema OLE.|  
|[COleObjectFactory::UnregisterAll](#unregisterall)|Anula el registro de todos los generadores de objetos de la aplicación.|  
|[COleObjectFactory::UpdateRegistry](#updateregistry)|Registra este generador de objetos con el registro del sistema OLE.|  
|[:: UpdateRegistryAll](#updateregistryall)|Registra todos los generadores de objetos de la aplicación con el registro del sistema OLE.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleObjectFactory::GetLicenseKey](#getlicensekey)|Solicita una clave única de archivo DLL del control.|  
|[COleObjectFactory::OnCreateObject](#oncreateobject)|Lo llama el marco para crear un nuevo objeto de tipo de este generador.|  
|[COleObjectFactory::VerifyLicenseKey](#verifylicensekey)|Comprueba que la clave incrustada en el control coincide con la clave que se incrustan en el contenedor.|  
|[COleObjectFactory::VerifyUserLicense](#verifyuserlicense)|Comprueba que el control tiene licencia para su uso en tiempo de diseño.|  
  
## <a name="remarks"></a>Comentarios  
 La `COleObjectFactory` clase tiene funciones de miembro para llevar a cabo las siguientes funciones:  
  
-   Administrar el registro de objetos.  
  
-   Actualizando el registro del sistema OLE, así como el registro de tiempo de ejecución que le informa de OLE que los objetos están ejecutando y está listo para recibir mensajes.  
  
-   Aplicación del Administrador de licencias mediante la limitación de uso del control para los desarrolladores con licencia en tiempo de diseño y las aplicaciones con licencia en tiempo de ejecución.  
  
-   Registrar generadores de objeto de control con el registro del sistema OLE.  
  
 Para obtener más información acerca de la creación de objetos, vea los artículos [objetos de datos y orígenes de datos (OLE)](../../mfc/data-objects-and-data-sources-ole.md) y [objetos de datos y orígenes de datos: creación y destrucción](../../mfc/data-objects-and-data-sources-creation-and-destruction.md). Para obtener más información acerca del registro, vea el artículo [registro](../../mfc/registration.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleObjectFactory`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdisp.h  
  
##  <a name="coleobjectfactory"></a>COleObjectFactory::COleObjectFactory  
 Construye un `COleObjectFactory` objeto, lo inicializa como un generador de objetos anular el registro y lo agrega a la lista de generadores.  
  
```  
COleObjectFactory(
    REFCLSID clsid,  
    CRuntimeClass* pRuntimeClass,  
    BOOL bMultiInstance,  
    LPCTSTR lpszProgID);

 
COleObjectFactory(
    REFCLSID clsid,  
    CRuntimeClass* pRuntimeClass,  
    BOOL bMultiInstance,  
    int nFlags,  
    LPCTSTR lpszProgID);
```  
  
### <a name="parameters"></a>Parámetros  
 `clsid`  
 Referencia al identificador de clase OLE representa este generador de objetos.  
  
 `pRuntimeClass`  
 Puntero a la clase en tiempo de ejecución de los objetos de C++ que se puede crear este generador.  
  
 `bMultiInstance`  
 Indica si una sola instancia de la aplicación puede admitir varias creaciones de instancias. Si **TRUE**, varias instancias de la aplicación se inicien para que cada solicitud crear un objeto.  
  
 `nFlags`  
 Contiene uno o varios de los siguientes indicadores:  
  
- **afxRegDefault** establece el modelo de subprocesos en ThreadingModel = apartamento.  
  
- **afxRegInsertable** permite que el control aparezca en el **Insertar objeto** cuadro de diálogo de objetos OLE.  
  
- `afxRegApartmentThreading`Establece el modelo de subprocesos en el registro para ThreadingModel = apartamento.  
  
- **afxRegFreeThreading** establece el modelo de subprocesos en el registro para ThreadingModel = libre.  
  
     Puede combinar los dos indicadores `afxRegApartmentThreading` y `afxRegFreeThreading` para establecer ThreadingModel = Both. Vea [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) en el SDK de Windows para obtener más información sobre el registro del modelo de subprocesos.  
  
 `lpszProgID`  
 Puntero a una cadena que contiene un identificador de programa verbales, como "Microsoft Excel".  
  
### <a name="remarks"></a>Comentarios  
 Para usar el objeto, sin embargo, debe registrarlo.  
  
 Para obtener más información, consulte [clave CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) del SDK de Windows.  
  
##  <a name="getclassid"></a>COleObjectFactory::GetClassID  
 Devuelve una referencia al identificador de clase OLE representa este generador.  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Representa la referencia al identificador de clase OLE este generador.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [clave CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) del SDK de Windows.  
  
##  <a name="getlicensekey"></a>COleObjectFactory::GetLicenseKey  
 Solicita una clave de licencia única del archivo DLL del control y lo almacena en la `BSTR` señalada por `pbstrKey`.  
  
```  
virtual BOOL GetLicenseKey(
    DWORD dwReserved,  
    BSTR* pbstrKey);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwReserved`  
 Reservado para un uso futuro.  
  
 `pbstrKey`  
 Puntero a un `BSTR` que almacenará la clave de licencia.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la cadena de clave de licencia no es **NULL**; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función devuelve 0 y almacena nada en la `BSTR`. Si usas ActiveX ControlWizard de MFC para crear el proyecto, ControlWizard proporciona una invalidación que recupera la clave de licencia del control.  
  
##  <a name="islicensevalid"></a>COleObjectFactory::IsLicenseValid  
 Determina si la licencia del control es válida.  
  
```  
BOOL IsLicenseValid();
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si realizado correctamente; lo contrario, false.  
  
##  <a name="isregistered"></a>COleObjectFactory::IsRegistered  
 Devuelve un valor distinto de cero si el generador está registrado con la DLL del sistema OLE.  
  
```  
virtual BOOL IsRegistered() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la fábrica está registrada; en caso contrario es 0.  
  
##  <a name="oncreateobject"></a>COleObjectFactory::OnCreateObject  
 Lo llama el marco para crear un nuevo objeto.  
  
```  
virtual CCmdTarget* OnCreateObject();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al objeto creado. Puede producir una excepción de memoria si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función para crear el objeto de algo distinto de la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) pasada al constructor.  
  
##  <a name="register"></a>COleObjectFactory::Register  
 Registra este generador de objetos con la archivos DLL del sistema OLE.  
  
```  
virtual BOOL Register();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se ha registrado correctamente el generador; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se suele llamar [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) cuando se inicia la aplicación.  
  
##  <a name="registerall"></a>COleObjectFactory:: RegisterAll  
 Registra todos los generadores de objetos de la aplicación con las DLL del sistema OLE.  
  
```  
static BOOL PASCAL RegisterAll();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se ha registrado correctamente los generadores; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se suele llamar [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) cuando se inicia la aplicación.  
  
##  <a name="revoke"></a>COleObjectFactory::Revoke  
 Revoca el registro del generador de este objeto con las DLL del sistema OLE.  
  
```  
void Revoke();
```  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a esta función automáticamente antes de que finalice la aplicación. Si es necesario, puede llamarlo desde una invalidación de [CWinApp:: ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).  
  
##  <a name="revokeall"></a>COleObjectFactory::RevokeAll  
 Revoca todos los registros de generadores del objeto de la aplicación con las DLL del sistema OLE.  
  
```  
static void PASCAL RevokeAll();
```  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a esta función automáticamente antes de que finalice la aplicación. Si es necesario, puede llamarlo desde una invalidación de [CWinApp:: ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).  
  
##  <a name="unregisterall"></a>COleObjectFactory::UnregisterAll  
 Anula el registro de todos los generadores de objetos de la aplicación.  
  
```  
static BOOL PASCAL UnregisterAll();
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si es correcto; en caso contrario, FALSE.  
  
##  <a name="updateregistry"></a>COleObjectFactory::UpdateRegistry  
 Registra todos los generadores de objetos de la aplicación con el registro del sistema OLE.  
  
```  
void UpdateRegistry(LPCTSTR lpszProgID = NULL);  
virtual BOOL UpdateRegistry(BOOL bRegister);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszProgID`  
 Puntero a una cadena que contiene el identificador de programa legible para el usuario, por ejemplo, "Excel.Document.5".  
  
 `bRegister`  
 Determina si el generador de objetos de la clase de control es que se registrará.  
  
### <a name="remarks"></a>Comentarios  
 Siguen las discusiones breves de las dos formas para esta función:  
  
- **UpdateRegistry (** `lpszProgID` **)** registra este generador de objetos con el registro del sistema OLE. Esta función se suele llamar [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) cuando se inicia la aplicación.  
  
- **UpdateRegistry (** `bRegister` **)** esta forma de la función es reemplazable. Si `bRegister` es **TRUE**, esta función registra la clase de control con el registro del sistema. En caso contrario, anula el registro de la clase.  
  
     Si usas ActiveX ControlWizard de MFC para crear el proyecto, ControlWizard proporciona una invalidación para esta función virtual pura.  
  
##  <a name="updateregistryall"></a>:: UpdateRegistryAll  
 Registra todos los generadores de objetos de la aplicación con el registro del sistema OLE.  
  
```  
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bRegister`  
 Determina si el generador de objetos de la clase de control es que se registrará.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se han actualizado correctamente los generadores; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se suele llamar [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) cuando se inicia la aplicación.  
  
##  <a name="verifylicensekey"></a>COleObjectFactory::VerifyLicenseKey  
 Comprueba que el contenedor tiene licencia para utilizar el control OLE.  
  
```  
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```  
  
### <a name="parameters"></a>Parámetros  
 `bstrKey`  
 Un `BSTR` almacenar la versión del contenedor de la cadena de licencia.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la licencia de tiempo de ejecución es válida; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 La versión predeterminada llama [GetLicenseKey](#getlicensekey) para obtener una copia del control de la cadena de licencia y lo compara con la cadena de `bstrKey`. Si las dos cadenas coinciden, la función devuelve un valor distinto de cero; en caso contrario, devuelve 0.  
  
 Puede invalidar esta función para proporcionar una verificación personalizada de la licencia.  
  
 La función [VerifyUserLicense](#verifyuserlicense) comprueba la licencia en tiempo de diseño.  
  
##  <a name="verifyuserlicense"></a>COleObjectFactory::VerifyUserLicense  
 Comprueba la licencia en tiempo de diseño para el control OLE.  
  
```  
virtual BOOL VerifyUserLicense();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la licencia de tiempo de diseño no es válida; en caso contrario es 0.  
  
## <a name="see-also"></a>Vea también  
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleTemplateServer (clase)](../../mfc/reference/coletemplateserver-class.md)
