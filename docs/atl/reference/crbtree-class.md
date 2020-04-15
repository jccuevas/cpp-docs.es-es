---
title: CRBTree Clase
ms.date: 11/04/2016
f1_keywords:
- CRBTree
- ATLCOLL/ATL::CRBTree
- ATLCOLL/ATL::CRBTree::KINARGTYPE
- ATLCOLL/ATL::CRBTree::KOUTARGTYPE
- ATLCOLL/ATL::CRBTree::VINARGTYPE
- ATLCOLL/ATL::CRBTree::VOUTARGTYPE
- ATLCOLL/ATL::CRBTree::FindFirstKeyAfter
- ATLCOLL/ATL::CRBTree::GetAt
- ATLCOLL/ATL::CRBTree::GetCount
- ATLCOLL/ATL::CRBTree::GetHeadPosition
- ATLCOLL/ATL::CRBTree::GetKeyAt
- ATLCOLL/ATL::CRBTree::GetNext
- ATLCOLL/ATL::CRBTree::GetNextAssoc
- ATLCOLL/ATL::CRBTree::GetNextKey
- ATLCOLL/ATL::CRBTree::GetNextValue
- ATLCOLL/ATL::CRBTree::GetPrev
- ATLCOLL/ATL::CRBTree::GetTailPosition
- ATLCOLL/ATL::CRBTree::GetValueAt
- ATLCOLL/ATL::CRBTree::IsEmpty
- ATLCOLL/ATL::CRBTree::RemoveAll
- ATLCOLL/ATL::CRBTree::RemoveAt
- ATLCOLL/ATL::CRBTree::SetValueAt
helpviewer_keywords:
- CRBTree class
ms.assetid: a1b1cb63-38e4-4fc2-bb28-f774d1721760
ms.openlocfilehash: 56c9db9d1a7bcd7fe2a2647d8b1339d223c4b66b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331248"
---
# <a name="crbtree-class"></a>CRBTree Clase

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

*K*<br/>
El tipo de elemento clave.

*Ⅴ*<br/>
El tipo de elemento value.

*KTraits*<br/>
El código utilizado para copiar o mover elementos clave. Consulte [CElementTraits (Clase)](../../atl/reference/celementtraits-class.md) para obtener más detalles.

