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
- CComClassFactory
- ATLCOM/ATL::CComClassFactory
- ATLCOM/ATL::CComClassFactory::CreateInstance
- ATLCOM/ATL::CComClassFactory::LockServer
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
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: a0c1c115bfffa1de9a2a8c91c5268de66c68e7cd
ms.lasthandoff: 03/31/2017

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
 `CComClassFactory`implementa el [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) interfaz, que contiene métodos para crear un objeto de CLSID determinado, así como el generador de clases en la memoria para permitir que los nuevos objetos que se crean más rápidamente el bloqueo. **IClassFactory** debe implementarse para todas las clases que se registran en el registro del sistema y a la que se asigna un CLSID.  
  
 Objetos ATL normalmente adquieren un generador de clases derivando de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), que declara `CComClassFactory` como el generador de clases de forma predeterminada. Para invalidar este comportamiento predeterminado, especifique uno de los `DECLARE_CLASSFACTORY` *XXX* macros en la definición de clase. Por ejemplo, el [DECLARE_CLASSFACTORY_EX](aggregation-and-class-factory-macros.md#declare_classfactory_ex) macro utiliza la clase especificada para el generador de clases:  
  
 [!code-cpp[NVC_ATL_COM #8](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]  
  
 La definición de clase anterior especifica que **CMyClassFactory** se usará como generador de clases predeterminado del objeto. **CMyClassFactory** debe derivarse de `CComClassFactory` e invalidar `CreateInstance`.  
  
 ATL proporciona tres otras macros que declaran un generador de clases:  
  
- [Macro DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) utiliza [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), que controla la creación a través de una licencia.  
  
- [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) utiliza [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), que crea objetos en varios contenedores.  
  
- [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) utiliza [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), que construye una sola [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="createinstance"></a>CComClassFactory::CreateInstance  
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
  
##  <a name="lockserver"></a>CComClassFactory::LockServer  
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
  
 Al llamar a `LockServer` permite a un cliente almacenar en un generador de clases para que se pueden crear varios objetos rápidamente.  
  
## <a name="see-also"></a>Vea también  
 [CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [Información general de clases](../../atl/atl-class-overview.md)

