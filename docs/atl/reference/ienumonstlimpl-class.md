---
title: Clase IEnumOnSTLImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl::Clone
- ATLCOM/ATL::IEnumOnSTLImpl::Init
- ATLCOM/ATL::IEnumOnSTLImpl::Next
- ATLCOM/ATL::IEnumOnSTLImpl::Reset
- ATLCOM/ATL::IEnumOnSTLImpl::Skip
- ATLCOM/ATL::IEnumOnSTLImpl::m_iter
- ATLCOM/ATL::IEnumOnSTLImpl::m_pcollection
- ATLCOM/ATL::IEnumOnSTLImpl::m_spUnk
dev_langs: C++
helpviewer_keywords: IEnumOnSTLImpl class
ms.assetid: 1789e77b-88b8-447d-a490-806b918912ce
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 38d645f7841cb71af9812bd1d62a979752a0343d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ienumonstlimpl-class"></a>Clase IEnumOnSTLImpl
Esta clase define una interfaz de enumerador basándose en una colección de la biblioteca estándar de C++.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Base,
    const IID* piid, class T, class Copy, class CollType>  
class ATL_NO_VTABLE IEnumOnSTLImpl : public Base
```  
  
#### <a name="parameters"></a>Parámetros  
 `Base`  
 Un enumerador COM ( [interfaz IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx)) interfaz.  
  
 `piid`  
 Un puntero al identificador de interfaz de la interfaz de enumerador.  
  
 `T`  
 El tipo de elemento expuesto por la interfaz de enumerador.  
  
 `Copy`  
 A [copiar clase directiva](../../atl/atl-copy-policy-classes.md).  
  
 `CollType`  
 Una clase de contenedor de la biblioteca estándar de C++.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IEnumOnSTLImpl::Clone](#clone)|La implementación de [IEnumXXXX::Clone](https://msdn.microsoft.com/library/ms690336.aspx).|  
|[IEnumOnSTLImpl::Init](#init)|Inicializa el enumerador.|  
|[IEnumOnSTLImpl::Next](#next)|La implementación de [IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx).|  
|[IEnumOnSTLImpl::Reset](#reset)|La implementación de [IEnumXXXX::Reset](https://msdn.microsoft.com/library/ms693414.aspx).|  
|[IEnumOnSTLImpl::Skip](#skip)|La implementación de [IEnumXXXX::Skip](https://msdn.microsoft.com/library/ms690392.aspx).|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IEnumOnSTLImpl::m_iter](#m_iter)|El iterador que representa la posición del enumerador actual dentro de la colección.|  
|[IEnumOnSTLImpl::m_pcollection](#m_pcollection)|Un puntero para el contenedor de la biblioteca estándar de C++ que contiene los elementos que se van a enumerar.|  
|[IEnumOnSTLImpl::m_spUnk](#m_spunk)|El **IUnknown** puntero del objeto que proporciona la colección.|  
  
## <a name="remarks"></a>Comentarios  
 `IEnumOnSTLImpl`proporciona la implementación de una interfaz de enumerador COM donde se almacenan los elementos que se enumeran en un contenedor compatible de biblioteca estándar de C++. Esta clase es análoga a la [CComEnumImpl](../../atl/reference/ccomenumimpl-class.md) (clase), que proporciona una implementación de una interfaz de enumerador basado en una matriz.  
  
> [!NOTE]
>  Vea [CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init) para obtener más información sobre aún más las diferencias entre `CComEnumImpl` y `IEnumOnSTLImpl`.  
  
 Normalmente, tendrá que *no* que necesite crear su propia clase de enumerador derivando de esta implementación de interfaz. Si desea utilizar un enumerador ATL proporcionada en función de un contenedor de la biblioteca estándar de C++, es más habitual para crear una instancia de [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md), o para crear una clase de colección que devuelve un enumerador derivando de [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md).  
  
 Sin embargo, si tiene que proporcionar un enumerador personalizado (por ejemplo, uno que expone interfaces además de la interfaz de enumerador), puede derivar de esta clase. En esta situación es probable que deba reemplazar el [clon](#clone) método para proporcionar su propia implementación.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `Base`  
  
 `IEnumOnSTLImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="init"></a>IEnumOnSTLImpl::Init  
 Inicializa el enumerador.  
  
