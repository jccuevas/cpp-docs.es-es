---
title: CRBTree (clase)
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
ms.openlocfilehash: a0f66e888220fbc5a4a484ddd37a3f28dff66065
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583279"
---
# <a name="crbtree-class"></a>CRBTree (clase)

Esta clase proporciona métodos para la creación y uso de un árbol rojo-negro.

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
El tipo de elemento de clave.

*V*<br/>
El tipo de elemento de valor.

*KTraits*<br/>
El código utilizado para copiar o mover los elementos clave. Consulte [CElementTraits (clase)](../../atl/reference/celementtraits-class.md) para obtener más detalles.

*VTraits*<br/>
El código utilizado para copiar o mover elementos de valor.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|[CRBTree::KINARGTYPE](#kinargtype)|Tipo que se utiliza cuando se pasa una clave como un argumento de entrada.|
|[CRBTree::KOUTARGTYPE](#koutargtype)|Tipo que se usa cuando una clave se devuelve como un argumento de salida.|
|[CRBTree::VINARGTYPE](#vinargtype)|Tipo que se utiliza cuando se pasa un valor como argumento de entrada.|
|[CRBTree::VOUTARGTYPE](#voutargtype)|Tipo que se utiliza cuando se pasa un valor como un argumento de salida.|

### <a name="public-classes"></a>Clases públicas

|Name|Descripción|
|----------|-----------------|
|[Clase CRBTree::CPair](#cpair_class)|Una clase que contiene los elementos clave y valor.|

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CRBTree:: ~ CRBTree](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)|Llame a este método para buscar la posición del elemento que se usa la siguiente clave disponible.|
|[CRBTree::GetAt](#getat)|Llame a este método para obtener el elemento en una posición determinada en el árbol.|
|[CRBTree::GetCount](#getcount)|Llame a este método para obtener el número de elementos en el árbol.|
|[CRBTree::GetHeadPosition](#getheadposition)|Llame a este método para obtener el valor de posición para el elemento al principio del árbol.|
|[CRBTree::GetKeyAt](#getkeyat)|Llame a este método para obtener la clave de una posición especificada en el árbol.|
|[CRBTree::GetNext](#getnext)|Llame a este método para obtener un puntero a un elemento almacenado en el `CRBTree` de objetos y avanzar la posición en el elemento siguiente.|
|[CRBTree::GetNextAssoc](#getnextassoc)|Llame a este método para obtener la clave y valor de un elemento almacenado en el mapa y avanzar la posición en el elemento siguiente.|
|[CRBTree::GetNextKey](#getnextkey)|Llame a este método para obtener la clave de un elemento almacenado en el árbol y avanzar la posición en el elemento siguiente.|
|[CRBTree::GetNextValue](#getnextvalue)|Llame a este método para obtener el valor de un elemento almacenado en el árbol y avanzar la posición en el elemento siguiente.|
|[CRBTree::GetPrev](#getprev)|Llame a este método para obtener un puntero a un elemento almacenado en el `CRBTree` de objetos y, a continuación, actualiza la posición para el elemento anterior.|
|[CRBTree::GetTailPosition](#gettailposition)|Llame a este método para obtener el valor de la posición del elemento en la cola del árbol.|
|[CRBTree::GetValueAt](#getvalueat)|Llame a este método para recuperar el valor almacenado en una posición determinada en el `CRBTree` objeto.|
|[CRBTree::IsEmpty](#isempty)|Llame a este método para probar un objeto de árbol vacía.|
|[CRBTree::RemoveAll](#removeall)|Llame a este método para quitar todos los elementos de la `CRBTree` objeto.|
|[CRBTree::RemoveAt](#removeat)|Llame a este método para quitar el elemento en la posición especificada en el `CRBTree` objeto.|
|[CRBTree::SetValueAt](#setvalueat)|Llame a este método para cambiar el valor almacenado en una posición determinada en el `CRBTree` objeto.|

## <a name="remarks"></a>Comentarios

Un árbol rojo-negro es un árbol de búsqueda binaria que usa un archivo extra algo de información por nodo para garantizar que permanece "equilibrado", que es, el alto de árbol no crezca desproporcionadamente grande y afectar al rendimiento.

Esta clase de plantilla está diseñada para usarse por [CRBMap](../../atl/reference/crbmap-class.md) y [CRBMultiMap](../../atl/reference/crbmultimap-class.md). Proporciona la mayor parte de los métodos que componen estas clases derivadas `CRBTree`.

Para obtener una explicación más completa de las distintas clases de colección y sus características y las características de rendimiento, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

##  <a name="cpair_class"></a>  Clase CRBTree::CPair

Una clase que contiene los elementos clave y valor.

```
class CPair : public __POSITION
```

### <a name="remarks"></a>Comentarios

Esta clase se utiliza los métodos [CRBTree::GetAt](#getat), [CRBTree::GetNext](#getnext), y [CRBTree::GetPrev](#getprev) para tener acceso a los elementos clave y el valor almacenados en la estructura de árbol.

Los miembros son los siguientes:

|||
|-|-|
|`m_key`|Almacenar el elemento clave de miembro de datos.|
|`m_value`|El miembro de datos almacenar el elemento de valor.|

##  <a name="dtor"></a>  CRBTree:: ~ CRBTree

Destructor.

```
~CRBTree() throw();
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados. Las llamadas [CRBTree::RemoveAll](#removeall) para eliminar todos los elementos.

##  <a name="findfirstkeyafter"></a>  CRBTree::FindFirstKeyAfter

Llame a este método para buscar la posición del elemento que se usa la siguiente clave disponible.

```
POSITION FindFirstKeyAfter(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Un valor de clave.

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de la posición del elemento que se usa la siguiente clave disponible. Si no hay ningún elemento más, se devuelve NULL.

### <a name="remarks"></a>Comentarios

Este método facilita recorrer el árbol sin tener que calcular los valores de posición con antelación.

##  <a name="getat"></a>  CRBTree::GetAt

Llame a este método para obtener el elemento en una posición determinada en el árbol.

```
CPair* GetAt(POSITION pos) throw();
const CPair* GetAt(POSITION pos) const throw();
void GetAt(POSITION pos, KOUTARGTYPE key, VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parámetros

*punto de venta*<br/>
El valor de posición.

*key*<br/>
La variable que recibe la clave.

*valor*<br/>
La variable que recibe el valor.

### <a name="return-value"></a>Valor devuelto

Los dos primeros formularios devuelven un puntero a un [CPair](#cpair_class). La tercera forma obtiene una clave y un valor para la posición especificada.

### <a name="remarks"></a>Comentarios

El valor de posición puede previamente determinarse con una llamada a un método como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::GetTailPosition](#gettailposition).

En las compilaciones de depuración, se producirá un error de aserción si *pos* es igual a NULL.

##  <a name="getcount"></a>  CRBTree::GetCount

Llame a este método para obtener el número de elementos en el árbol.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de elementos (cada par clave/valor es un elemento) almacenados en el árbol.

##  <a name="getheadposition"></a>  CRBTree::GetHeadPosition

Llame a este método para obtener el valor de posición para el elemento al principio del árbol.

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de posición para el elemento al principio del árbol.

### <a name="remarks"></a>Comentarios

El valor devuelto por `GetHeadPosition` puede usarse con métodos como [CRBTree::GetKeyAt](#getkeyat) o [CRBTree::GetNext](#getnext) para recorrer el árbol y recuperar valores.

##  <a name="getkeyat"></a>  CRBTree::GetKeyAt

Llame a este método para obtener la clave de una posición especificada en el árbol.

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parámetros

*punto de venta*<br/>
El valor de posición.

### <a name="return-value"></a>Valor devuelto

Devuelve la clave almacenada en la posición *pos* en el árbol.

### <a name="remarks"></a>Comentarios

Si *pos* no es un valor de posición válida, los resultados son imprevisibles. En las compilaciones de depuración, se producirá un error de aserción si *pos* es igual a NULL.

##  <a name="getnext"></a>  CRBTree::GetNext

Llame a este método para obtener un puntero a un elemento almacenado en el `CRBTree` de objetos y avanzar la posición en el elemento siguiente.

```
const CPair* GetNext(POSITION& pos) const throw();
CPair* GetNext(POSITION& pos) throw();
```

### <a name="parameters"></a>Parámetros

*punto de venta*<br/>
El contador de posición, devuelto por una llamada anterior a métodos como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la siguiente [CPair](#cpair_class) valor en el árbol.

### <a name="remarks"></a>Comentarios

El *pos* contador de posición se actualiza después de cada llamada. Si el elemento recuperado es el último en el árbol, *pos* se establece en NULL.

##  <a name="getnextassoc"></a>  CRBTree::GetNextAssoc

Llame a este método para obtener la clave y valor de un elemento almacenado en el mapa y avanzar la posición en el elemento siguiente.

```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parámetros

*punto de venta*<br/>
El contador de posición, devuelto por una llamada anterior a métodos como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

*key*<br/>
Parámetro de plantilla que especifica el tipo de clave del árbol.

*valor*<br/>
Parámetro de plantilla que especifica el tipo de valor del árbol.

### <a name="remarks"></a>Comentarios

El *pos* contador de posición se actualiza después de cada llamada. Si el elemento recuperado es el último en el árbol, *pos* se establece en NULL.

##  <a name="getnextkey"></a>  CRBTree::GetNextKey

Llame a este método para obtener la clave de un elemento almacenado en el árbol y avanzar la posición en el elemento siguiente.

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parámetros

*punto de venta*<br/>
El contador de posición, devuelto por una llamada anterior a métodos como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia a la siguiente clave en el árbol.

### <a name="remarks"></a>Comentarios

Actualiza el contador actual de posición, *pos*. Si no hay ningún más entradas en el árbol, el contador de posición se establece en NULL.

##  <a name="getnextvalue"></a>  CRBTree::GetNextValue

Llame a este método para obtener el valor de un elemento almacenado en el árbol y avanzar la posición en el elemento siguiente.

```
const V& GetNextValue(POSITION& pos) const throw();
V& GetNextValue(POSITION& pos) throw();
```

### <a name="parameters"></a>Parámetros

*punto de venta*<br/>
El contador de posición, devuelto por una llamada anterior a métodos como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al siguiente valor en el árbol.

### <a name="remarks"></a>Comentarios

Actualiza el contador actual de posición, *pos*. Si no hay ningún más entradas en el árbol, el contador de posición se establece en NULL.

##  <a name="getprev"></a>  CRBTree::GetPrev

Llame a este método para obtener un puntero a un elemento almacenado en el `CRBTree` de objetos y, a continuación, actualiza la posición para el elemento anterior.

```
const CPair* GetPrev(POSITION& pos) const throw();
CPair* GetPrev(POSITION& pos) throw();
```

### <a name="parameters"></a>Parámetros

*punto de venta*<br/>
El contador de posición, devuelto por una llamada anterior a métodos como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la anterior [CPair](#cpair_class) valor almacenado en el árbol.

### <a name="remarks"></a>Comentarios

Actualiza el contador actual de posición, *pos*. Si no hay ningún más entradas en el árbol, el contador de posición se establece en NULL.

##  <a name="gettailposition"></a>  CRBTree::GetTailPosition

Llame a este método para obtener el valor de la posición del elemento en la cola del árbol.

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de la posición del elemento en la cola del árbol.

### <a name="remarks"></a>Comentarios

El valor devuelto por `GetTailPosition` puede usarse con métodos como [CRBTree::GetKeyAt](#getkeyat) o [CRBTree::GetPrev](#getprev) para recorrer el árbol y recuperar valores.

##  <a name="getvalueat"></a>  CRBTree::GetValueAt

Llame a este método para recuperar el valor almacenado en una posición determinada en el `CRBTree` objeto.

```
const V& GetValueAt(POSITION pos) const throw();
V& GetValueAt(POSITION pos) throw();
```

### <a name="parameters"></a>Parámetros

*punto de venta*<br/>
El contador de posición, devuelto por una llamada anterior a métodos como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al valor almacenado en la posición especificada en el `CRBTree` objeto.

##  <a name="isempty"></a>  CRBTree::IsEmpty

Llame a este método para probar un objeto de árbol vacía.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el árbol está vacío, FALSE en caso contrario.

##  <a name="kinargtype"></a>  CRBTree::KINARGTYPE

Tipo que se utiliza cuando se pasa una clave como un argumento de entrada.

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

##  <a name="koutargtype"></a>  CRBTree::KOUTARGTYPE

Tipo que se usa cuando una clave se devuelve como un argumento de salida.

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

##  <a name="removeall"></a>  CRBTree::RemoveAll

Llame a este método para quitar todos los elementos de la `CRBTree` objeto.

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Comentarios

Borra la `CRBTree` objeto, libere la memoria utilizada para almacenar los elementos.

##  <a name="removeat"></a>  CRBTree::RemoveAt

Llame a este método para quitar el elemento en la posición especificada en el `CRBTree` objeto.

```
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>Parámetros

*punto de venta*<br/>
El contador de posición, devuelto por una llamada anterior a métodos como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="remarks"></a>Comentarios

Quita el par clave/valor almacenado en la posición especificada. Se libera la memoria usada para almacenar el elemento. La posición hace referencia a *pos* deja de ser válida y, mientras que la posición de cualquier otro elemento en el árbol sigue siendo válida, no necesariamente lo hacen, conservar el mismo orden.

##  <a name="setvalueat"></a>  CRBTree::SetValueAt

Llame a este método para cambiar el valor almacenado en una posición determinada en el `CRBTree` objeto.

```
void SetValueAt(POSITION pos, VINARGTYPE value);
```

### <a name="parameters"></a>Parámetros

*punto de venta*<br/>
El contador de posición, devuelto por una llamada anterior a métodos como [CRBTree::GetHeadPosition](#getheadposition) o [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

*valor*<br/>
Valor que se agrega a la `CRBTree` objeto.

### <a name="remarks"></a>Comentarios

Cambia el elemento de valor almacenado en la posición especificada en el `CRBTree` objeto.

##  <a name="vinargtype"></a>  CRBTree::VINARGTYPE

Tipo que se utiliza cuando se pasa un valor como argumento de entrada.

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

##  <a name="voutargtype"></a>  CRBTree::VOUTARGTYPE

Tipo que se utiliza cuando se pasa un valor como un argumento de salida.

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
