---
title: Clase CAtlMap
ms.date: 11/04/2016
f1_keywords:
- CAtlMap
- ATLCOLL/ATL::CAtlMap
- ATLCOLL/ATL::CAtlMap::KINARGTYPE
- ATLCOLL/ATL::CAtlMap::KOUTARGTYPE
- ATLCOLL/ATL::CAtlMap::VINARGTYPE
- ATLCOLL/ATL::CAtlMap::VOUTARGTYPE
- ATLCOLL/ATL::CPair::m_key
- ATLCOLL/ATL::CPair::m_value
- ATLCOLL/ATL::CAtlMap::CAtlMap
- ATLCOLL/ATL::CAtlMap::AssertValid
- ATLCOLL/ATL::CAtlMap::DisableAutoRehash
- ATLCOLL/ATL::CAtlMap::EnableAutoRehash
- ATLCOLL/ATL::CAtlMap::GetAt
- ATLCOLL/ATL::CAtlMap::GetCount
- ATLCOLL/ATL::CAtlMap::GetHashTableSize
- ATLCOLL/ATL::CAtlMap::GetKeyAt
- ATLCOLL/ATL::CAtlMap::GetNext
- ATLCOLL/ATL::CAtlMap::GetNextAssoc
- ATLCOLL/ATL::CAtlMap::GetNextKey
- ATLCOLL/ATL::CAtlMap::GetNextValue
- ATLCOLL/ATL::CAtlMap::GetStartPosition
- ATLCOLL/ATL::CAtlMap::GetValueAt
- ATLCOLL/ATL::CAtlMap::InitHashTable
- ATLCOLL/ATL::CAtlMap::IsEmpty
- ATLCOLL/ATL::CAtlMap::Lookup
- ATLCOLL/ATL::CAtlMap::Rehash
- ATLCOLL/ATL::CAtlMap::RemoveAll
- ATLCOLL/ATL::CAtlMap::RemoveAtPos
- ATLCOLL/ATL::CAtlMap::RemoveKey
- ATLCOLL/ATL::CAtlMap::SetAt
- ATLCOLL/ATL::CAtlMap::SetOptimalLoad
- ATLCOLL/ATL::CAtlMap::SetValueAt
helpviewer_keywords:
- CAtlMap class
ms.assetid: 5e2fe028-8e6d-4686-93df-1433d2080ec3
ms.openlocfilehash: 8954eeae28f13fb50643646b41c032588ecc278f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748657"
---
# <a name="catlmap-class"></a>Clase CAtlMap

Esta clase proporciona métodos para crear y administrar un objeto de mapa.

