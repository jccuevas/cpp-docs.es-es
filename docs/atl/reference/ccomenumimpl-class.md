---
title: Clase CComEnumImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComEnumImpl
- ATLCOM/ATL::CComEnumImpl
- ATLCOM/ATL::CComEnumImpl::CComEnumImpl
- ATLCOM/ATL::CComEnumImpl::Clone
- ATLCOM/ATL::CComEnumImpl::Init
- ATLCOM/ATL::CComEnumImpl::Next
- ATLCOM/ATL::CComEnumImpl::Reset
- ATLCOM/ATL::CComEnumImpl::Skip
- ATLCOM/ATL::CComEnumImpl::m_begin
- ATLCOM/ATL::CComEnumImpl::m_dwFlags
- ATLCOM/ATL::CComEnumImpl::m_end
- ATLCOM/ATL::CComEnumImpl::m_iter
- ATLCOM/ATL::CComEnumImpl::m_spUnk
dev_langs:
- C++
helpviewer_keywords:
- CComEnumImpl class
ms.assetid: cc0d8e76-e608-46db-87cd-4c7161fe32d2
caps.latest.revision: 19
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 6dc6a8ed6a318642efe58dfb94835d45b2163b54
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="ccomenumimpl-class"></a>Clase CComEnumImpl
Esta clase proporciona la implementación de una interfaz de enumerador COM donde se almacenan los elementos que se va a enumerar en una matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Base,
    const IID* piid, class T, class Copy>  
class ATL_NO_VTABLE CComEnumImpl : public Base
```  
  
#### <a name="parameters"></a>Parámetros  
 `Base`  
 Un enumerador COM ( [interfaz IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx)) interfaz.  
  
 `piid`  
 Un puntero al identificador de interfaz de la interfaz de enumerador.  
  
 `T`  
 El tipo de elemento que expone la interfaz de enumerador.  
  
 `Copy`  
 Un homogéneos [copiar la clase de directiva](../../atl/atl-copy-policy-classes.md).  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComEnumImpl::CComEnumImpl](#ccomenumimpl)|El constructor.|  
|[CComEnumImpl:: ~ CComEnumImpl](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComEnumImpl::Clone](#clone)|La implementación de [IEnumXXXX::Clone](https://msdn.microsoft.com/library/ms690336.aspx).|  
|[CComEnumImpl::Init](#init)|Inicializa el enumerador.|  
|[CComEnumImpl::Next](#next)|La implementación de [IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx).|  
|[CComEnumImpl::Reset](#reset)|La implementación de [IEnumXXXX::Reset](https://msdn.microsoft.com/library/ms693414.aspx).|  
|[CComEnumImpl:: Skip](#skip)|La implementación de [IEnumXXXX::Skip](https://msdn.microsoft.com/library/ms690392.aspx).|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComEnumImpl::m_begin](#m_begin)|Un puntero al primer elemento de la matriz.|  
|[CComEnumImpl::m_dwFlags](#m_dwflags)|Copie los indicadores que pasan a través de `Init`.|  
|[CComEnumImpl::m_end](#m_end)|Puntero a la ubicación situada más allá del último elemento de la matriz.|  
|[CComEnumImpl::m_iter](#m_iter)|Un puntero al elemento actual de la matriz.|  
|[CComEnumImpl::m_spUnk](#m_spunk)|El **IUnknown** puntero del objeto proporciona la colección que se va a enumerar.|  
  
## <a name="remarks"></a>Comentarios  
 `CComEnumImpl`proporciona la implementación de una interfaz de enumerador COM donde se almacenan los elementos que se va a enumerar en una matriz. Esta clase es análoga a la `IEnumOnSTLImpl` clase, que proporciona una implementación de una interfaz de enumerador se basa en un contenedor de la biblioteca estándar de C++.  
  
> [!NOTE]
>  Para obtener más información sobre aún más diferencias entre `CComEnumImpl` y `IEnumOnSTLImpl`, consulte [CComEnumImpl::Init](#init).  
  
 Normalmente, será *no* que necesite crear su propia clase de enumerador derivando de esta implementación de la interfaz. Si desea utilizar un enumerador ATL proporcionado basado en una matriz, es más común para crear una instancia de [CComEnum](../../atl/reference/ccomenum-class.md).  
  
 Sin embargo, si necesita proporcionar un enumerador personalizado (por ejemplo, uno que expone interfaces además de la interfaz de enumerador), puede derivar de esta clase. En esta situación, es probable que deba reemplazar el [CComEnumImpl::Clone](#clone) método para proporcionar su propia implementación.  
  
 Para obtener más información, consulte [colecciones y enumeradores ATL](../../atl/atl-collections-and-enumerators.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `Base`  
  
 `CComEnumImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="ccomenumimpl"></a>CComEnumImpl::CComEnumImpl  
 El constructor.  
  
