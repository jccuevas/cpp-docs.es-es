---
title: Clase de CComClassFactory | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CComClassFactory
- CComClassFactory
- ATL::CComClassFactory
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactory class
ms.assetid: e56dacf7-d5c4-4c42-aef4-a86d91981a1b
caps.latest.revision: 20
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
ms.openlocfilehash: c7c488732d7b32248acaaa5c5c9c6a29404c3872
ms.lasthandoff: 02/24/2017

---
# <a name="ccomclassfactory-class"></a>CComClassFactory (clase)
Esta clase implementa la [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) interfaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CComClassFactory 
   : public IClassFactory,  
     public CComObjectRootEx<CComGlobalsThreadModel>
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComClassFactory::CreateInstance](#createinstance)|Crea un objeto del CLSID especificado.|  
|[CComClassFactory::LockServer](#lockserver)|Bloquea el generador de clases en la memoria.|  
  
## <a name="remarks"></a>Comentarios  
 `CComClassFactory`implementa el [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) interfaz, que contiene métodos para crear un objeto de CLSID determinado, así como el generador de clases en la memoria para permitir que los nuevos objetos que se crean más rápidamente el bloqueo. **IClassFactory** deben implementarse para cada clase que se registra en el registro del sistema y de que asigna un CLSID.  
  
 Objetos ATL normalmente adquieren un generador de clases derivando de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](http://msdn.microsoft.com/library/51a6b925-07c0-4d3a-9174-0b8c808975e4), que declara `CComClassFactory` como el generador de clases de forma predeterminada. Para reemplazar este valor predeterminado, especifique uno de los `DECLARE_CLASSFACTORY` *XXX* macros en la definición de clase. Por ejemplo, el [DECLARE_CLASSFACTORY_EX](http://msdn.microsoft.com/library/4181ef00-0f30-4e19-b0ee-e7648062e926) macro utiliza la clase especificada para el generador de clases:  
  
 [!code-cpp[NVC_ATL_COM Nº&8;](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]  
  
 La definición de clase anterior especifica que **CMyClassFactory** se utiliza como generador de clases predeterminado del objeto. **CMyClassFactory** debe derivar de `CComClassFactory` e invalidar `CreateInstance`.  
  
 ATL proporciona tres otras macros que declaran un generador de clases:  
  
- [Macro DECLARE_CLASSFACTORY2](http://msdn.microsoft.com/library/38a6c969-7297-4bb1-9ba6-1fe2d355b285) utiliza [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), que controla la creación de una licencia.  
  
- [DECLARE_CLASSFACTORY_AUTO_THREAD](http://msdn.microsoft.com/library/19d7105e-03e8-4412-9f5e-5384c8a5e18f) utiliza [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), que crea objetos en varios contenedores.  
  
- [DECLARE_CLASSFACTORY_SINGLETON](http://msdn.microsoft.com/library/0e4a3964-c03d-463e-884c-fe3b416db478) utiliza [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), que construye una sola [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="a-namecreateinstancea--ccomclassfactorycreateinstance"></a><a name="createinstance"></a>CComClassFactory::CreateInstance  
 Crea un objeto del CLSID especificado y recupera un puntero de interfaz a este objeto.  
  
```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```  
  
### <a name="parameters"></a>Parámetros  
 `pUnkOuter`  
 [in] Si el objeto se crea como parte de un agregado, a continuación, `pUnkOuter` debe ser el desconocido externo. De lo contrario, `pUnkOuter` debe ser **NULL**.  
  
 `riid`  
 [in] El IID de la interfaz solicitada. Si `pUnkOuter` no es **NULL**, `riid` debe ser **IID_IUnknown**.  
  
 `ppvObj`  
 [out] Un puntero al puntero de interfaz identificado por `riid`. Si el objeto no admite esta interfaz, `ppvObj` está establecido en **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
##  <a name="a-namelockservera--ccomclassfactorylockserver"></a><a name="lockserver"></a>CComClassFactory::LockServer  
 Aumenta y disminuye el módulo recuento de bloqueos mediante una llamada a **_Module::Lock** y **_Module::Unlock**, respectivamente.  
  
```
STDMETHOD(LockServer)(BOOL fLock);
```  
  
### <a name="parameters"></a>Parámetros  
 `fLock`  
 [in] Si **TRUE**, el recuento de bloqueos se incrementa; en caso contrario, disminuye el recuento de bloqueos.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 **_Module** hace referencia a la instancia global de [CComModule](../../atl/reference/ccommodule-class.md) o una clase derivada de ella.  
  
 Llamar a `LockServer` permite a un cliente retener un generador de clases para que se pueden crear rápidamente varios objetos.  
  
## <a name="see-also"></a>Vea también  
 [CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [Información general de la clase](../../atl/atl-class-overview.md)