## <a name="syntax"></a>Sintaxis

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CAtlMap
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
|[CAtlMap::KINARGTYPE](#kinargtype)|Tipo utilizado cuando se pasa una clave como argumento de entrada|
|[CAtlMap::KOUTARGTYPE](#koutargtype)|Tipo utilizado cuando se devuelve una clave como argumento de salida.|
|[CAtlMap::VINARGTYPE](#vinargtype)|Tipo utilizado cuando se pasa un valor como argumento de entrada.|
|[CAtlMap::VOUTARGTYPE](#voutargtype)|Tipo utilizado cuando se pasa un valor como argumento de salida.|

### <a name="public-classes"></a>Clases públicas

|Nombre|Descripción|
|----------|-----------------|
|[CAtlMap::CPair (clase)](#cpair_class)|Clase que contiene los elementos key y value.|

### <a name="cpair-data-members"></a>Miembros de datos de CPair

|Nombre|Descripción|
|----------|-----------------|
|[CPair::m_key](#m_key)|El miembro de datos que almacena el elemento de clave.|
|[CPair::m_value](#m_value)|El miembro de datos que almacena el elemento value.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlMap::CAtlMap](#catlmap)|El constructor.|
|[CAtlMap::-CAtlMap](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlMap::AssertValid](#assertvalid)|Llame a este método para `CAtlMap` provocar un ASSERT si el no es válido.|
|[CAtlMap::DisableAutoRehash](#disableautorehash)|Llame a este método para deshabilitar `CAtlMap` el rehashing automático del objeto.|
|[CAtlMap::EnableAutoRehash](#enableautorehash)|Llame a este método para habilitar `CAtlMap` el rehashing automático del objeto.|
|[CAtlMap::GetAt](#getat)|Llame a este método para devolver el elemento en una posición especificada en el mapa.|
|[CAtlMap::GetCount](#getcount)|Llame a este método para recuperar el número de elementos en el mapa.|
|[CAtlMap::GetHashTableSize](#gethashtablesize)|Llame a este método para determinar el número de ubicaciones en la tabla hash del mapa.|
|[CAtlMap::GetKeyAt](#getkeyat)|Llame a este método para recuperar la `CAtlMap` clave almacenada en la posición dada en el objeto.|
|[CAtlMap::GetNext](#getnext)|Llame a este método para obtener un puntero `CAtlMap` al siguiente par de elementos almacenado en el objeto.|
|[CAtlMap::GetNextAssoc](#getnextassoc)|Obtiene el siguiente elemento para iterar.|
|[CAtlMap::GetNextKey](#getnextkey)|Llame a este método para `CAtlMap` recuperar la siguiente clave del objeto.|
|[CAtlMap::GetNextValue](#getnextvalue)|Llame a este método para `CAtlMap` obtener el siguiente valor del objeto.|
|[CAtlMap::GetStartPosition](#getstartposition)|Llame a este método para iniciar una iteración de mapa.|
|[CAtlMap::GetValueAt](#getvalueat)|Llame a este método para recuperar el `CAtlMap` valor almacenado en una posición determinada en el objeto.|
|[CAtlMap::InitHashTable](#inithashtable)|Llame a este método para inicializar la tabla hash.|
|[CAtlMap::IsEmpty](#isempty)|Llame a este método para probar un objeto de mapa vacío.|
|[CAtlMap::Lookup](#lookup)|Llame a este método para buscar `CAtlMap` claves o valores en el objeto.|
|[CAtlMap::Rehash](#rehash)|Llame a este método `CAtlMap` para volver a hash el objeto.|
|[CAtlMap::RemoveAll](#removeall)|Llame a este método para `CAtlMap` quitar todos los elementos del objeto.|
|[CAtlMap::RemoveAtPos](#removeatpos)|Llame a este método para quitar el `CAtlMap` elemento en la posición dada en el objeto.|
|[CAtlMap::RemoveKey](#removekey)|Llame a este método para `CAtlMap` quitar un elemento del objeto, dada la clave.|
|[CAtlMap::SetAt](#setat)|Llame a este método para insertar un par de elementos en el mapa.|
|[CAtlMap::SetOptimalLoad](#setoptimalload)|Llame a este método para `CAtlMap` establecer la carga óptima del objeto.|
|[CAtlMap::SetValueAt](#setvalueat)|Llame a este método para cambiar el `CAtlMap` valor almacenado en una posición determinada en el objeto.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlMap::operator\[\]](catlmap-class.md#operator_at)|Reemplaza o agrega un nuevo `CAtlMap`elemento al archivo .|

## <a name="remarks"></a>Observaciones

`CAtlMap`proporciona compatibilidad con una matriz de asignación de cualquier tipo determinado, administrando una matriz desordenada de elementos clave y sus valores asociados. Los elementos (que constan de una clave y un valor) se almacenan mediante un algoritmo hash, lo que permite almacenar y recuperar de forma eficaz una gran cantidad de datos.

Los *parámetros KTraits* y *VTraits* son clases de rasgos que contienen cualquier código suplementario necesario para copiar o mover elementos.

La clase `CAtlMap` CRBMap ofrece una alternativa a la que ofrece la clase [CRBMap.](../../atl/reference/crbmap-class.md) `CRBMap`también almacena pares clave/valor, pero exhibe diferentes características de rendimiento. El tiempo necesario para insertar un elemento, buscar una `CRBMap` clave o eliminar una clave de un objeto es de *registro de pedido(n),* donde *n* es el número de elementos. Para `CAtlMap`, todas estas operaciones suelen tardar un tiempo constante, aunque los peores escenarios pueden ser de orden *n*. Por lo tanto, `CAtlMap` en un caso típico, es más rápido.

La otra `CRBMap` diferencia `CAtlMap` entre y se hace evidente al recorrer en iteración los elementos almacenados. En `CRBMap`un , los elementos se visitan en un orden ordenado. En `CAtlMap`un , los elementos no se ordenan y no se puede deducir ningún orden.

Cuando sea necesario almacenar un pequeño número de elementos, considere la posibilidad de usar la [clase CSimpleMap](../../atl/reference/csimplemap-class.md) en su lugar.

Para obtener más información, vea Clases de [colección ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

## <a name="catlmapassertvalid"></a><a name="assertvalid"></a>CAtlMap::AssertValid

Llame a este método para `CAtlMap` provocar un ASSERT si el objeto no es válido.

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>Observaciones

En compilaciones de depuración, este `CAtlMap` método provocará un ASSERT si el objeto no es válido.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapcatlmap"></a><a name="catlmap"></a>CAtlMap::CAtlMap

El constructor.

```
CAtlMap(
    UINT nBins = 17,
    float fOptimalLoad = 0.75f,
    float fLoThreshold = 0.25f,
    float fHiThreshold = 2.25f,
    UINT nBlockSize = 10) throw ();
```

### <a name="parameters"></a>Parámetros

*nBins*<br/>
El número de ubicaciones que proporcionan punteros a los elementos almacenados. Consulte Comentarios más adelante en este tema para obtener una explicación de las ubicaciones.

*fOptimalLoad*<br/>
La relación de carga óptima.

*fLoThreshold*<br/>
El umbral inferior para la relación de carga.

*fHiThreshold*<br/>
El umbral superior para la relación de carga.

*nBlockSize*<br/>
Tamaño de bloque.

### <a name="remarks"></a>Observaciones

`CAtlMap`haciendo referencia a todos sus elementos almacenados creando primero un índice mediante un algoritmo hash en la clave. Este índice hace referencia a un "bin" que contiene un puntero a los elementos almacenados. Si la ubicación ya está en uso, se crea una lista vinculada para tener acceso a los elementos subsiguientes. Atravesar una lista es más lento que acceder directamente al elemento correcto, por lo que la estructura de mapa debe equilibrar los requisitos de almacenamiento con el rendimiento. Los parámetros predeterminados se han elegido para dar buenos resultados en la mayoría de los casos.

La relación de carga es la relación entre el número de ubicaciones y el número de elementos almacenados en el objeto de mapa. Cuando se vuelve a calcular la estructura de mapa, se utilizará el valor del parámetro *fOptimalLoad* para calcular el número de ubicaciones necesarias. Este valor se puede cambiar mediante el [CAtlMap::SetOptimalLoad](#setoptimalload) método.

El parámetro *fLoThreshold* es el valor inferior `CAtlMap` que la relación de carga puede alcanzar antes volverá a calcular el tamaño óptimo del mapa.

El parámetro *fHiThreshold* es el valor superior que `CAtlMap` la relación de carga puede alcanzar antes de que el objeto vuelva a calcular el tamaño óptimo del mapa.

Este proceso de recálculo (conocido como rehashing) está habilitado de forma predeterminada. Si desea deshabilitar este proceso, tal vez al introducir una gran cantidad de datos a la vez, llame a la [CAtlMap::DisableAutoRehash](#disableautorehash) método. Reactivarlo con el [CAtlMap::EnableAutoRehash](#enableautorehash) método.

El *nBlockSize* parámetro es una medida de la cantidad de memoria asignada cuando se requiere un nuevo elemento. Los tamaños de bloque más grandes reducen las llamadas a rutinas de asignación de memoria, pero usan más recursos.

Antes de que se puedan almacenar datos, es necesario inicializar la tabla hash con una llamada a [CAtlMap::InitHashTable](#inithashtable).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]

## <a name="catlmapcatlmap"></a><a name="dtor"></a>CAtlMap::-CAtlMap

Destructor.

```
~CAtlMap() throw();
```

### <a name="remarks"></a>Observaciones

Libera los recursos asignados.

## <a name="catlmapcpair-class"></a><a name="cpair_class"></a>CAtlMap::CPair (clase)

Clase que contiene los elementos key y value.

```
class CPair : public __POSITION
```

### <a name="remarks"></a>Observaciones

Esta clase es utilizada por los métodos [CAtlMap::GetNext](#getnext) y [CAtlMap::Lookup](#lookup) para tener acceso a los elementos de clave y valor almacenados en la estructura de asignación.

## <a name="catlmapdisableautorehash"></a><a name="disableautorehash"></a>CAtlMap::DisableAutoRehash

Llame a este método para deshabilitar `CAtlMap` el rehashing automático del objeto.

```cpp
void DisableAutoRehash() throw();
```

### <a name="remarks"></a>Observaciones

Cuando se habilita el rehashing automático (que es de forma predeterminada), el número de ubicaciones en la tabla hash se volverá a calcular automáticamente si el valor de carga (la proporción del número de ubicaciones con el número de elementos almacenados en la matriz) supera los valores máximos o mínimos especificados en el momento en que se creó el mapa.

`DisableAutoRehash`es más útil cuando se agregará un gran número de elementos al mapa a la vez. En lugar de desencadenar el proceso de rehashing cada vez `DisableAutoRehash`que se superan los límites, es más eficaz llamar a , agregar los elementos y, finalmente, llamar a [CAtlMap::EnableAutoRehash](#enableautorehash).

## <a name="catlmapenableautorehash"></a><a name="enableautorehash"></a>CAtlMap::EnableAutoRehash

Llame a este método para habilitar `CAtlMap` el rehashing automático del objeto.

```cpp
void EnableAutoRehash() throw();
```

### <a name="remarks"></a>Observaciones

Cuando se habilita el rehashing automático (que es de forma predeterminada), el número de ubicaciones en la tabla hash se volverá a calcular automáticamente si el valor de carga (la proporción del número de ubicaciones con el número de elementos almacenados en la matriz) supera los valores máximos o mínimos especificados en el momento en que se crea el mapa.

`EnableAutoRefresh`se utiliza con mayor frecuencia después de una llamada a [CAtlMap::DisableAutoRehash](#disableautorehash).

## <a name="catlmapgetat"></a><a name="getat"></a>CAtlMap::GetAt

Llame a este método para devolver el elemento en una posición especificada en el mapa.

```cpp
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).

*key*<br/>
Parámetro de plantilla que especifica el tipo de clave del mapa.

*value*<br/>
Parámetro de plantilla que especifica el tipo del valor del mapa.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al par actual de elementos clave/valor almacenados en el mapa.

### <a name="remarks"></a>Observaciones

En compilaciones de depuración, se producirá un error de aserción si *pos* es igual a NULL.

## <a name="catlmapgetcount"></a><a name="getcount"></a>CAtlMap::GetCount

Llame a este método para recuperar el número de elementos en el mapa.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de elementos del objeto de mapa. Un solo elemento es un par clave/valor.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapgethashtablesize"></a><a name="gethashtablesize"></a>CAtlMap::GetHashTableSize

Llame a este método para determinar el número de ubicaciones en la tabla hash del mapa.

```
UINT GetHashTableSize() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de ubicaciones de la tabla hash. Consulte [CAtlMap::CAtlMap](#catlmap) para obtener una explicación.

## <a name="catlmapgetkeyat"></a><a name="getkeyat"></a>CAtlMap::GetKeyAt

Llame a este método para recuperar la `CAtlMap` clave almacenada en la posición dada en el objeto.

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia a la clave almacenada `CAtlMap` en la posición dada en el objeto.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapgetnext"></a><a name="getnext"></a>CAtlMap::GetNext

Llame a este método para obtener un puntero `CAtlMap` al siguiente par de elementos almacenado en el objeto.

```
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al siguiente par de elementos clave/valor almacenados en el mapa. El contador de posición *pos* se actualiza después de cada llamada. Si el elemento recuperado es el último en el mapa, *pos* se establece en NULL.

## <a name="catlmapgetnextassoc"></a><a name="getnextassoc"></a>CAtlMap::GetNextAssoc

Obtiene el siguiente elemento para iterar.

```cpp
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).

*key*<br/>
Parámetro de plantilla que especifica el tipo de clave del mapa.

*value*<br/>
Parámetro de plantilla que especifica el tipo del valor del mapa.

### <a name="remarks"></a>Observaciones

El contador de posición *pos* se actualiza después de cada llamada. Si el elemento recuperado es el último en el mapa, *pos* se establece en NULL.

## <a name="catlmapgetnextkey"></a><a name="getnextkey"></a>CAtlMap::GetNextKey

Llame a este método para `CAtlMap` recuperar la siguiente clave del objeto.

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia a la siguiente clave del mapa.

### <a name="remarks"></a>Observaciones

Actualiza el contador de posición actual, *pos*. Si no hay más entradas en el mapa, el contador de posiciones se establece en NULL.

## <a name="catlmapgetnextvalue"></a><a name="getnextvalue"></a>CAtlMap::GetNextValue

Llame a este método para `CAtlMap` obtener el siguiente valor del objeto.

```
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al siguiente valor del mapa.

### <a name="remarks"></a>Observaciones

Actualiza el contador de posición actual, *pos*. Si no hay más entradas en el mapa, el contador de posiciones se establece en NULL.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapgetstartposition"></a><a name="getstartposition"></a>CAtlMap::GetStartPosition

Llame a este método para iniciar una iteración de mapa.

```
POSITION GetStartPosition() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la posición inicial o se devuelve NULL si el mapa está vacío.

### <a name="remarks"></a>Observaciones

Llame a este método para iniciar una iteración de `GetNextAssoc` mapa devolviendo un position valor que se puede pasar al método.

> [!NOTE]
> La secuencia de iteración no es predecible

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapgetvalueat"></a><a name="getvalueat"></a>CAtlMap::GetValueAt

Llame a este método para recuperar el `CAtlMap` valor almacenado en una posición determinada en el objeto.

```
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al valor almacenado en `CAtlMap` la posición dada en el objeto.

## <a name="catlmapinithashtable"></a><a name="inithashtable"></a>CAtlMap::InitHashTable

Llame a este método para inicializar la tabla hash.

```
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```

### <a name="parameters"></a>Parámetros

*nBins*<br/>
El número de ubicaciones utilizadas por la tabla hash. Consulte [CAtlMap::CAtlMap](#catlmap) para obtener una explicación.

*bAllocNow*<br/>
Una indicación de marca cuando se debe asignar memoria.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en la inicialización correcta, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

`InitHashTable`debe llamarse antes de que los elementos se almacenen en la tabla hash.  Si no se llama explícitamente a este método, se llamará automáticamente la primera vez `CAtlMap` que se agregue un elemento mediante el recuento de ubicaciones especificado por el constructor.  De lo contrario, el mapa se inicializará utilizando el nuevo recuento de bins especificado por el parámetro *nBins.*

Si el parámetro *bAllocNow* es false, la memoria requerida por la tabla hash no se asignará hasta que se requiera por primera vez. Esto puede ser útil si no se sabe si se utilizará el mapa.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapisempty"></a><a name="isempty"></a>CAtlMap::IsEmpty

Llame a este método para probar un objeto de mapa vacío.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el mapa está vacío, FALSE en caso contrario.

## <a name="catlmapkinargtype"></a><a name="kinargtype"></a>CAtlMap::KINARGTYPE

Tipo utilizado cuando se pasa una clave como argumento de entrada.

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="catlmapkoutargtype"></a><a name="koutargtype"></a>CAtlMap::KOUTARGTYPE

Tipo utilizado cuando se devuelve una clave como argumento de salida.

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="catlmaplookup"></a><a name="lookup"></a>CAtlMap::Lookup

Llame a este método para buscar `CAtlMap` claves o valores en el objeto.

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Especifica la clave que identifica el elemento que se va a buscar.

*value*<br/>
Variable que recibe el valor buscado.

### <a name="return-value"></a>Valor devuelto

La primera forma del método devuelve true si se encuentra la clave, de lo contrario false. La segunda y tercera formas devuelven un puntero a un [CPair](#cpair_class) que se puede utilizar como una posición para las llamadas a [CAtlMap::GetNext](#getnext) y así sucesivamente.

### <a name="remarks"></a>Observaciones

`Lookup`utiliza un algoritmo hash para encontrar rápidamente el elemento de mapa que contiene una clave que coincide exactamente con el parámetro de clave especificado.

## <a name="catlmapoperator-"></a><a name="operator_at"></a>CAtlMap::operator\[\]

Reemplaza o agrega un nuevo `CAtlMap`elemento al archivo .

```
V& operator[](kinargtype key) throw();
```

### <a name="parameters"></a>Parámetros

*key*<br/>
La clave del elemento que se va a agregar o reemplazar.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al valor asociado a la clave dada.

### <a name="example"></a>Ejemplo

Si la clave ya existe, se reemplaza el elemento. Si la clave no existe, se agrega un nuevo elemento. Vea el ejemplo de [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmaprehash"></a><a name="rehash"></a>CAtlMap::Rehash

Llame a este método `CAtlMap` para volver a hash el objeto.

```cpp
void Rehash(UINT nBins = 0);
```

### <a name="parameters"></a>Parámetros

*nBins*<br/>
El nuevo número de ubicaciones que se utilizarán en la tabla hash. Consulte [CAtlMap::CAtlMap](#catlmap) para obtener una explicación.

### <a name="remarks"></a>Observaciones

Si *nBins* es `CAtlMap` 0, calcula un número razonable en función del número de elementos del mapa y de la configuración de carga óptima. Normalmente, el proceso de rehashing es automático, pero si se ha llamado [a CAtlMap::DisableAutoRehash,](#disableautorehash) este método realizará el cambio de tamaño necesario.

## <a name="catlmapremoveall"></a><a name="removeall"></a>CAtlMap::RemoveAll

Llame a este método para `CAtlMap` quitar todos los elementos del objeto.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>Observaciones

Borra el `CAtlMap` objeto, liberando la memoria utilizada para almacenar los elementos.

## <a name="catlmapremoveatpos"></a><a name="removeatpos"></a>CAtlMap::RemoveAtPos

Llame a este método para quitar el `CAtlMap` elemento en la posición dada en el objeto.

```cpp
void RemoveAtPos(POSITION pos) throw();
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).

### <a name="remarks"></a>Observaciones

Elimina el par clave/valor almacenado en la posición especificada. La memoria utilizada para almacenar el elemento se libera. La POSITION a la que hace referencia *pos* deja de ser válida y, aunque la POSITION de cualquier otro elemento del mapa sigue siendo válida, no necesariamente conservan el mismo orden.

## <a name="catlmapremovekey"></a><a name="removekey"></a>CAtlMap::RemoveKey

Llame a este método para `CAtlMap` quitar un elemento del objeto, dada la clave.

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parámetros

*key*<br/>
La clave correspondiente al par de elementos que desea quitar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se encuentra y quita la clave, FALSE en caso de error.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapsetat"></a><a name="setat"></a>CAtlMap::SetAt

Llame a este método para insertar un par de elementos en el mapa.

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
El valor de clave `CAtlMap` que se va a agregar al objeto.

*value*<br/>
El valor que `CAtlMap` se va a agregar al objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve la posición del par clave/valor del elemento en el `CAtlMap` objeto.

### <a name="remarks"></a>Observaciones

`SetAt`reemplaza un elemento existente si se encuentra una clave coincidente. Si no se encuentra la clave, se crea un nuevo par clave/valor.

## <a name="catlmapsetoptimalload"></a><a name="setoptimalload"></a>CAtlMap::SetOptimalLoad

Llame a este método para `CAtlMap` establecer la carga óptima del objeto.

```cpp
void SetOptimalLoad(
    float fOptimalLoad,
    float fLoThreshold,
    float fHiThreshold,
    bool bRehashNow = false);
```

### <a name="parameters"></a>Parámetros

*fOptimalLoad*<br/>
La relación de carga óptima.

*fLoThreshold*<br/>
El umbral inferior para la relación de carga.

*fHiThreshold*<br/>
El umbral superior para la relación de carga.

*bRehashNow*<br/>
Marcador que indica si se debe volver a calcular la tabla hash.

### <a name="remarks"></a>Observaciones

Este método redefine el valor `CAtlMap` de carga óptimo para el objeto. Consulte [CAtlMap::CAtlMap](#catlmap) para obtener una explicación de los distintos parámetros. Si *bRehashNow* es true y el número de elementos está fuera de los valores mínimo y máximo, se vuelve a calcular la tabla hash.

## <a name="catlmapsetvalueat"></a><a name="setvalueat"></a>CAtlMap::SetValueAt

Llame a este método para cambiar el `CAtlMap` valor almacenado en una posición determinada en el objeto.

```cpp
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).

*value*<br/>
El valor que `CAtlMap` se va a agregar al objeto.

### <a name="remarks"></a>Observaciones

Cambia el elemento de valor almacenado `CAtlMap` en la posición dada en el objeto.

## <a name="catlmapvinargtype"></a><a name="vinargtype"></a>CAtlMap::VINARGTYPE

Tipo utilizado cuando se pasa un valor como argumento de entrada.

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="catlmapvoutargtype"></a><a name="voutargtype"></a>CAtlMap::VOUTARGTYPE

Tipo utilizado cuando se pasa un valor como argumento de salida.

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="catlmapcpairm_key"></a><a name="m_key"></a>CAtlMap::CPair::m_key

El miembro de datos que almacena el elemento de clave.

```
const K m_key;
```

### <a name="parameters"></a>Parámetros

*K*<br/>
El tipo de elemento clave.

## <a name="catlmapcpairm_value"></a><a name="m_value"></a>CAtlMap::CPair::m_value

El miembro de datos que almacena el elemento value.

```
V  m_value;
```

### <a name="parameters"></a>Parámetros

*Ⅴ*<br/>
El tipo de elemento value.

## <a name="see-also"></a>Vea también

[Muestra de marquesina](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