```
HRESULT Init(
    IUnknown* pUnkForRelease,
    CollType& collection);
```  
  
### <a name="parameters"></a>Parámetros  
 `pUnkForRelease`  
 [in] El **IUnknown** puntero de un objeto que debe mantenerse activo durante la vigencia del enumerador. Pasar **NULL** si no existe el objeto no existe.  
  
 `collection`  
 Una referencia al contenedor de biblioteca estándar de C++ que contiene los elementos que hay que enumerar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Si se pasa `Init` mantiene una referencia a una colección en otro objeto, puede usar el `pUnkForRelease` parámetro para asegurarse de que está disponible para el objeto y la colección contiene, siempre y cuando lo necesite el enumerador.  
  
 Debe llamar a este método antes de pasar un puntero a la interfaz de enumerador a cualquiera de los clientes.  
  
##  <a name="clone"></a>IEnumOnSTLImpl::Clone  
 Este método proporciona la implementación de la [IEnumXXXX::Clone](https://msdn.microsoft.com/library/ms690336.aspx) método mediante la creación de un objeto de tipo `CComEnumOnSTL`, inicializándola con la misma colección e iterador utilizado por el objeto actual y devuelve la interfaz en el objeto recién creado.  
  
```
STDMETHOD(Clone)(Base** ppEnum);
```  
  
### <a name="parameters"></a>Parámetros  
 `ppEnum`  
 [out] La interfaz de enumerador en un objeto recién creado clonados a partir del enumerador actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
##  <a name="m_spunk"></a>IEnumOnSTLImpl::m_spUnk  
 El **IUnknown** puntero del objeto que proporciona la colección.  
  
```
CComPtr<IUnknown> m_spUnk;
```  
  
### <a name="remarks"></a>Comentarios  
 Este puntero inteligente mantiene una referencia en el objeto pasado a [IEnumOnSTLImpl::Init](#init), asegurándose de que permanece activo durante la vigencia del enumerador.  
  
##  <a name="m_pcollection"></a>IEnumOnSTLImpl::m_pcollection  
 Este miembro apunta a la colección que proporciona los datos que se imponen la implementación de la interfaz de enumerador.  
  
```
CollType* m_pcollection;
```  
  
### <a name="remarks"></a>Comentarios  
 Este miembro se inicializa mediante una llamada a [IEnumOnSTLImpl::Init](#init).  
  
##  <a name="m_iter"></a>IEnumOnSTLImpl::m_iter  
 Este miembro contiene el iterador que se usan para marcar la posición actual dentro de la colección y navegar a los elementos siguientes.  
  
```
CollType::iterator m_iter;
```  
  
##  <a name="next"></a>IEnumOnSTLImpl::Next  
 Este método proporciona la implementación de la [IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx) método.  
  
```
STDMETHOD(Next)(
    ULONG celt,
    T* rgelt,
    ULONG* pceltFetched);
```  
  
### <a name="parameters"></a>Parámetros  
 `celt`  
 [in] El número de elementos solicitados.  
  
 `rgelt`  
 [out] La matriz que se rellena con los elementos.  
  
 `pceltFetched`  
 [out] El número de elementos realmente devueltos en `rgelt`. Esto puede ser menor que `celt` si hay menos de `celt` elementos permanecen en la lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
##  <a name="reset"></a>IEnumOnSTLImpl::Reset  
 Este método proporciona la implementación de la [IEnumXXXX::Reset](https://msdn.microsoft.com/library/ms693414.aspx) método.  
  
```
STDMETHOD(Reset)(void);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
##  <a name="skip"></a>IEnumOnSTLImpl::Skip  
 Este método proporciona la implementación de la [IEnumXXXX::Skip](https://msdn.microsoft.com/library/ms690392.aspx) método.  
  
```
STDMETHOD(Skip)(ULONG celt);
```  
  
### <a name="parameters"></a>Parámetros  
 `celt`  
 [in] El número de elementos que se van a omitir.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)
