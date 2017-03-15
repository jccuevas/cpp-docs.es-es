---
title: Clase CAutoVectorPtr | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CAutoVectorPtr
- ATL.CAutoVectorPtr
- ATL.CAutoVectorPtr<T>
- CAutoVectorPtr
- ATL::CAutoVectorPtr<T>
dev_langs:
- C++
helpviewer_keywords:
- CAutoVectorPtr class
ms.assetid: 0030362b-6bc4-4a47-9b5b-3c3899dceab4
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: bb4bbd110552d1e3cf604add44de7e428d2703ee
ms.lasthandoff: 02/24/2017

---
# <a name="cautovectorptr-class"></a>Clase CAutoVectorPtr
Esta clase representa un objeto de puntero inteligente con nuevo vector y elimina operadores.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<typename T>  
class CAutoVectorPtr
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de puntero.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAutoVectorPtr::CAutoVectorPtr](#cautovectorptr)|El constructor.|  
|[CAutoVectorPtr:: ~ CAutoVectorPtr](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAutoVectorPtr::Allocate](#allocate)|Llamar a este método para asignar la memoria necesaria por la matriz de objetos que apunta `CAutoVectorPtr`.|  
|[CAutoVectorPtr::Attach](#attach)|Llamar a este método para tomar posesión de un puntero existente.|  
|[CAutoVectorPtr::Detach](#detach)|Llamar a este método para liberar la propiedad de un puntero.|  
|[CAutoVectorPtr::Free](#free)|Llamar a este método para eliminar un objeto al que señala un `CAutoVectorPtr`.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAutoVectorPtr::operator T *](#operator_t__star)|El operador de conversión.|  
|[CAutoVectorPtr::operator =](#operator_eq)|El operador de asignación.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAutoVectorPtr::m_p](#m_p)|La variable de miembro de datos de puntero.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona métodos para crear y administrar un puntero inteligente, que le ayudará a proteger frente a pérdidas de memoria al liberar automáticamente los recursos cuando se encuentra fuera del ámbito. `CAutoVectorPtr`es similar a `CAutoPtr`, la única diferencia es que `CAutoVectorPtr` utiliza [vector new []](../../standard-library/new-operators.md#operator_new_arr) y [vector delete []](../../standard-library/new-operators.md#operator_delete_arr) para asignar y liberar memoria en lugar de C++ **nueva** y **eliminar** operadores. Consulte [CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md) si las clases de colección de `CAutoVectorPtr` son necesarios.  

  
 Consulte [CAutoPtr](../../atl/reference/cautoptr-class.md) para obtener un ejemplo del uso de una clase de puntero inteligente.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="a-nameallocatea--cautovectorptrallocate"></a><a name="allocate"></a>CAutoVectorPtr::Allocate  
 Llamar a este método para asignar la memoria necesaria por la matriz de objetos que apunta `CAutoVectorPtr`.  
  
```
bool Allocate(size_t nElements) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nElements`  
 Número de elementos de la matriz.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la memoria está correctamente asignada, false en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 En compilaciones de depuración, se producirá un error de aserción si el [CAutoVectorPtr::m_p](#m_p) variable miembro actualmente apunta a un valor existente; es decir, no es igual a NULL.  
  
##  <a name="a-nameattacha--cautovectorptrattach"></a><a name="attach"></a>CAutoVectorPtr::Attach  
 Llamar a este método para tomar posesión de un puntero existente.  
  
```
void Attach(T* p) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 La `CAutoVectorPtr` objeto tomará posesión de este puntero.  
  
### <a name="remarks"></a>Comentarios  
 Cuando un `CAutoVectorPtr` objeto toma posesión de un puntero, eliminará automáticamente el puntero y los datos asignados cuando sale del ámbito. Si [CAutoVectorPtr::Detach](#detach) es llama, el programador es nuevo dada la responsabilidad para liberar cualquier recursos asignado.  
  
 En compilaciones de depuración, se producirá un error de aserción si el [CAutoVectorPtr::m_p](#m_p) variable miembro actualmente apunta a un valor existente; es decir, no es igual a NULL.  
  
##  <a name="a-namecautovectorptra--cautovectorptrcautovectorptr"></a><a name="cautovectorptr"></a>CAutoVectorPtr::CAutoVectorPtr  
 El constructor.  
  
```
CAutoVectorPtr() throw();
explicit CAutoVectorPtr(T* p) throw();
CAutoVectorPtr(CAutoVectorPtr<T>& p) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 Un puntero existente.  
  
### <a name="remarks"></a>Comentarios  
 El `CAutoVectorPtr` se puede crear el objeto mediante un puntero existente, en cuyo caso transfiere la propiedad del puntero.  
  
##  <a name="a-namedtora--cautovectorptrcautovectorptr"></a><a name="dtor"></a>CAutoVectorPtr:: ~ CAutoVectorPtr  
 Destructor.  
  
```
~CAutoVectorPtr() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera los recursos asignados. Llamadas [CAutoVectorPtr::Free](#free).  
  
##  <a name="a-namedetacha--cautovectorptrdetach"></a><a name="detach"></a>CAutoVectorPtr::Detach  
 Llamar a este método para liberar la propiedad de un puntero.  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una copia del puntero.  
  
### <a name="remarks"></a>Comentarios  
 Libera la posesión de un puntero, se establece la [CAutoVectorPtr::m_p](#m_p) variable miembro en NULL y devuelve una copia del puntero. Después de llamar a **separar**, es hasta el programador para liberarlos recursos asignado que la `CAutoVectorPtr` objeto puede haber supuesto previamente responsabilidad.  
  
##  <a name="a-namefreea--cautovectorptrfree"></a><a name="free"></a>CAutoVectorPtr::Free  
 Llamar a este método para eliminar un objeto al que señala un `CAutoVectorPtr`.  
  
```
void Free() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 El objeto al que apunta el `CAutoVectorPtr` se liberan y el [CAutoVectorPtr::m_p](#m_p) variable miembro se establece en NULL.  
  
##  <a name="a-namempa--cautovectorptrmp"></a><a name="m_p"></a>CAutoVectorPtr::m_p  
 La variable de miembro de datos de puntero.  
  
```
T* m_p;
```  
  
### <a name="remarks"></a>Comentarios  
 Esta variable miembro contiene la información de puntero.  
  
##  <a name="a-nameoperatoreqa--cautovectorptroperator-"></a><a name="operator_eq"></a>CAutoVectorPtr::operator =  
 El operador de asignación.  
  
```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 Un puntero.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia a un **CAutoVectorPtr\< T >**.  
  
### <a name="remarks"></a>Comentarios  
 El operador de asignación se separa la `CAutoVectorPtr` objeto desde el puntero actual y se asocia el nuevo puntero, `p`, en su lugar.  
  
##  <a name="a-nameoperatortstara--cautovectorptroperator-t-"></a><a name="operator_t__star"></a>CAutoVectorPtr::operator T *  
 El operador de conversión.  
  
```  
operator T*() const throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Devuelve un puntero al tipo de datos de objeto definido en la plantilla de clase.  
  
## <a name="see-also"></a>Vea también  
 [Clase CAutoPtr](../../atl/reference/cautoptr-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