*VTraits*<br/>
El código utilizado para copiar o mover elementos de valor.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|[CRBTree::KINARGTYPE](#kinargtype)|Tipo utilizado cuando se pasa una clave como argumento de entrada.|
|[CRBTree::KOUTARGTYPE](#koutargtype)|Tipo utilizado cuando se devuelve una clave como argumento de salida.|
|[CRBTree::VINARGTYPE](#vinargtype)|Tipo utilizado cuando se pasa un valor como argumento de entrada.|
|[CRBTree::VOUTARGTYPE](#voutargtype)|Tipo utilizado cuando se pasa un valor como argumento de salida.|

### <a name="public-classes"></a>Clases públicas

|Nombre|Descripción|
|----------|-----------------|
|[CRBTree::CPair Clase](#cpair_class)|Clase que contiene los elementos key y value.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRBTree::-CRBTree](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRBTree::FindFirstKeyDespude](#findfirstkeyafter)|Llame a este método para buscar la posición del elemento que utiliza la siguiente clave disponible.|
|[CRBTree::GetAt](#getat)|Llame a este método para obtener el elemento en una posición determinada en el árbol.|
|[CRBTree::GetCount](#getcount)|Llame a este método para obtener el número de elementos en el árbol.|
|[CRBTree::GetHeadPosition](#getheadposition)|Llame a este método para obtener el valor de posición para el elemento en la cabecera del árbol.|
|[CRBTree::GetKeyAt](#getkeyat)|Llame a este método para obtener la clave de una posición determinada en el árbol.|
|[CRBTree::GetNext](#getnext)|Llame a este método para obtener un `CRBTree` puntero a un elemento almacenado en el objeto y avanzar la posición al siguiente elemento.|
|[CRBTree::GetNextAssoc](#getnextassoc)|Llame a este método para obtener la clave y el valor de un elemento almacenado en el mapa y avanzar la posición al siguiente elemento.|
|[CRBTree::GetNextKey](#getnextkey)|Llame a este método para obtener la clave de un elemento almacenado en el árbol y avanzar la posición al siguiente elemento.|
|[CRBTree::GetNextValue](#getnextvalue)|Llame a este método para obtener el valor de un elemento almacenado en el árbol y avanzar la posición al siguiente elemento.|
|[CRBTree::GetPrev](#getprev)|Llame a este método para obtener un `CRBTree` puntero a un elemento almacenado en el objeto y, a continuación, actualice la posición al elemento anterior.|
|[CRBTree::GetTailPosition](#gettailposition)|Llame a este método para obtener el valor de posición para el elemento en la cola del árbol.|
|[CRBTree::GetValueAt](#getvalueat)|Llame a este método para recuperar el `CRBTree` valor almacenado en una posición determinada en el objeto.|
|[CRBTree::IsEmpty](#isempty)|Llame a este método para probar un objeto de árbol vacío.|
|[CRBTree::RemoveAll](#removeall)|Llame a este método para `CRBTree` quitar todos los elementos del objeto.|
|[CRBTree::RemoveAt](#removeat)|Llame a este método para quitar el `CRBTree` elemento en la posición dada en el objeto.|
|[CRBTree::SetValueAt](#setvalueat)|Llame a este método para cambiar el `CRBTree` valor almacenado en una posición determinada en el objeto.|

## <a name="remarks"></a>Observaciones

Un árbol rojo-negro es un árbol de búsqueda binario que utiliza un bit adicional de información por nodo para asegurarse de que permanece "equilibrado", es decir, la altura del árbol no crece desproporcionadamente grande y afecta al rendimiento.

Esta clase de plantilla está diseñada para ser utilizada por [CRBMap](../../atl/reference/crbmap-class.md) y [CRBMultiMap](../../atl/reference/crbmultimap-class.md). La mayor parte de los métodos que `CRBTree`componen estas clases derivadas son proporcionados por .

Para obtener una explicación más completa de las distintas clases de colección y sus características y características de rendimiento, vea Clases de [colección ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

## <a name="crbtreecpair-class"></a><a name="cpair_class"></a>CRBTree::CPair Clase

Clase que contiene los elementos key y value.

```
class CPair : public __POSITION
```

### <a name="remarks"></a>Observaciones

Esta clase la utilizan los métodos [CRBTree::GetAt](#getat), [CRBTree::GetNext](#getnext)y [CRBTree::GetPrev](#getprev) para tener acceso a los elementos de clave y valor almacenados en la estructura de árbol.

Los miembros son los siguientes:

|||
|-|-|
|`m_key`|El miembro de datos que almacena el elemento de clave.|
|`m_value`|El miembro de datos que almacena el elemento value.|

## <a name="crbtreecrbtree"></a><a name="dtor"></a>CRBTree::-CRBTree

Destructor.

```
~CRBTree() throw();
```

### <a name="remarks"></a>Observaciones

Libera los recursos asignados. Llama a [CRBTree::RemoveAll](#removeall) para eliminar todos los elementos.

## <a name="crbtreefindfirstkeyafter"></a><a name="findfirstkeyafter"></a>CRBTree::FindFirstKeyDespude

Llame a este método para buscar la posición del elemento que utiliza la siguiente clave disponible.

```
POSITION FindFirstKeyAfter(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Un valor de clave.

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de posición del elemento que utiliza la siguiente clave disponible. Si no hay más elementos, se devuelve NULL.

### <a name="remarks"></a>Observaciones

Este método facilita el recorrido del árbol sin tener que calcular los valores de posición de antemano.

## <a name="crbtreegetat"></a><a name="getat"></a>CRBTree::GetAt

Llame a este método para obtener el elemento en una posición determinada en el árbol.

```
CPair* GetAt(POSITION pos) throw();
const CPair* GetAt(POSITION pos) const throw();
void GetAt(POSITION pos, KOUTARGTYPE key, VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
Valor de la posición.

*key*<br/>
La variable que recibe la clave.

*value*<br/>
La variable que recibe el valor.

### <a name="return-value"></a>Valor devuelto

Los dos primeros formularios devuelven un puntero a un [CPair](#cpair_class). La tercera forma obtiene una clave y un valor para la posición dada.

### <a name="remarks"></a>Observaciones

El valor de posición se puede determinar previamente con una llamada a un método como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::GetTailPosition](#gettailposition).

En compilaciones de depuración, se producirá un error de aserción si *pos* es igual a NULL.

## <a name="crbtreegetcount"></a><a name="getcount"></a>CRBTree::GetCount

Llame a este método para obtener el número de elementos en el árbol.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de elementos (cada par clave/valor es un elemento) almacenados en el árbol.

## <a name="crbtreegetheadposition"></a><a name="getheadposition"></a>CRBTree::GetHeadPosition

Llame a este método para obtener el valor de posición para el elemento en la cabecera del árbol.

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de posición del elemento en la cabecera del árbol.

### <a name="remarks"></a>Observaciones

El valor `GetHeadPosition` devuelto por se puede utilizar con métodos como [CRBTree::GetKeyAt](#getkeyat) o [CRBTree::GetNext](#getnext) para recorrer el árbol y recuperar valores.

## <a name="crbtreegetkeyat"></a><a name="getkeyat"></a>CRBTree::GetKeyAt

Llame a este método para obtener la clave de una posición determinada en el árbol.

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
Valor de la posición.

### <a name="return-value"></a>Valor devuelto

Devuelve la clave almacenada en la posición *pos* en el árbol.

### <a name="remarks"></a>Observaciones

Si *pos* no es un valor de posición válido, los resultados son impredecibles. En compilaciones de depuración, se producirá un error de aserción si *pos* es igual a NULL.

## <a name="crbtreegetnext"></a><a name="getnext"></a>CRBTree::GetNext

Llame a este método para obtener un `CRBTree` puntero a un elemento almacenado en el objeto y avanzar la posición al siguiente elemento.

```
const CPair* GetNext(POSITION& pos) const throw();
CPair* GetNext(POSITION& pos) throw();
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
El contador de posición, devuelto por una llamada anterior a métodos como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al siguiente [Valor de CPair](#cpair_class) en el árbol.

### <a name="remarks"></a>Observaciones

El contador de posición *pos* se actualiza después de cada llamada. Si el elemento recuperado es el último en el árbol, *pos* se establece en NULL.

## <a name="crbtreegetnextassoc"></a><a name="getnextassoc"></a>CRBTree::GetNextAssoc

Llame a este método para obtener la clave y el valor de un elemento almacenado en el mapa y avanzar la posición al siguiente elemento.

```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
El contador de posición, devuelto por una llamada anterior a métodos como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

*key*<br/>
Parámetro de plantilla que especifica el tipo de clave del árbol.

*value*<br/>
Parámetro de plantilla que especifica el tipo del valor del árbol.

### <a name="remarks"></a>Observaciones

El contador de posición *pos* se actualiza después de cada llamada. Si el elemento recuperado es el último en el árbol, *pos* se establece en NULL.

## <a name="crbtreegetnextkey"></a><a name="getnextkey"></a>CRBTree::GetNextKey

Llame a este método para obtener la clave de un elemento almacenado en el árbol y avanzar la posición al siguiente elemento.

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
El contador de posición, devuelto por una llamada anterior a métodos como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia a la siguiente clave del árbol.

### <a name="remarks"></a>Observaciones

Actualiza el contador de posición actual, *pos*. Si no hay más entradas en el árbol, el contador de posiciones se establece en NULL.

## <a name="crbtreegetnextvalue"></a><a name="getnextvalue"></a>CRBTree::GetNextValue

Llame a este método para obtener el valor de un elemento almacenado en el árbol y avanzar la posición al siguiente elemento.

```
const V& GetNextValue(POSITION& pos) const throw();
V& GetNextValue(POSITION& pos) throw();
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
El contador de posición, devuelto por una llamada anterior a métodos como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al siguiente valor del árbol.

### <a name="remarks"></a>Observaciones

Actualiza el contador de posición actual, *pos*. Si no hay más entradas en el árbol, el contador de posiciones se establece en NULL.

## <a name="crbtreegetprev"></a><a name="getprev"></a>CRBTree::GetPrev

Llame a este método para obtener un `CRBTree` puntero a un elemento almacenado en el objeto y, a continuación, actualice la posición al elemento anterior.

```
const CPair* GetPrev(POSITION& pos) const throw();
CPair* GetPrev(POSITION& pos) throw();
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
El contador de posición, devuelto por una llamada anterior a métodos como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al valor [CPair](#cpair_class) anterior almacenado en el árbol.

### <a name="remarks"></a>Observaciones

Actualiza el contador de posición actual, *pos*. Si no hay más entradas en el árbol, el contador de posiciones se establece en NULL.

## <a name="crbtreegettailposition"></a><a name="gettailposition"></a>CRBTree::GetTailPosition

Llame a este método para obtener el valor de posición para el elemento en la cola del árbol.

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de posición del elemento en la parte central del árbol.

### <a name="remarks"></a>Observaciones

El valor `GetTailPosition` devuelto por se puede utilizar con métodos como [CRBTree::GetKeyAt](#getkeyat) o [CRBTree::GetPrev](#getprev) para recorrer el árbol y recuperar valores.

## <a name="crbtreegetvalueat"></a><a name="getvalueat"></a>CRBTree::GetValueAt

Llame a este método para recuperar el `CRBTree` valor almacenado en una posición determinada en el objeto.

```
const V& GetValueAt(POSITION pos) const throw();
V& GetValueAt(POSITION pos) throw();
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
El contador de posición, devuelto por una llamada anterior a métodos como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al valor almacenado en `CRBTree` la posición dada en el objeto.

## <a name="crbtreeisempty"></a><a name="isempty"></a>CRBTree::IsEmpty

Llame a este método para probar un objeto de árbol vacío.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el árbol está vacío, FALSE en caso contrario.

## <a name="crbtreekinargtype"></a><a name="kinargtype"></a>CRBTree::KINARGTYPE

Tipo utilizado cuando se pasa una clave como argumento de entrada.

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="crbtreekoutargtype"></a><a name="koutargtype"></a>CRBTree::KOUTARGTYPE

Tipo utilizado cuando se devuelve una clave como argumento de salida.

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="crbtreeremoveall"></a><a name="removeall"></a>CRBTree::RemoveAll

Llame a este método para `CRBTree` quitar todos los elementos del objeto.

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Observaciones

Borra el `CRBTree` objeto, liberando la memoria utilizada para almacenar los elementos.

## <a name="crbtreeremoveat"></a><a name="removeat"></a>CRBTree::RemoveAt

Llame a este método para quitar el `CRBTree` elemento en la posición dada en el objeto.

```
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
El contador de posición, devuelto por una llamada anterior a métodos como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="remarks"></a>Observaciones

Elimina el par clave/valor almacenado en la posición especificada. La memoria utilizada para almacenar el elemento se libera. La POSITION a la que hace referencia *pos* deja de ser válida y, aunque la POSITION de cualquier otro elemento del árbol sigue siendo válida, no necesariamente conservan el mismo orden.

## <a name="crbtreesetvalueat"></a><a name="setvalueat"></a>CRBTree::SetValueAt

Llame a este método para cambiar el `CRBTree` valor almacenado en una posición determinada en el objeto.

```
void SetValueAt(POSITION pos, VINARGTYPE value);
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
El contador de posición, devuelto por una llamada anterior a métodos como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

*value*<br/>
El valor que `CRBTree` se va a agregar al objeto.

### <a name="remarks"></a>Observaciones

Cambia el elemento de valor almacenado `CRBTree` en la posición dada en el objeto.

## <a name="crbtreevinargtype"></a><a name="vinargtype"></a>CRBTree::VINARGTYPE

Tipo utilizado cuando se pasa un valor como argumento de entrada.

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="crbtreevoutargtype"></a><a name="voutargtype"></a>CRBTree::VOUTARGTYPE

Tipo utilizado cuando se pasa un valor como argumento de salida.

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
