---
title: Clase CComTearOffObject | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComTearOffObject
- ATLCOM/ATL::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::AddRef
- ATLCOM/ATL::CComTearOffObject::QueryInterface
- ATLCOM/ATL::CComTearOffObject::Release
- ATLCOM/ATL::CComTearOffObjectBase
- ATLCOM/ATL::m_pOwner
dev_langs:
- C++
helpviewer_keywords:
- tear-off interfaces, ATL
- tear-off interfaces
- CComTearOffObject class
ms.assetid: d974b598-c6b2-42b1-8360-9190d9d0fbf3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be47c9525098cb3bd444cefff39dbbf25b88d396
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364994"
---
# <a name="ccomtearoffobject-class"></a>Clase CComTearOffObject
Esta clase implementa una interfaz desplazable.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class Base>
class CComTearOffObject : public Base
```  
  
#### <a name="parameters"></a>Parámetros  
 `Base`  
 Deriva de la clase desplazable, `CComTearOffObjectBase` y las interfaces desea que su objeto desplazable para admitir.  
  
 ATL implementa sus interfaces divisibles en dos fases: el `CComTearOffObjectBase` métodos controlan el recuento de referencias y `QueryInterface`, mientras que `CComTearOffObject` implementa [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509).  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComTearOffObject::CComTearOffObject](#ccomtearoffobject)|El constructor.|  
|[CComTearOffObject:: ~ CComTearOffObject](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComTearOffObject::AddRef](#addref)|Incrementa el recuento de referencias para un `CComTearOffObject` objeto.|  
|[CComTearOffObject::QueryInterface](#queryinterface)|Devuelve un puntero a la interfaz solicitada en la clase desplazable o la clase propietaria.|  
|[CComTearOffObject::Release](#release)|Disminuye el recuento de referencias para un `CComTearOffObject` de objeto y se destruye.|  
  
### <a name="ccomtearoffobjectbase-methods"></a>Métodos de CComTearOffObjectBase  
  
|||  
|-|-|  
|[CComTearOffObjectBase](#ccomtearoffobjectbase)|Constructor.|  
  
### <a name="ccomtearoffobjectbase-data-members"></a>Miembros de datos de CComTearOffObjectBase  
  
|||  
|-|-|  
|[m_pOwner](#m_powner)|Un puntero a un `CComObject` deriva de la clase propietaria.|  
  
## <a name="remarks"></a>Comentarios  
 `CComTearOffObject` implementa una interfaz desplazable como un objeto independiente que se crea una instancia solo cuando se consulta esa interfaz. El desplazable se elimina cuando su recuento de referencias se convierte en cero. Por lo general, compilar una interfaz desplazable para una interfaz que se usa con poca frecuencia, puesto que utilizando un desplazable guarda un puntero vtable en todas las instancias del objeto principal.  
  
 Debe derivar la clase que implementa el desplazable de `CComTearOffObjectBase` y de cualquier interfaces que desea que su objeto desplazable a admitir. `CComTearOffObjectBase` se hace plantilla en la clase de propietario y el modelo de subprocesos. La clase de propietario es la clase del objeto para el que se implementa un desplazable. Si no especifica un modelo de subprocesos, se utiliza el modelo de subprocesos de manera predeterminada.  
  
 Debe crear un mapa de COM para la clase desplazable. Cuando se crea una instancia de ATL el desplazable, creará **CComTearOffObject\<CYourTearOffClass >** o **CComCachedTearOffObject\<CYourTearOffClass >**.  
  
 Por ejemplo, en el ejemplo de BUSCAPERSONAS, el `CBeeper2` es la clase desplazable y `CBeeper` es la clase de propietario:  
  
 [!code-cpp[NVC_ATL_COM#43](../../atl/codesnippet/cpp/ccomtearoffobject-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `Base`  
  
 `CComTearOffObject`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="addref"></a>  CComTearOffObject::AddRef  
 Incrementa el recuento de referencias de la `CComTearOffObject` objeto en uno.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que puede ser útil para el diagnóstico y prueba.  
  
##  <a name="ccomtearoffobject"></a>  CComTearOffObject::CComTearOffObject  
 El constructor.  
  
```
CComTearOffObject(void* pv);
```  
  
### <a name="parameters"></a>Parámetros  
 `pv`  
 [in] Puntero que se convertirá en un puntero a un **CComObject\<propietario >** objeto.  
  
### <a name="remarks"></a>Comentarios  
 Recuento de referencias del propietario se incrementa en uno.  
  
##  <a name="dtor"></a>  CComTearOffObject:: ~ CComTearOffObject  
 Destructor.  
  
```
~CComTearOffObject();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados, las llamadas FinalRelease y reduce el módulo de recuento de bloqueo.  
  
##  <a name="ccomtearoffobjectbase"></a>  CComTearOffObject::CComTearOffObjectBase  
 El constructor.  
  
```
CComTearOffObjectBase();
```  
  
### <a name="remarks"></a>Comentarios  
 Inicializa el [m_pOwner](#m_powner) miembro **NULL**.  
  
##  <a name="m_powner"></a>  CComTearOffObject::m_pOwner  
 Un puntero a un [CComObject](../../atl/reference/ccomobject-class.md) objeto derivado de *propietario*.  
  
```
CComObject<Owner>* m_pOwner;
```  
  
### <a name="parameters"></a>Parámetros  
 *Propietario*  
 [in] La clase para el que se implementa un desplazable.  
  
### <a name="remarks"></a>Comentarios  
 El puntero se inicializa en **NULL** durante la construcción.  
  
##  <a name="queryinterface"></a>  CComTearOffObject::QueryInterface  
 Recupera un puntero a la interfaz solicitada.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 [in] El IID de la interfaz que se solicita.  
  
 `ppvObject`  
 [out] Un puntero al puntero de interfaz identificado por `iid`, o **NULL** si no se encuentra la interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Consultas en primer lugar para las interfaces de la clase desplazable. Si la interfaz no está allí, busca la interfaz en el objeto de propietario. Si la interfaz solicitada es **IUnknown**, devuelve el **IUnknown** del propietario.  
  
##  <a name="release"></a>  CComTearOffObject::Release  
 Disminuye el recuento de referencias en uno y, si el recuento de referencias es cero, elimina el `CComTearOffObject`.  
  
```
STDMETHOD_ULONG Release();
```  
  
### <a name="return-value"></a>Valor devuelto  
 En las compilaciones de depuración no, siempre devuelve cero. En las compilaciones de depuración, devuelve un valor que puede ser útil para el diagnóstico o pruebas.  
  
## <a name="see-also"></a>Vea también  
 [Clase CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
