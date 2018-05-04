---
title: Clase CComClassFactory2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComClassFactory2
- ATLCOM/ATL::CComClassFactory2
- ATLCOM/ATL::CComClassFactory2::CreateInstance
- ATLCOM/ATL::CComClassFactory2::CreateInstanceLic
- ATLCOM/ATL::CComClassFactory2::GetLicInfo
- ATLCOM/ATL::CComClassFactory2::LockServer
- ATLCOM/ATL::CComClassFactory2::RequestLicKey
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactory2 class
ms.assetid: 19b66fd6-b9ed-47a0-822c-8132184f5a3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: da2b47290d3d0be525ca65b16733c9f42835d24e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="ccomclassfactory2-class"></a>Clase CComClassFactory2
Esta clase implementa la [IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720) interfaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class license>  
class CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```  
  
#### <a name="parameters"></a>Parámetros  
 *Licencia*  
 Una clase que implementa las funciones estáticas siguientes:  
  
- **estática VerifyLicenseKey BOOL (BSTR** `bstr` **);**  
  
- **estática GetLicenseKey BOOL (DWORD** `dwReserved` **, BSTR\***  `pBstr` **);**  
  
- **static BOOL IsLicenseValid ();**  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComClassFactory2::CreateInstance](#createinstance)|Crea un objeto del CLSID especificado.|  
|[CComClassFactory2::CreateInstanceLic](#createinstancelic)|Debido a una clave de licencia, crea un objeto del CLSID especificado.|  
|[CComClassFactory2::GetLicInfo](#getlicinfo)|Recupera la información que describe las capacidades de licencias de la fábrica de clase.|  
|[CComClassFactory2::LockServer](#lockserver)|Bloquea el generador de clases en la memoria.|  
|[CComClassFactory2::RequestLicKey](#requestlickey)|Crea y devuelve una clave de licencia.|  
  
## <a name="remarks"></a>Comentarios  
 `CComClassFactory2` implementa el [IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720) interfaz, que es una extensión de [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364). **IClassFactory2** controles objeto creación a través de una licencia. Una ejecución de fábrica de clase en un equipo con licencia puede proporcionar una clave de licencia de tiempo de ejecución. Esta clave de licencia permite que una aplicación crear instancias de objetos cuando no existe una licencia completo de equipo.  
  
 Objetos ATL normalmente adquieren un generador de clases derivando de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), que declara [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases de forma predeterminada. Usar `CComClassFactory2`, especifique el [macro DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) macro en la definición de clase del objeto. Por ejemplo:  
  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]  
  
 **CMyLicense**, el parámetro de plantilla `CComClassFactory2`, debe implementar las funciones estáticas `VerifyLicenseKey`, `GetLicenseKey`, y `IsLicenseValid`. El siguiente es un ejemplo de una clase simple de licencia:  
  
 [!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]  
  
 `CComClassFactory2` se deriva de ambos **CComClassFactory2Base** y *licencia*. **CComClassFactory2Base**, a su vez, deriva de **IClassFactory2** y **CComObjectRootEx\< CComGlobalsThreadModel >**.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CComObjectRootBase`  
  
 `license`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory2`  
  
 `CComClassFactory2`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="createinstance"></a>  CComClassFactory2::CreateInstance  
 Crea un objeto del CLSID especificado y recupera un puntero de interfaz a este objeto.  
  
```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```  
  
### <a name="parameters"></a>Parámetros  
 `pUnkOuter`  
 [in] Si el objeto se crea como parte de un agregado, a continuación, `pUnkOuter` debe ser el desconocido externo. En caso contrario, `pUnkOuter` debe ser **NULL**.  
  
 `riid`  
 [in] El IID de la interfaz solicitada. Si `pUnkOuter` no es **NULL**, `riid` debe ser **IID_IUnknown**.  
  
 `ppvObj`  
 [out] Un puntero al puntero de interfaz identificado por `riid`. Si el objeto no admite esta interfaz, `ppvObj` está establecido en **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Requiere que se autoriza el uso de completamente el equipo. Si no existe una licencia completo de equipo, llame a [CreateInstanceLic](#createinstancelic).  
  
##  <a name="createinstancelic"></a>  CComClassFactory2::CreateInstanceLic  
 Similar a [CreateInstance](#createinstance), salvo que `CreateInstanceLic` requiere una clave de licencia.  
  
```
STDMETHOD(CreateInstanceLic)(
    IUnknown* pUnkOuter,
    IUnknown* /* pUnkReserved
 */,
    REFIID riid,
    BSTR bstrKey,
    void** ppvObject);