```
CComEnumImpl();
```  
  
##  <a name="dtor"></a>CComEnumImpl:: ~ CComEnumImpl  
 Destructor.  
  
```
~CComEnumImpl();
```  
  
##  <a name="init"></a>CComEnumImpl::Init  
 Debe llamar a este método antes de pasar un puntero a la interfaz de enumerador a los clientes.  
  
```
HRESULT Init(
    T* begin,
    T* end,
    IUnknown* pUnk,
    CComEnumFlags flags = AtlFlagNoCopy);
```  
  
### <a name="parameters"></a>Parámetros  
 *begin*  
 Un puntero al primer elemento de la matriz que contiene los elementos que se van a enumerar.  
  
 `end`  
 Puntero a la ubicación situada más allá del último elemento de la matriz que contiene los elementos que se van a enumerar.  
  
 *pUnk*  
 [in] El **IUnknown** puntero de un objeto que debe mantenerse activo durante la vigencia del enumerador. Pasar **NULL** si no existe el objeto existe.  
  
 `flags`  
 Marcadores que especifican si debe tomar posesión de la matriz o realizar una copia de él el enumerador. Los valores posibles se describen a continuación.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Solo llame a este método una vez, inicializar el enumerador, usar y, a continuación, deshacerse de él.  
  
 Si pasar punteros a elementos de una matriz que se mantienen en otro objeto (y no preguntar el enumerador para copiar los datos), puede utilizar el *pUnk* parámetro para garantizar que están disponibles para el objeto y la matriz contiene siempre y cuando las necesita el enumerador. El enumerador simplemente mantiene una referencia COM en el objeto para mantener activa. La referencia COM se libera automáticamente cuando se destruye el enumerador.  
  
 El `flags` parámetro le permite especificar cómo el enumerador debe tratar los elementos de matriz que se pasa a él. `flags`puede realizar uno de los valores de la **CComEnumFlags** (enumeración) se muestra a continuación:  
  
```  
enum CComEnumFlags  
   {  
   AtlFlagNoCopy = 0,  
   AtlFlagTakeOwnership = 2, // BitOwn  
   AtlFlagCopy = 3           // BitOwn | BitCopy  
   };  
```  
  
 **AtlFlagNoCopy** significa que la duración de la matriz no está controlado por el enumerador. En este caso, estará bien la matriz estática o el objeto identificado por *pUnk* será responsable de liberar la matriz cuando ya no es necesario.  
  
 **AtlFlagTakeOwnership** significa que la destrucción de la matriz está controlado por el enumerador. En este caso, la matriz debe haber sido dinámicamente asignada mediante **nueva**. El enumerador eliminará de la matriz en su destructor. Normalmente, deberá pasar **NULL** de *pUnk*, aunque todavía puede pasar un puntero válido si necesita recibir una notificación de la destrucción del enumerador por algún motivo.  
  
 **AtlFlagCopy** significa que se crea copiando la matriz pasada a una nueva matriz `Init`. Duración de la nueva matriz es controlado por el enumerador. El enumerador eliminará de la matriz en su destructor. Normalmente, deberá pasar **NULL** de *pUnk*, aunque todavía puede pasar un puntero válido si necesita recibir una notificación de la destrucción del enumerador por algún motivo.  
  
