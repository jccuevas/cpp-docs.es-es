---
title: CComClassFactory2 (clase) | Microsoft Docs
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
ms.openlocfilehash: fe4ddaab8de2369c7cb1b31132f686bc6037676b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205530"
---
# <a name="ccomclassfactory2-class"></a>CComClassFactory2 (clase)
Esta clase implementa la [IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2) interfaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class license>  
class CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```  
  
#### <a name="parameters"></a>Parámetros  
 *licencia*  
 Una clase que implementa las funciones estáticas siguientes:  
  
- `static BOOL VerifyLicenseKey( BSTR bstr );`  
  
- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`  
  
- `static BOOL IsLicenseValid( );`  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComClassFactory2::CreateInstance](#createinstance)|Crea un objeto del CLSID especificado.|  
|[CComClassFactory2::CreateInstanceLic](#createinstancelic)|Dada una clave de licencia, crea un objeto del CLSID especificado.|  
|[CComClassFactory2::GetLicInfo](#getlicinfo)|Recupera la información que describe las capacidades de administración de licencias del generador de clases.|  
|[CComClassFactory2::LockServer](#lockserver)|Bloquea el generador de clases en la memoria.|  
|[CComClassFactory2::RequestLicKey](#requestlickey)|Crea y devuelve una clave de licencia.|  
  
## <a name="remarks"></a>Comentarios  
 `CComClassFactory2` implementa el [IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2) interfaz, que es una extensión de [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory). `IClassFactory2` creación de objetos de los controles a través de una licencia. Una clase factory ejecutada en un equipo con licencia puede proporcionar una clave de licencia de tiempo de ejecución. Esta clave de licencia permite que una aplicación crear instancias de objetos cuando no existe una licencia de toda la máquina.  
  
 Objetos ATL adquieren normalmente un generador de clases mediante la derivación de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), que declara [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases de forma predeterminada. Para usar `CComClassFactory2`, especifique el [macro DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) macro en la definición de clase del objeto. Por ejemplo:  
  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]  
  
 `CMyLicense`, el parámetro de plantilla `CComClassFactory2`, debe implementar las funciones estáticas `VerifyLicenseKey`, `GetLicenseKey`, y `IsLicenseValid`. El siguiente es un ejemplo de una clase simple de licencia:  
  
 [!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]  
  
 `CComClassFactory2` se deriva de ambos `CComClassFactory2Base` y *licencia*. `CComClassFactory2Base`, a su vez, deriva `IClassFactory2` y `CComObjectRootEx< CComGlobalsThreadModel >`.  
  
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
 *pUnkOuter*  
 [in] Si el objeto se crea como parte de un agregado y, a continuación, *pUnkOuter* debe ser el desconocido externo. En caso contrario, *pUnkOuter* debe ser NULL.  
  
 *riid*  
 [in] IID de la interfaz solicitada. Si *pUnkOuter* es distinto de NULL, *riid* debe ser `IID_IUnknown`.  
  
 *ppvObj*  
 [out] Un puntero al puntero de interfaz identificado por *riid*. Si el objeto no admite esta interfaz, *ppvObj* se establece en NULL.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Requiere que el equipo estar totalmente protegidos. Si no existe una licencia de toda la máquina, llame a [CreateInstanceLic](#createinstancelic).  
  
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
 *pUnkOuter*  
 [in] Si el objeto se crea como parte de un agregado y, a continuación, *pUnkOuter* debe ser el desconocido externo. En caso contrario, *pUnkOuter* debe ser NULL.  
  
 *pUnkReserved*  
 [in] No se utiliza. Debe ser NULL.  
  
 *riid*  
 [in] IID de la interfaz solicitada. Si *pUnkOuter* es distinto de NULL, *riid* debe ser `IID_IUnknown`.  
  
 *bstrKey*  
 [in] La clave de licencia de tiempo de ejecución se obtuvo antes en una llamada a `RequestLicKey`. Esta clave es necesaria para crear el objeto.  
  
 *ppvObject*  
 [out] Un puntero al puntero de interfaz especificado por *riid*. Si el objeto no admite esta interfaz, *ppvObject* se establece en NULL.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Puede obtener una clave licencia con [RequestLicKey](#requestlickey). Para poder crear un objeto en un equipo sin licencia, debe llamar a `CreateInstanceLic`.  
  
##  <a name="getlicinfo"></a>  CComClassFactory2::GetLicInfo  
 Rellena un [LICINFO](/windows/desktop/api/ocidl/ns-ocidl-taglicinfo) capacidades de licencia de estructura con información que describe el generador de clases.  
  
```
STDMETHOD(GetLicInfo)(LICINFO* pLicInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 *pLicInfo*  
 [out] Puntero a un `LICINFO` estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 El `fRuntimeKeyAvail` miembro de esta estructura indica si, dada una clave de licencia, el generador de clases permite que los objetos que se crearán en un equipo sin licencia. El *fLicVerified* miembro indica si existe una licencia de toda la máquina.  
  
##  <a name="lockserver"></a>  CComClassFactory2::LockServer  
 Incrementa y disminuye el bloqueo de módulo se cuentan mediante una llamada a `_Module::Lock` y `_Module::Unlock`, respectivamente.  
  
```
STDMETHOD(LockServer)(BOOL fLock);
```  
  
### <a name="parameters"></a>Parámetros  
 *manada*  
 [in] Si es TRUE, se incrementa el recuento de bloqueos; en caso contrario, el recuento de bloqueos es reducido.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 `_Module` hace referencia a la instancia global de [CComModule](../../atl/reference/ccommodule-class.md) o una clase derivada de él.  
  
 Una llamada a `LockServer` permite que un cliente retener un generador de clases para que se pueden crear rápidamente varios objetos.  
  
##  <a name="requestlickey"></a>  CComClassFactory2::RequestLicKey  
 Crea y devuelve una clave de licencia, siempre que el `fRuntimeKeyAvail` miembro de la [LICINFO](/windows/desktop/api/ocidl/ns-ocidl-taglicinfo) estructura es TRUE.  
  
```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwReservado*  
 [in] No se utiliza. Debe ser cero.  
  
 *pbstrKey*  
 [out] Puntero a la clave de licencia.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Es necesaria para llamar a una clave de licencia [CreateInstanceLic](#createinstancelic) para crear un objeto en un equipo sin licencia. Si `fRuntimeKeyAvail` es FALSE, entonces solo se pueden crear objetos en un equipo con licencia completa.  
  
 Llame a [GetLicInfo](#getlicinfo) para recuperar el valor de `fRuntimeKeyAvail`.  
  
## <a name="see-also"></a>Vea también  
 [CComClassFactoryAutoThread (clase)](../../atl/reference/ccomclassfactoryautothread-class.md)   
 [CComClassFactorySingleton (clase)](../../atl/reference/ccomclassfactorysingleton-class.md)   
 [CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [Información general de clases](../../atl/atl-class-overview.md)