```  
  
### <a name="parameters"></a>Parámetros  
 `pUnkOuter`  
 [in] Si el objeto se crea como parte de un agregado, a continuación, `pUnkOuter` debe ser el desconocido externo. En caso contrario, `pUnkOuter` debe ser **NULL**.  
  
 *pUnkReserved*  
 [in] No usado. Debe ser **NULL**.  
  
 `riid`  
 [in] El IID de la interfaz solicitada. Si `pUnkOuter` no es **NULL**, `riid` debe ser **IID_IUnknown**.  
  
 `bstrKey`  
 [in] La clave de licencia de tiempo de ejecución ha obtenido anteriormente de una llamada a `RequestLicKey`. Esta clave es necesaria para crear el objeto.  
  
 `ppvObject`  
 [out] Un puntero al puntero de interfaz especificado por `riid`. Si el objeto no admite esta interfaz, `ppvObject` está establecido en **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Puede obtener una clave licencia con [RequestLicKey](#requestlickey). Para crear un objeto en un equipo sin licencia, se debe llamar a `CreateInstanceLic`.  
  
##  <a name="getlicinfo"></a>  CComClassFactory2::GetLicInfo  
 Rellena un [LICINFO](http://msdn.microsoft.com/library/windows/desktop/ms690590) capacidades de licencia de estructura con información que describe el generador de clases.  
  
```
STDMETHOD(GetLicInfo)(LICINFO* pLicInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 *pLicInfo*  
 [out] Puntero a un **LICINFO** estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 El `fRuntimeKeyAvail` un miembro de esta estructura indica si, dada una clave de licencia, el generador de clases permite que los objetos se creen en un equipo sin licencia. El *fLicVerified* miembro indica si existe una licencia completo de equipo.  
  
##  <a name="lockserver"></a>  CComClassFactory2::LockServer  
 Aumenta y disminuye el módulo recuento de bloqueos mediante una llamada a **_Module::Lock** y **_Module::Unlock**, respectivamente.  
  
```
STDMETHOD(LockServer)(BOOL fLock);
```  
  
### <a name="parameters"></a>Parámetros  
 `fLock`  
 [in] Si **TRUE**, el recuento de bloqueos se incrementó; en caso contrario, disminuye el recuento de bloqueos.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 **_Module** hace referencia a la instancia global de [CComModule](../../atl/reference/ccommodule-class.md) o una clase derivada de ella.  
  
 Al llamar a `LockServer` permite a un cliente almacenar en un generador de clases para que se pueden crear rápidamente varios objetos.  
  
##  <a name="requestlickey"></a>  CComClassFactory2::RequestLicKey  
 Crea y devuelve una clave de licencia, siempre que el `fRuntimeKeyAvail` miembro de la [LICINFO](http://msdn.microsoft.com/library/windows/desktop/ms690590) estructura es **TRUE**.  
  
```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwReserved`  
 [in] No usado. Debe ser cero.  
  
 `pbstrKey`  
 [out] Puntero a la clave de licencia.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Es necesaria para llamar a una clave de licencia [CreateInstanceLic](#createinstancelic) para crear un objeto en un equipo sin licencia. Si `fRuntimeKeyAvail` es **FALSE**, a continuación, solo se pueden crear objetos en un equipo con licencia completa.  
  
 Llame a [GetLicInfo](#getlicinfo) para recuperar el valor de `fRuntimeKeyAvail`.  
  
## <a name="see-also"></a>Vea también  
 [Clase CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)   
 [Clase CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)   
 [CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [Información general de clases](../../atl/atl-class-overview.md)