> [!NOTE]
>  El prototipo de este método especifica los elementos de la matriz como de tipo **T**, donde **T** se define como un parámetro de plantilla a la clase. Esto es del mismo tipo que se expone mediante el método de interfaz COM [CComEnumImpl::Next](#next). La implicación de esto es que, a diferencia de [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md), esta clase no admite el almacenamiento diferentes y expone los tipos de datos. El tipo de datos de elementos de la matriz debe ser el mismo que el tipo de datos expuesto por medio de la interfaz COM.  
  
##  <a name="clone"></a>CComEnumImpl::Clone  
 Este método proporciona la implementación de la [IEnumXXXX::Clone](https://msdn.microsoft.com/library/ms690336.aspx) método mediante la creación de un objeto de tipo `CComEnum`, inicializar con la misma matriz e iterador utilizado por el objeto actual y devuelve la interfaz en el objeto recién creado.  
  
```
STDMETHOD(Clone)(Base** ppEnum);
```  
  
### <a name="parameters"></a>Parámetros  
 `ppEnum`  
 [out] La interfaz de enumerador en un objeto recién creado se clona desde el enumerador actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que los enumeradores clonados nunca realizan sus propia copia o tomar posesión de los datos utilizados por el enumerador original. Si es necesario, los enumeradores clonados mantendrá el enumerador original activo (mediante una referencia COM) para asegurarse de que los datos están disponibles para siempre y cuando lo necesiten.  
  
##  <a name="m_spunk"></a>CComEnumImpl::m_spUnk  
 Este puntero inteligente mantiene una referencia en el objeto pasado a [CComEnumImpl::Init](#init), asegurándose de que permanece activo durante la vigencia del enumerador.  
  
```
CComPtr<IUnknown> m_spUnk;
```  
  
##  <a name="m_begin"></a>CComEnumImpl::m_begin  
 Puntero a la ubicación situada más allá del último elemento de la matriz que contiene los elementos que se van a enumerar.  
  
```
T* m_begin;
```  
  
##  <a name="m_end"></a>CComEnumImpl::m_end  
 Un puntero al primer elemento de la matriz que contiene los elementos que se van a enumerar.  
  
```
T* m_end;
```  
  
##  <a name="m_iter"></a>CComEnumImpl::m_iter  
 Un puntero al elemento actual de la matriz que contiene los elementos que se van a enumerar.  
  
```
T* m_iter;
```  
  
##  <a name="m_dwflags"></a>CComEnumImpl::m_dwFlags  
 Los indicadores que se pasan a [CComEnumImpl::Init](#init).  
  
```
DWORD m_dwFlags;
```  
  
##  <a name="next"></a>CComEnumImpl::Next  
 Este método proporciona la implementación de la [IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx) método.  
  
```
STDMETHOD(Next)(ULONG celt, T* rgelt, ULONG* pceltFetched);
```  
  
### <a name="parameters"></a>Parámetros  
 `celt`  
 [in] El número de elementos solicitados.  
  
 `rgelt`  
 [out] La matriz que se debe rellenar con los elementos.  
  
 `pceltFetched`  
 [out] El número de elementos realmente devueltos en `rgelt`. Esto puede ser menor que `celt` si hay menos de `celt` elementos permanecen en la lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
##  <a name="reset"></a>CComEnumImpl::Reset  
 Este método proporciona la implementación de la [IEnumXXXX::Reset](https://msdn.microsoft.com/library/ms693414.aspx) método.  
  
```
STDMETHOD(Reset)(void);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
##  <a name="skip"></a>CComEnumImpl:: Skip  
 Este método proporciona la implementación de la [IEnumXXXX::Skip](https://msdn.microsoft.com/library/ms690392.aspx) método.  
  
```
STDMETHOD(Skip)(ULONG celt);
```  
  
### <a name="parameters"></a>Parámetros  
 `celt`  
 [in] El número de elementos que se van a omitir.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Devuelve E_INVALIDARG si `celt` es cero, se devuelve S_FALSE si es menor que `celt` se devuelven los elementos, lo contrario, devuelve S_OK.  
  
## <a name="see-also"></a>Vea también  
 [Clase IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)   
 [Clase CComEnum](../../atl/reference/ccomenum-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

