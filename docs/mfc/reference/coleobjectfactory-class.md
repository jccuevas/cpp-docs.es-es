---
title: COleObjectFactory (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
- OLE, class factory
- OLE class factory
- COleObjectFactory class
- objects [C++], creating OLE
- OLE objects
- object creation, OLE objects
- class factories, COleObjectFactory class
- OLE objects, creating
ms.assetid: ab179c1e-4af2-44aa-a576-37c48149b427
caps.latest.revision: 21
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
ms.openlocfilehash: 643d17ccdefb60b561e7e5488753a6dbf778c69f
ms.lasthandoff: 02/24/2017

---
# <a name="coleobjectfactory-class"></a>COleObjectFactory (clase)
Implementa el generador de clases OLE, que crea objetos OLE tales como servidores, objetos de automatización y documentos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleObjectFactory : public CCmdTarget  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleObjectFactory::COleObjectFactory](#coleobjectfactory)|Construye un objeto `COleObjectFactory`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleObjectFactory::GetClassID](#getclassid)|Devuelve la OLE identificador de clase de los objetos que crea este generador.|  
|[COleObjectFactory::IsLicenseValid](#islicensevalid)|Determina si la licencia del control es válida.|  
|[COleObjectFactory::IsRegistered](#isregistered)|Indica si el generador de objetos está registrado con la DLL del sistema OLE.|  
|[COleObjectFactory::Register](#register)|Registra este generador de objetos con la DLL del sistema OLE.|  
|[COleObjectFactory:: RegisterAll](#registerall)|Registra todos los generadores de objetos de la aplicación con la DLL del sistema OLE.|  
|[COleObjectFactory::Revoke](#revoke)|Revoca el registro del generador de este objeto con la DLL del sistema OLE.|  
|[COleObjectFactory::RevokeAll](#revokeall)|Revoca los registros de las fábricas de objeto de la aplicación con las DLL del sistema OLE.|  
|[COleObjectFactory::UnregisterAll](#unregisterall)|Anula el registro de todos los generadores de objetos de la aplicación.|  
|[COleObjectFactory::UpdateRegistry](#updateregistry)|Registra este generador de objetos con el registro del sistema OLE.|  
|[:: UpdateRegistryAll](#updateregistryall)|Registra todos los generadores de objetos de la aplicación con el registro del sistema OLE.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleObjectFactory::GetLicenseKey](#getlicensekey)|Solicita una clave única del archivo DLL del control.|  
|[COleObjectFactory::OnCreateObject](#oncreateobject)|Llamado por el marco para crear un nuevo objeto de tipo de este generador.|  
|[COleObjectFactory::VerifyLicenseKey](#verifylicensekey)|Comprueba que la clave incrustada en el control coincide con la clave incrustada en el contenedor.|  
|[COleObjectFactory::VerifyUserLicense](#verifyuserlicense)|Comprueba que el control tiene licencia para su uso en tiempo de diseño.|  
  
## <a name="remarks"></a>Comentarios  
 La `COleObjectFactory` clase tiene funciones de miembro para llevar a cabo las siguientes funciones:  
  
-   Administrar el registro de objetos.  
  
-   Actualizar el registro del sistema OLE, así como el registro de tiempo de ejecución que le informa de OLE que los objetos se están ejecutando y está listo para recibir mensajes.  
  
-   Aplicación de licencias limitando el uso del control a los desarrolladores con licencia en tiempo de diseño y las aplicaciones con licencia en tiempo de ejecución.  
  
-   Registrar generadores de objeto de control con el registro del sistema OLE.  
  
 Para obtener más información acerca de la creación de objetos, consulte los artículos [objetos de datos y orígenes de datos (OLE)](../../mfc/data-objects-and-data-sources-ole.md) y [objetos de datos y orígenes de datos: creación y destrucción](../../mfc/data-objects-and-data-sources-creation-and-destruction.md). Para obtener más información acerca del registro, consulte el artículo [registro](../../mfc/registration.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleObjectFactory`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdisp.h  
  
##  <a name="coleobjectfactory"></a>COleObjectFactory::COleObjectFactory  
 Construye un `COleObjectFactory` objeto, inicializa como un generador de objetos no registrados y lo agrega a la lista de generadores.  
  
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
 Indica si una sola instancia de la aplicación puede admitir varias creaciones de instancias. Si **TRUE**, se ejecutan varias instancias de la aplicación para que cada solicitud crear un objeto.  
  
 `nFlags`  
 Contiene uno o varios de los siguientes indicadores:  
  
- **afxRegDefault** establece el modelo de subprocesos en ThreadingModel = apartamento.  
  
- **afxRegInsertable** permite que el control aparezca en el **Insertar objeto** cuadro de diálogo de objetos OLE.  
  
- `afxRegApartmentThreading`Establece el modelo de subprocesos en el registro para ThreadingModel = apartamento.  
  
- **afxRegFreeThreading** establece el modelo de subprocesos en el registro para ThreadingModel = gratis.  
  
     Puede combinar los dos indicadores `afxRegApartmentThreading` y `afxRegFreeThreading` para establecer ThreadingModel = Both. Consulte [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener más información sobre los subprocesos de registro del modelo.  
  
 `lpszProgID`  
 Puntero a una cadena que contiene un identificador de programa verbal, como "Microsoft Excel".  
  
### <a name="remarks"></a>Comentarios  
 Para utilizar el objeto, sin embargo, debe registrarlo.  
  
 Para obtener más información, consulte [clave CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getclassid"></a>COleObjectFactory::GetClassID  
 Devuelve una referencia al identificador de clase OLE representa este generador.  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Representa la referencia al identificador de clase OLE este generador.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [clave CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getlicensekey"></a>COleObjectFactory::GetLicenseKey  
 Solicita una clave de licencia única del archivo DLL del control y lo almacena en el `BSTR` señala `pbstrKey`.  
  
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
 Distinto de cero si la cadena de la clave de licencia no es **NULL**; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función devuelve 0 y se almacena nada en la `BSTR`. Si utiliza MFC ActiveX ControlWizard para crear el proyecto, ControlWizard proporciona una invalidación que recupera la clave de licencia del control.  
  
##  <a name="islicensevalid"></a>COleObjectFactory::IsLicenseValid  
 Determina si la licencia del control es válida.  
  
```  
BOOL IsLicenseValid();
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si realizado correctamente; en caso contrario, false.  
  
##  <a name="isregistered"></a>COleObjectFactory::IsRegistered  
 Devuelve un valor distinto de cero si el generador está registrado con la DLL del sistema OLE.  
  
```  
virtual BOOL IsRegistered() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el generador está registrado; en caso contrario, 0.  
  
##  <a name="oncreateobject"></a>COleObjectFactory::OnCreateObject  
 Llamado por el marco para crear un nuevo objeto.  
  
```  
virtual CCmdTarget* OnCreateObject();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al objeto creado. Puede producir una excepción de memoria si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función para crear el objeto desde algo distinto de la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) pasada al constructor.  
  
##  <a name="register"></a>COleObjectFactory::Register  
 Registra este generador de objetos con la DLL del sistema OLE.  
  
```  
virtual BOOL Register();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se ha registrado correctamente el generador; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se suele llamar [InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) cuando se inicia la aplicación.  
  
##  <a name="registerall"></a>COleObjectFactory:: RegisterAll  
 Registra todos los generadores de objetos de la aplicación con las DLL del sistema OLE.  
  
```  
static BOOL PASCAL RegisterAll();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se ha registrado correctamente las fábricas; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se suele llamar [InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) cuando se inicia la aplicación.  
  
##  <a name="revoke"></a>COleObjectFactory::Revoke  
 Revoca el registro del generador de este objeto con la DLL del sistema OLE.  
  
```  
void Revoke();
```  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a esta función automáticamente antes de que finalice la aplicación. Si es necesario, puede llamarlo desde un reemplazo de [CWinApp:: ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).  
  
##  <a name="revokeall"></a>COleObjectFactory::RevokeAll  
 Revoca todos los registros de las fábricas de objeto de la aplicación con las DLL del sistema OLE.  
  
```  
static void PASCAL RevokeAll();
```  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a esta función automáticamente antes de que finalice la aplicación. Si es necesario, puede llamarlo desde un reemplazo de [CWinApp:: ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).  
  
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
 Puntero a una cadena que contiene el identificador de programa legible, como "Excel.Document.5."  
  
 `bRegister`  
 Determina si el generador de objetos de la clase de control es que se registrará.  
  
### <a name="remarks"></a>Comentarios  
 Siguen las discusiones breves de las dos formas para esta función:  
  
- **UpdateRegistry (** `lpszProgID` **)** registra este generador de objetos con el registro del sistema OLE. Esta función se suele llamar [InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) cuando se inicia la aplicación.  
  
- **UpdateRegistry (** `bRegister` **)** esta forma de la función es reemplazable. Si `bRegister` es **TRUE**, esta función registra la clase de control con el registro del sistema. De lo contrario, anula el registro de la clase.  
  
     Si utiliza MFC ActiveX ControlWizard para crear el proyecto, ControlWizard proporciona una invalidación para esta función virtual pura.  
  
##  <a name="updateregistryall"></a>:: UpdateRegistryAll  
 Registra todos los generadores de objetos de la aplicación con el registro del sistema OLE.  
  
```  
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bRegister`  
 Determina si el generador de objetos de la clase de control es que se registrará.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se ha actualizado correctamente los generadores; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se suele llamar [InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) cuando se inicia la aplicación.  
  
##  <a name="verifylicensekey"></a>COleObjectFactory::VerifyLicenseKey  
 Comprueba que el contenedor tiene licencia para utilizar el control OLE.  
  
```  
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```  
  
### <a name="parameters"></a>Parámetros  
 `bstrKey`  
 Un `BSTR` almacenar la versión del contenedor de la cadena de licencia.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la licencia de tiempo de ejecución es válida; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La versión predeterminada llama [GetLicenseKey](#getlicensekey) para obtener una copia del control de la cadena de licencia y la compara con la cadena de `bstrKey`. Si las dos cadenas coinciden, la función devuelve un valor distinto de cero; de lo contrario, devuelve 0.  
  
 Puede reemplazar esta función para proporcionar una verificación personalizada de la licencia.  
  
 La función [VerifyUserLicense](#verifyuserlicense) comprueba la licencia en tiempo de diseño.  
  
##  <a name="verifyuserlicense"></a>COleObjectFactory::VerifyUserLicense  
 Comprueba la licencia en tiempo de diseño para el control OLE.  
  
```  
virtual BOOL VerifyUserLicense();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la licencia de tiempo de diseño no es válida; en caso contrario, 0.  
  
## <a name="see-also"></a>Vea también  
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [COleTemplateServer (clase)](../../mfc/reference/coletemplateserver-class.md)

