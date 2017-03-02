---
title: Clase CRBTree | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CRBTree
- CRBTree
- ATL::CRBTree
dev_langs:
- C++
helpviewer_keywords:
- CRBTree class
ms.assetid: a1b1cb63-38e4-4fc2-bb28-f774d1721760
caps.latest.revision: 18
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
ms.openlocfilehash: 7dec5cc56d28c4574f923fe2cbb952b628e2689f
ms.lasthandoff: 02/24/2017

---
# <a name="crbtree-class"></a>Clase CRBTree
Esta clase proporciona métodos para crear y utilizar un árbol rojo-negro.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <typename K,
          typename V, 
          class KTraits = CElementTraits<K>, 
          class VTraits = CElementTraits<V>> 
class CRBTree
```  
  
#### <a name="parameters"></a>Parámetros  
 `K`  
 El tipo de elemento de la clave.  
  
 *V*  
 El tipo de elemento de valor.  
  
 `KTraits`  
 El código utilizado para copiar o mover elementos clave. Consulte [CElementTraits clase](../../atl/reference/celementtraits-class.md) para obtener más detalles.  
  
 `VTraits`  
 El código utilizado para copiar o mover elementos de valor.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRBTree::KINARGTYPE](#kinargtype)|Tipo que se utiliza cuando una clave se pasa como un argumento de entrada.|  
|[CRBTree::KOUTARGTYPE](#koutargtype)|Tipo que se utiliza cuando una clave se devuelve como un argumento de salida.|  
|[CRBTree::VINARGTYPE](#vinargtype)|Tipo que se utiliza cuando se pasa un valor como argumento de entrada.|  
|[CRBTree::VOUTARGTYPE](#voutargtype)|Tipo que se utiliza cuando se pasa un valor como un argumento de salida.|  
  
### <a name="public-classes"></a>Clases públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[Clase CRBTree::CPair](#cpair_class)|Una clase que contiene los elementos clave y valor.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRBTree:: ~ CRBTree](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)|Llame a este método para buscar la posición del elemento que se utiliza la siguiente clave disponible.|  
|[CRBTree::GetAt](#getat)|Llame a este método para obtener el elemento en una posición determinada en el árbol.|  
|[CRBTree::GetCount](#getcount)|Llame a este método para obtener el número de elementos en el árbol.|  
|[CRBTree::GetHeadPosition](#getheadposition)|Llamar a este método para obtener el valor de la posición del elemento en el encabezado del árbol.|  
|[CRBTree::GetKeyAt](#getkeyat)|Llame a este método para obtener la clave de una posición especificada en el árbol.|  
|[CRBTree::GetNext](#getnext)|Llamar a este método para obtener un puntero a un elemento almacenado en el `CRBTree` de objetos y avanzar la posición en el siguiente elemento.|  
|[CRBTree::GetNextAssoc](#getnextassoc)|Llamar a este método para obtener la clave y el valor de un elemento almacenado en el mapa y avanzar la posición en el siguiente elemento.|  
|[CRBTree::GetNextKey](#getnextkey)|Llamar a este método para obtener la clave de un elemento almacenado en el árbol y avanzar la posición en el siguiente elemento.|  
|[CRBTree::GetNextValue](#getnextvalue)|Llamar a este método para obtener el valor de un elemento almacenado en el árbol y avanzar la posición en el siguiente elemento.|  
|[CRBTree::GetPrev](#getprev)|Llamar a este método para obtener un puntero a un elemento almacenado en el `CRBTree` de objetos y, a continuación, actualizar la posición al elemento anterior.|  
|[CRBTree::GetTailPosition](#gettailposition)|Llamar a este método para obtener el valor de la posición del elemento en la cola del árbol.|  
|[CRBTree::GetValueAt](#getvalueat)|Llamar a este método para recuperar el valor almacenado en una posición determinada en la `CRBTree` objeto.|  
|[CRBTree::IsEmpty](#isempty)|Llamar a este método para probar si un objeto de árbol vacía.|  
|[CRBTree::RemoveAll](#removeall)|Llamar a este método para quitar todos los elementos de la **CRBTree** objeto.|  
|[CRBTree::RemoveAt](#removeat)|Llamar a este método para quitar el elemento de la posición especificada en el **CRBTree** objeto.|  
|[CRBTree::SetValueAt](#setvalueat)|Llamar a este método para cambiar el valor almacenado en una posición determinada en la `CRBTree` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Un árbol rojo-negro es un árbol de búsqueda binaria que usa un dato adicional algo de información por nodo para asegurarse de que sigue siendo "equilibrado", que es, el alto del árbol no crezca desproporcionadamente grande y afectar al rendimiento.  
  
 Esta clase de plantilla está diseñada para utilizarse en [CRBMap](../../atl/reference/crbmap-class.md) y [CRBMultiMap](../../atl/reference/crbmultimap-class.md). Proporciona la mayor parte de los métodos que componen estas clases derivadas `CRBTree`.  
  
 Para obtener una explicación más completa de las diversas clases de colección y sus funciones y características de rendimiento, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="a-namecpairclassa--crbtreecpair-class"></a><a name="cpair_class"></a>Clase CRBTree::CPair  
 Una clase que contiene los elementos clave y valor.  
  
```
class CPair : public __POSITION
```  
  
### <a name="remarks"></a>Comentarios  
 Esta clase se utiliza con los métodos [CRBTree::GetAt](#getat), [CRBTree::GetNext](#getnext), y [CRBTree::GetPrev](#getprev) para tener acceso a los elementos de clave y valor almacenados en la estructura de árbol.  
  
 Los miembros son los siguientes:  
  
|||  
|-|-|  
|`m_key`|El miembro de datos que se almacena el elemento key.|  
|`m_value`|El miembro de datos almacenar el elemento de valor.|  
  
##  <a name="a-namedtora--crbtreecrbtree"></a><a name="dtor"></a>CRBTree:: ~ CRBTree  
 Destructor.  
  
```
~CRBTree() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera los recursos asignados. Llamadas [CRBTree::RemoveAll](#removeall) eliminar todos los elementos.  
  
##  <a name="a-namefindfirstkeyaftera--crbtreefindfirstkeyafter"></a><a name="findfirstkeyafter"></a>CRBTree::FindFirstKeyAfter  
 Llame a este método para buscar la posición del elemento que se utiliza la siguiente clave disponible.  
  
```
POSITION FindFirstKeyAfter(KINARGTYPE key) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Un valor de clave.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de la posición del elemento que se utiliza la siguiente clave disponible. Si no hay ningún elemento más, se devuelve NULL.  
  
### <a name="remarks"></a>Comentarios  
 Este método facilita la recorrer el árbol sin necesidad de calcular los valores de posición de antemano.  
  
##  <a name="a-namegetata--crbtreegetat"></a><a name="getat"></a>CRBTree::GetAt  
 Llame a este método para obtener el elemento en una posición determinada en el árbol.  
  
```
CPair* GetAt(POSITION pos) throw();
const CPair* GetAt(POSITION pos) const throw();
void GetAt(POSITION pos, KOUTARGTYPE key, VOUTARGTYPE value) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El valor de posición.  
  
 `key`  
 La variable que recibe la clave.  
  
 *value*  
 La variable que recibe el valor.  
  
### <a name="return-value"></a>Valor devuelto  
 Las dos primeras formas devuelven un puntero a un [CPair](#cpair_class). La tercera forma obtiene una clave y un valor para la posición especificada.  
  
### <a name="remarks"></a>Comentarios  
 El valor de posición puede ser previamente determinado con una llamada a un método como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::GetTailPosition](#gettailposition).  
  
 En compilaciones de depuración, se producirá un error de aserción si `pos` es igual a NULL.  
  
##  <a name="a-namegetcounta--crbtreegetcount"></a><a name="getcount"></a>CRBTree::GetCount  
 Llame a este método para obtener el número de elementos en el árbol.  
  
```
size_t GetCount() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de elementos (cada par clave/valor es un elemento) que se almacena en el árbol.  
  
##  <a name="a-namegetheadpositiona--crbtreegetheadposition"></a><a name="getheadposition"></a>CRBTree::GetHeadPosition  
 Llamar a este método para obtener el valor de la posición del elemento en el encabezado del árbol.  
  
```
POSITION GetHeadPosition() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de la posición del elemento en el encabezado del árbol.  
  
### <a name="remarks"></a>Comentarios  
 El valor devuelto por `GetHeadPosition` puede utilizarse con métodos como [CRBTree::GetKeyAt](#getkeyat) o [CRBTree::GetNext](#getnext) para recorrer el árbol y recuperar valores.  
  
##  <a name="a-namegetkeyata--crbtreegetkeyat"></a><a name="getkeyat"></a>CRBTree::GetKeyAt  
 Llame a este método para obtener la clave de una posición especificada en el árbol.  
  
```
const K& GetKeyAt(POSITION pos) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El valor de posición.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la clave almacenada en la posición `pos` en el árbol.  
  
### <a name="remarks"></a>Comentarios  
 Si `pos` no es un valor de posición válida, los resultados son impredecibles. En compilaciones de depuración, se producirá un error de aserción si `pos` es igual a NULL.  
  
##  <a name="a-namegetnexta--crbtreegetnext"></a><a name="getnext"></a>CRBTree::GetNext  
 Llamar a este método para obtener un puntero a un elemento almacenado en el `CRBTree` de objetos y avanzar la posición en el siguiente elemento.  
  
```
const CPair* GetNext(POSITION& pos) const throw();
CPair* GetNext(POSITION& pos) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El contador de posición, devuelto por una llamada anterior a métodos como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a la siguiente [CPair](#cpair_class) valor en el árbol.  
  
### <a name="remarks"></a>Comentarios  
 El `pos` contador de posición se actualiza después de cada llamada. Si el elemento recuperado es el último en el árbol, `pos` se establece en NULL.  
  
##  <a name="a-namegetnextassoca--crbtreegetnextassoc"></a><a name="getnextassoc"></a>CRBTree::GetNextAssoc  
 Llamar a este método para obtener la clave y el valor de un elemento almacenado en el mapa y avanzar la posición en el siguiente elemento.  
  
```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El contador de posición, devuelto por una llamada anterior a métodos como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
 `key`  
 Parámetro de plantilla que especifica el tipo de clave del árbol.  
  
 *value*  
 Parámetro de plantilla que especifica el tipo de valor del árbol.  
  
### <a name="remarks"></a>Comentarios  
 El `pos` contador de posición se actualiza después de cada llamada. Si el elemento recuperado es el último en el árbol, `pos` se establece en NULL.  
  
##  <a name="a-namegetnextkeya--crbtreegetnextkey"></a><a name="getnextkey"></a>CRBTree::GetNextKey  
 Llamar a este método para obtener la clave de un elemento almacenado en el árbol y avanzar la posición en el siguiente elemento.  
  
```
const K& GetNextKey(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El contador de posición, devuelto por una llamada anterior a métodos como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia a la clave siguiente en el árbol.  
  
### <a name="remarks"></a>Comentarios  
 Actualiza el contador de posición actual, `pos`. Si no hay ninguna más entradas en el árbol, el contador de posición se establece en NULL.  
  
##  <a name="a-namegetnextvaluea--crbtreegetnextvalue"></a><a name="getnextvalue"></a>CRBTree::GetNextValue  
 Llamar a este método para obtener el valor de un elemento almacenado en el árbol y avanzar la posición en el siguiente elemento.  
  
```
const V& GetNextValue(POSITION& pos) const throw();
V& GetNextValue(POSITION& pos) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El contador de posición, devuelto por una llamada anterior a métodos como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia al siguiente valor en el árbol.  
  
### <a name="remarks"></a>Comentarios  
 Actualiza el contador de posición actual, `pos`. Si no hay ninguna más entradas en el árbol, el contador de posición se establece en NULL.  
  
##  <a name="a-namegetpreva--crbtreegetprev"></a><a name="getprev"></a>CRBTree::GetPrev  
 Llamar a este método para obtener un puntero a un elemento almacenado en el `CRBTree` de objetos y, a continuación, actualizar la posición al elemento anterior.  
  
```
const CPair* GetPrev(POSITION& pos) const throw();
CPair* GetPrev(POSITION& pos) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El contador de posición, devuelto por una llamada anterior a métodos como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a la anterior [CPair](#cpair_class) valor almacenado en el árbol.  
  
### <a name="remarks"></a>Comentarios  
 Actualiza el contador de posición actual, `pos`. Si no hay ninguna más entradas en el árbol, el contador de posición se establece en NULL.  
  
##  <a name="a-namegettailpositiona--crbtreegettailposition"></a><a name="gettailposition"></a>CRBTree::GetTailPosition  
 Llamar a este método para obtener el valor de la posición del elemento en la cola del árbol.  
  
```
POSITION GetTailPosition() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de la posición del elemento en la cola del árbol.  
  
### <a name="remarks"></a>Comentarios  
 El valor devuelto por `GetTailPosition` puede utilizarse con métodos como [CRBTree::GetKeyAt](#getkeyat) o [CRBTree::GetPrev](#getprev) para recorrer el árbol y recuperar valores.  
  
##  <a name="a-namegetvalueata--crbtreegetvalueat"></a><a name="getvalueat"></a>CRBTree::GetValueAt  
 Llamar a este método para recuperar el valor almacenado en una posición determinada en la `CRBTree` objeto.  
  
```
const V& GetValueAt(POSITION pos) const throw();
V& GetValueAt(POSITION pos) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El contador de posición, devuelto por una llamada anterior a métodos como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia para el valor almacenado en la posición especificada en el `CRBTree` objeto.  
  
##  <a name="a-nameisemptya--crbtreeisempty"></a><a name="isempty"></a>CRBTree::IsEmpty  
 Llamar a este método para probar si un objeto de árbol vacía.  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si está vacío, el árbol **false** en caso contrario.  
  
##  <a name="a-namekinargtypea--crbtreekinargtype"></a><a name="kinargtype"></a>CRBTree::KINARGTYPE  
 Tipo que se utiliza cuando una clave se pasa como un argumento de entrada.  
  
```
typedef KTraits::INARGTYPE KINARGTYPE;
```  
  
##  <a name="a-namekoutargtypea--crbtreekoutargtype"></a><a name="koutargtype"></a>CRBTree::KOUTARGTYPE  
 Tipo que se utiliza cuando una clave se devuelve como un argumento de salida.  
  
```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```  
  
##  <a name="a-nameremovealla--crbtreeremoveall"></a><a name="removeall"></a>CRBTree::RemoveAll  
 Llamar a este método para quitar todos los elementos de la `CRBTree` objeto.  
  
```
void RemoveAll() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Borra la `CRBTree` objeto, liberando la memoria utilizada para almacenar los elementos.  
  
##  <a name="a-nameremoveata--crbtreeremoveat"></a><a name="removeat"></a>CRBTree::RemoveAt  
 Llamar a este método para quitar el elemento de la posición especificada en el **CRBTree** objeto.  
  
```
void RemoveAt(POSITION pos) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El contador de posición, devuelto por una llamada anterior a métodos como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
### <a name="remarks"></a>Comentarios  
 Quita el par clave/valor almacenado en la posición especificada. Se libera la memoria utilizada para almacenar el elemento. Hace referencia la posición `pos` deja de ser válido y mientras la posición de los demás elementos en el árbol de sigue siendo válida, que no siempre conservan el mismo orden.  
  
##  <a name="a-namesetvalueata--crbtreesetvalueat"></a><a name="setvalueat"></a>CRBTree::SetValueAt  
 Llamar a este método para cambiar el valor almacenado en una posición determinada en la `CRBTree` objeto.  
  
```
void SetValueAt(POSITION pos, VINARGTYPE value);
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El contador de posición, devuelto por una llamada anterior a métodos como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
 *value*  
 El valor que se va a agregar a la `CRBTree` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Cambia el elemento de valor almacenado en la posición especificada en el `CRBTree` objeto.  
  
##  <a name="a-namevinargtypea--crbtreevinargtype"></a><a name="vinargtype"></a>CRBTree::VINARGTYPE  
 Tipo que se utiliza cuando se pasa un valor como argumento de entrada.  
  
```
typedef VTraits::INARGTYPE VINARGTYPE;
```  
  
##  <a name="a-namevoutargtypea--crbtreevoutargtype"></a><a name="voutargtype"></a>CRBTree::VOUTARGTYPE  
 Tipo que se utiliza cuando se pasa un valor como un argumento de salida.  
  
```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)

