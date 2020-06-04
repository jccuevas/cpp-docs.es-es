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
ms.openlocfilehash: b79e6cbd796569e6ba11c96158099de6c30b310a
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168064"
---
# <a name="catlmap-class"></a>Clase CAtlMap

Esta clase proporciona métodos para crear y administrar un objeto de mapa.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CAtlMap
```

### <a name="parameters"></a>Parámetros

*K*<br/>
El tipo de elemento de clave.

*V*<br/>
El tipo de elemento de valor.

*KTraits*<br/>
Código que se usa para copiar o quitar elementos clave. Consulte [clase CElementTraits](../../atl/reference/celementtraits-class.md) para obtener más detalles.

*VTraits*<br/>
Código que se usa para copiar o quitar elementos de valor.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|[CAtlMap:: KINARGTYPE](#kinargtype)|Tipo usado cuando se pasa una clave como argumento de entrada|
|[CAtlMap:: KOUTARGTYPE](#koutargtype)|Tipo usado cuando se devuelve una clave como argumento de salida.|
|[CAtlMap:: VINARGTYPE](#vinargtype)|Tipo usado cuando se pasa un valor como argumento de entrada.|
|[CAtlMap:: VOUTARGTYPE](#voutargtype)|Tipo usado cuando se pasa un valor como argumento de salida.|

### <a name="public-classes"></a>Clases públicas

|Nombre|Descripción|
|----------|-----------------|
|[CAtlMap:: CPair (clase)](#cpair_class)|Una clase que contiene los elementos clave y valor.|

### <a name="cpair-data-members"></a>Miembros de datos de CPair

|Nombre|Descripción|
|----------|-----------------|
|[CPair:: m_key](#m_key)|El miembro de datos que almacena el elemento de clave.|
|[CPair:: m_value](#m_value)|El miembro de datos que almacena el elemento de valor.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlMap:: CAtlMap](#catlmap)|El constructor.|
|[CAtlMap:: ~ CAtlMap](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlMap:: AssertValid](#assertvalid)|Llame a este método para producir una ASERCIÓN si `CAtlMap` el no es válido.|
|[CAtlMap::D isableAutoRehash](#disableautorehash)|Llame a este método para deshabilitar el `CAtlMap` rehash automático del objeto.|
|[CAtlMap:: EnableAutoRehash](#enableautorehash)|Llame a este método para habilitar el `CAtlMap` rehash automático del objeto.|
|[CAtlMap:: GetAt](#getat)|Llame a este método para devolver el elemento en una posición especificada del mapa.|
|[CAtlMap:: GetCount](#getcount)|Llame a este método para recuperar el número de elementos del mapa.|
|[CAtlMap:: GetHashTableSize](#gethashtablesize)|Llame a este método para determinar el número de depósitos de la tabla hash del mapa.|
|[CAtlMap:: GetKeyAt](#getkeyat)|Llame a este método para recuperar la clave almacenada en la posición especificada `CAtlMap` en el objeto.|
|[CAtlMap:: GetNext](#getnext)|Llame a este método para obtener un puntero al siguiente par de elementos almacenado en `CAtlMap` el objeto.|
|[CAtlMap:: GetNextAssoc](#getnextassoc)|Obtiene el siguiente elemento para recorrer en iteración.|
|[CAtlMap:: GetNextKey](#getnextkey)|Llame a este método para recuperar la clave siguiente del `CAtlMap` objeto.|
|[CAtlMap:: GetNextValue](#getnextvalue)|Llame a este método para obtener el siguiente valor del `CAtlMap` objeto.|
|[CAtlMap:: GetStartPosition](#getstartposition)|Llame a este método para iniciar una iteración de mapa.|
|[CAtlMap:: GetValueAt](#getvalueat)|Llame a este método para recuperar el valor almacenado en una posición determinada en `CAtlMap` el objeto.|
|[CAtlMap:: InitHashTable](#inithashtable)|Llame a este método para inicializar la tabla hash.|
|[CAtlMap:: IsEmpty](#isempty)|Llame a este método para comprobar si hay un objeto de mapa vacío.|
|[CAtlMap:: Lookup](#lookup)|Llame a este método para buscar claves o valores en el `CAtlMap` objeto.|
|[CAtlMap:: rehash](#rehash)|Llame a este método para rehashar el `CAtlMap` objeto.|
|[CAtlMap:: RemoveAll](#removeall)|Llame a este método para quitar todos los elementos `CAtlMap` del objeto.|
|[CAtlMap:: RemoveAtPos](#removeatpos)|Llame a este método para quitar el elemento en la posición especificada en `CAtlMap` el objeto.|
|[CAtlMap:: RemoveKey](#removekey)|Llame a este método para quitar un elemento del `CAtlMap` objeto, dada la clave.|
|[CAtlMap:: SetAt](#setat)|Llame a este método para insertar un par de elementos en la asignación.|
|[CAtlMap:: SetOptimalLoad](#setoptimalload)|Llame a este método para establecer la carga óptima del `CAtlMap` objeto.|
|[CAtlMap:: SetValueAt](#setvalueat)|Llame a este método para cambiar el valor almacenado en una posición determinada en `CAtlMap` el objeto.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlMap::operator\[\]](catlmap-class.md#operator_at)|Reemplaza o agrega un nuevo elemento a `CAtlMap`.|

## <a name="remarks"></a>Observaciones

`CAtlMap`proporciona compatibilidad para una matriz de asignación de cualquier tipo dado, administrando una matriz sin ordenar de elementos clave y sus valores asociados. Los elementos (que se componen de una clave y un valor) se almacenan mediante un algoritmo hash, lo que permite almacenar y recuperar eficazmente una gran cantidad de datos.

Los parámetros *KTraits* y *VTraits* son clases de rasgos que contienen cualquier código complementario necesario para copiar o quitar elementos.

Una alternativa a `CAtlMap` la ofrece la clase [CRBMap](../../atl/reference/crbmap-class.md) . `CRBMap`también almacena pares clave-valor, pero presenta diferentes características de rendimiento. El tiempo necesario para insertar un elemento, buscar una clave o eliminar una clave de un `CRBMap` objeto es el registro de pedidos *(n)*, donde *n* es el número de elementos. En `CAtlMap`el caso de, todas estas operaciones suelen tardar un tiempo constante, aunque los escenarios en el peor de los casos podrían ser del orden *n*. Por lo tanto, en un caso `CAtlMap` típico, es más rápido.

La otra diferencia entre `CRBMap` y `CAtlMap` se vuelve patente al recorrer en iteración los elementos almacenados. En `CRBMap`, los elementos se visitan en un orden ordenado. En `CAtlMap`, los elementos no están ordenados y no se puede inferir ningún orden.

Cuando sea necesario almacenar un pequeño número de elementos, considere la posibilidad de usar la clase [CSimpleMap](../../atl/reference/csimplemap-class.md) en su lugar.

Para obtener más información, vea [clases de colección ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll. h

## <a name="catlmapassertvalid"></a><a name="assertvalid"></a>CAtlMap:: AssertValid

Llame a este método para producir una ASERCIÓN si `CAtlMap` el objeto no es válido.

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>Observaciones

En las compilaciones de depuración, este método `CAtlMap` producirá una aserción si el objeto no es válido.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlMap:: CAtlMap](#catlmap).

## <a name="catlmapcatlmap"></a><a name="catlmap"></a>CAtlMap:: CAtlMap

El constructor.

```cpp
CAtlMap(
    UINT nBins = 17,
    float fOptimalLoad = 0.75f,
    float fLoThreshold = 0.25f,
    float fHiThreshold = 2.25f,
    UINT nBlockSize = 10) throw ();
```

### <a name="parameters"></a>Parámetros

*nBins*<br/>
El número de ubicaciones que proporcionan punteros a los elementos almacenados. Vea la sección Comentarios más adelante en este tema para obtener una explicación de las ubicaciones.

*fOptimalLoad*<br/>
La proporción de carga óptima.

*fLoThreshold*<br/>
Umbral inferior para la proporción de carga.

*fHiThreshold*<br/>
Umbral superior de la proporción de carga.

*nBlockSize*<br/>
Tamaño de bloque.

### <a name="remarks"></a>Observaciones

`CAtlMap`hace referencia a todos sus elementos almacenados creando primero un índice mediante un algoritmo hash en la clave. Este índice hace referencia a un "bin" que contiene un puntero a los elementos almacenados. Si la ubicación ya está en uso, se crea una lista vinculada para tener acceso a los elementos siguientes. Recorrer una lista es más lento que el acceso directo al elemento correcto, por lo que la estructura del mapa necesita equilibrar los requisitos de almacenamiento con respecto al rendimiento. Los parámetros predeterminados se han elegido para proporcionar buenos resultados en la mayoría de los casos.

La proporción de carga es la proporción entre el número de contenedores y el número de elementos almacenados en el objeto de mapa. Cuando se vuelve a calcular la estructura del mapa, se usará el valor del parámetro *fOptimalLoad* para calcular el número de ubicaciones necesarias. Este valor se puede cambiar mediante el método [CAtlMap:: SetOptimalLoad](#setoptimalload) .

El parámetro *fLoThreshold* es el valor más bajo que puede alcanzar la relación de `CAtlMap` carga antes de que recalcule el tamaño óptimo del mapa.

El parámetro *fHiThreshold* es el valor superior que la proporción de carga puede alcanzar antes `CAtlMap` de que el objeto vuelva a calcular el tamaño óptimo del mapa.

Este proceso de recálculo (conocido como rehashing) está habilitado de forma predeterminada. Si desea deshabilitar este proceso, quizás al escribir muchos datos al mismo tiempo, llame al método [CAtlMap::D isableautorehash](#disableautorehash) . Reactívelo con el método [CAtlMap:: EnableAutoRehash](#enableautorehash) .

El parámetro *nBlockSize* es una medida de la cantidad de memoria asignada cuando se requiere un nuevo elemento. Los tamaños de bloque más grandes reducen las llamadas a rutinas de asignación de memoria, pero usan más recursos.

Antes de que se puedan almacenar los datos, es necesario inicializar la tabla hash con una llamada a [CAtlMap:: InitHashTable](#inithashtable).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]

## <a name="catlmapcatlmap"></a><a name="dtor"></a>CAtlMap:: ~ CAtlMap

Destructor.

```cpp
~CAtlMap() throw();
```

### <a name="remarks"></a>Observaciones

Libera los recursos asignados.

## <a name="catlmapcpair-class"></a><a name="cpair_class"></a>CAtlMap:: CPair (clase)

Una clase que contiene los elementos clave y valor.

```cpp
class CPair : public __POSITION
```

### <a name="remarks"></a>Observaciones

Los métodos [CAtlMap:: Getnext](#getnext) y [CAtlMap:: lookup](#lookup) usan esta clase para tener acceso a los elementos de clave y valor almacenados en la estructura de asignación.

## <a name="catlmapdisableautorehash"></a><a name="disableautorehash"></a>CAtlMap::D isableAutoRehash

Llame a este método para deshabilitar el `CAtlMap` rehash automático del objeto.

```cpp
void DisableAutoRehash() throw();
```

### <a name="remarks"></a>Observaciones

Cuando el rehash automático está habilitado (que es de forma predeterminada), el número de ubicaciones de la tabla hash se volverá a calcular automáticamente si el valor de carga (la proporción entre el número de contenedores y el número de elementos almacenados en la matriz) supera los valores máximo o mínimo especificados en el momento en que se creó la asignación.

`DisableAutoRehash`es muy útil cuando se agrega un gran número de elementos al mapa a la vez. En lugar de desencadenar el proceso de rehashización cada vez que se superan los límites, es más eficaz `DisableAutoRehash`llamar a, agregar los elementos y, por último, llamar a [CAtlMap:: EnableAutoRehash](#enableautorehash).

## <a name="catlmapenableautorehash"></a><a name="enableautorehash"></a>CAtlMap:: EnableAutoRehash

Llame a este método para habilitar el `CAtlMap` rehash automático del objeto.

```cpp
void EnableAutoRehash() throw();
```

### <a name="remarks"></a>Observaciones

Cuando el rehash automático está habilitado (que es de forma predeterminada), el número de ubicaciones de la tabla hash se volverá a calcular automáticamente si el valor de carga (la proporción entre el número de contenedores y el número de elementos almacenados en la matriz) supera los valores máximos o mínimos especificados en el momento en que se crea la asignación.

`EnableAutoRefresh`se suele usar después de una llamada a [CAtlMap::D isableautorehash](#disableautorehash).

## <a name="catlmapgetat"></a><a name="getat"></a>CAtlMap:: GetAt

Llame a este método para devolver el elemento en una posición especificada del mapa.

```cpp
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```

### <a name="parameters"></a>Parámetros

*abre*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap:: GetNextAssoc](#getnextassoc) o [CAtlMap:: GetStartPosition](#getstartposition).

*key*<br/>
Parámetro de plantilla que especifica el tipo de la clave del mapa.

*value*<br/>
Parámetro de plantilla que especifica el tipo del valor del mapa.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al par actual de elementos de clave y valor almacenados en la asignación.

### <a name="remarks"></a>Observaciones

En las compilaciones de depuración, se producirá un error de aserción si *pos* es igual a NULL.

## <a name="catlmapgetcount"></a><a name="getcount"></a>CAtlMap:: GetCount

Llame a este método para recuperar el número de elementos del mapa.

```cpp
size_t GetCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de elementos del objeto de mapa. Un único elemento es un par clave-valor.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlMap:: CAtlMap](#catlmap).

## <a name="catlmapgethashtablesize"></a><a name="gethashtablesize"></a>CAtlMap:: GetHashTableSize

Llame a este método para determinar el número de depósitos de la tabla hash del mapa.

```cpp
UINT GetHashTableSize() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de ubicaciones de la tabla hash. Vea [CAtlMap:: CAtlMap](#catlmap) para obtener una explicación.

## <a name="catlmapgetkeyat"></a><a name="getkeyat"></a>CAtlMap:: GetKeyAt

Llame a este método para recuperar la clave almacenada en la posición especificada `CAtlMap` en el objeto.

```cpp
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parámetros

*abre*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap:: GetNextAssoc](#getnextassoc) o [CAtlMap:: GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia a la clave almacenada en la posición especificada en `CAtlMap` el objeto.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlMap:: CAtlMap](#catlmap).

## <a name="catlmapgetnext"></a><a name="getnext"></a>CAtlMap:: GetNext

Llame a este método para obtener un puntero al siguiente par de elementos almacenado en `CAtlMap` el objeto.

```cpp
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parámetros

*abre*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap:: GetNextAssoc](#getnextassoc) o [CAtlMap:: GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al siguiente par de elementos de clave y valor almacenados en la asignación. El contador posición de *PDV* se actualiza después de cada llamada. Si el elemento recuperado es el último en el mapa, *pos* se establece en NULL.

## <a name="catlmapgetnextassoc"></a><a name="getnextassoc"></a>CAtlMap:: GetNextAssoc

Obtiene el siguiente elemento para recorrer en iteración.

```cpp
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parámetros

*abre*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap:: GetNextAssoc](#getnextassoc) o [CAtlMap:: GetStartPosition](#getstartposition).

*key*<br/>
Parámetro de plantilla que especifica el tipo de la clave del mapa.

*value*<br/>
Parámetro de plantilla que especifica el tipo del valor del mapa.

### <a name="remarks"></a>Observaciones

El contador posición de *PDV* se actualiza después de cada llamada. Si el elemento recuperado es el último en el mapa, *pos* se establece en NULL.

## <a name="catlmapgetnextkey"></a><a name="getnextkey"></a>CAtlMap:: GetNextKey

Llame a este método para recuperar la clave siguiente del `CAtlMap` objeto.

```cpp
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parámetros

*abre*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap:: GetNextAssoc](#getnextassoc) o [CAtlMap:: GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia a la clave siguiente en el mapa.

### <a name="remarks"></a>Observaciones

Actualiza el contador de posición actual, *pos*. Si no hay más entradas en el mapa, el contador de posición se establece en NULL.

## <a name="catlmapgetnextvalue"></a><a name="getnextvalue"></a>CAtlMap:: GetNextValue

Llame a este método para obtener el siguiente valor del `CAtlMap` objeto.

```cpp
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parámetros

*abre*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap:: GetNextAssoc](#getnextassoc) o [CAtlMap:: GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al siguiente valor del mapa.

### <a name="remarks"></a>Observaciones

Actualiza el contador de posición actual, *pos*. Si no hay más entradas en el mapa, el contador de posición se establece en NULL.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlMap:: CAtlMap](#catlmap).

## <a name="catlmapgetstartposition"></a><a name="getstartposition"></a>CAtlMap:: GetStartPosition

Llame a este método para iniciar una iteración de mapa.

```cpp
POSITION GetStartPosition() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la posición inicial o se devuelve NULL si la asignación está vacía.

### <a name="remarks"></a>Observaciones

Llame a este método para iniciar una iteración de asignación devolviendo un valor de posición que se `GetNextAssoc` puede pasar al método.

> [!NOTE]
> La secuencia de iteración no es predecible

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlMap:: CAtlMap](#catlmap).

## <a name="catlmapgetvalueat"></a><a name="getvalueat"></a>CAtlMap:: GetValueAt

Llame a este método para recuperar el valor almacenado en una posición determinada en `CAtlMap` el objeto.

```cpp
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parámetros

*abre*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap:: GetNextAssoc](#getnextassoc) o [CAtlMap:: GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al valor almacenado en la posición especificada en el `CAtlMap` objeto.

## <a name="catlmapinithashtable"></a><a name="inithashtable"></a>CAtlMap:: InitHashTable

Llame a este método para inicializar la tabla hash.

```cpp
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```

### <a name="parameters"></a>Parámetros

*nBins*<br/>
El número de ubicaciones utilizadas por la tabla hash. Vea [CAtlMap:: CAtlMap](#catlmap) para obtener una explicación.

*bAllocNow*<br/>
Una indicación de marca cuando se debe asignar memoria.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la inicialización se realiza correctamente, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

`InitHashTable`se debe llamar a antes de que los elementos se almacenen en la tabla hash.  Si no se llama a este método explícitamente, se llamará automáticamente la primera vez que se agregue un elemento mediante el recuento de `CAtlMap` bins especificado por el constructor.  De lo contrario, el mapa se inicializará mediante el nuevo recuento de bins especificado por el parámetro *nBins* .

Si el parámetro *bAllocNow* es false, la memoria requerida por la tabla hash no se asignará hasta que se requiera por primera vez. Esto puede ser útil si no está seguro si se va a usar la asignación.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlMap:: CAtlMap](#catlmap).

## <a name="catlmapisempty"></a><a name="isempty"></a>CAtlMap:: IsEmpty

Llame a este método para comprobar si hay un objeto de mapa vacío.

```cpp
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la asignación está vacía; en caso contrario, FALSE.

## <a name="catlmapkinargtype"></a><a name="kinargtype"></a>CAtlMap:: KINARGTYPE

Tipo usado cuando se pasa una clave como argumento de entrada.

```cpp
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="catlmapkoutargtype"></a><a name="koutargtype"></a>CAtlMap:: KOUTARGTYPE

Tipo usado cuando se devuelve una clave como argumento de salida.

```cpp
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="catlmaplookup"></a><a name="lookup"></a>CAtlMap:: Lookup

Llame a este método para buscar claves o valores en el `CAtlMap` objeto.

```cpp
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

La primera forma del método devuelve true si se encuentra la clave; de lo contrario, es false. El segundo y el tercer formulario devuelven un puntero a un [CPair](#cpair_class) que se puede usar como una posición para las llamadas a [CAtlMap:: Getnext](#getnext) , etc.

### <a name="remarks"></a>Observaciones

`Lookup`utiliza un algoritmo hash para encontrar rápidamente el elemento de mapa que contiene una clave que coincide exactamente con el parámetro de clave determinado.

## <a name="catlmapoperator-"></a><a name="operator_at"></a>CAtlMap:: Operator\[\]

Reemplaza o agrega un nuevo elemento a `CAtlMap`.

```cpp
V& operator[](kinargtype key) throw();
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Clave del elemento que se va a agregar o reemplazar.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al valor asociado a la clave especificada.

### <a name="example"></a>Ejemplo

Si la clave ya existe, se reemplaza el elemento. Si la clave no existe, se agrega un nuevo elemento. Vea el ejemplo de [CAtlMap:: CAtlMap](#catlmap).

## <a name="catlmaprehash"></a><a name="rehash"></a>CAtlMap:: rehash

Llame a este método para rehashar el `CAtlMap` objeto.

```cpp
void Rehash(UINT nBins = 0);
```

### <a name="parameters"></a>Parámetros

*nBins*<br/>
Nuevo número de ubicaciones que se van a usar en la tabla hash. Vea [CAtlMap:: CAtlMap](#catlmap) para obtener una explicación.

### <a name="remarks"></a>Observaciones

Si *nBins* es 0, `CAtlMap` calcula un número razonable según el número de elementos de la asignación y la configuración de carga óptima. Normalmente, el proceso de rehash es automático, pero si se ha llamado a [CAtlMap::D isableautorehash](#disableautorehash) , este método realizará el cambio de tamaño necesario.

## <a name="catlmapremoveall"></a><a name="removeall"></a>CAtlMap:: RemoveAll

Llame a este método para quitar todos los elementos `CAtlMap` del objeto.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>Observaciones

Borra el `CAtlMap` objeto y libera la memoria usada para almacenar los elementos.

## <a name="catlmapremoveatpos"></a><a name="removeatpos"></a>CAtlMap:: RemoveAtPos

Llame a este método para quitar el elemento en la posición especificada en `CAtlMap` el objeto.

```cpp
void RemoveAtPos(POSITION pos) throw();
```

### <a name="parameters"></a>Parámetros

*abre*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap:: GetNextAssoc](#getnextassoc) o [CAtlMap:: GetStartPosition](#getstartposition).

### <a name="remarks"></a>Observaciones

Quita el par clave-valor almacenado en la posición especificada. Se libera la memoria usada para almacenar el elemento. La posición a la que hace referencia *pos* deja de ser válida y, mientras que la posición de cualquier otro elemento del mapa sigue siendo válida, no conservan necesariamente el mismo orden.

## <a name="catlmapremovekey"></a><a name="removekey"></a>CAtlMap:: RemoveKey

Llame a este método para quitar un elemento del `CAtlMap` objeto, dada la clave.

```cpp
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Clave correspondiente al par de elementos que se desea quitar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la clave se encuentra y se quita; en caso contrario, FALSE.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlMap:: CAtlMap](#catlmap).

## <a name="catlmapsetat"></a><a name="setat"></a>CAtlMap:: SetAt

Llame a este método para insertar un par de elementos en la asignación.

```cpp
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Valor de clave que se va a `CAtlMap` agregar al objeto.

*value*<br/>
Valor que se va a agregar `CAtlMap` al objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve la posición del par de elementos de clave y valor en `CAtlMap` el objeto.

### <a name="remarks"></a>Observaciones

`SetAt`reemplaza un elemento existente si se encuentra una clave coincidente. Si no se encuentra la clave, se crea un nuevo par clave-valor.

## <a name="catlmapsetoptimalload"></a><a name="setoptimalload"></a>CAtlMap:: SetOptimalLoad

Llame a este método para establecer la carga óptima del `CAtlMap` objeto.

```cpp
void SetOptimalLoad(
    float fOptimalLoad,
    float fLoThreshold,
    float fHiThreshold,
    bool bRehashNow = false);
```

### <a name="parameters"></a>Parámetros

*fOptimalLoad*<br/>
La proporción de carga óptima.

*fLoThreshold*<br/>
Umbral inferior para la proporción de carga.

*fHiThreshold*<br/>
Umbral superior de la proporción de carga.

*bRehashNow*<br/>
Marca que indica si se debe volver a calcular la tabla hash.

### <a name="remarks"></a>Observaciones

Este método vuelve a definir el valor de carga óptimo para `CAtlMap` el objeto. Vea [CAtlMap:: CAtlMap](#catlmap) para obtener una explicación de los distintos parámetros. Si *bRehashNow* es true y el número de elementos está fuera de los valores mínimo y máximo, se vuelve a calcular la tabla hash.

## <a name="catlmapsetvalueat"></a><a name="setvalueat"></a>CAtlMap:: SetValueAt

Llame a este método para cambiar el valor almacenado en una posición determinada en `CAtlMap` el objeto.

```cpp
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```

### <a name="parameters"></a>Parámetros

*abre*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap:: GetNextAssoc](#getnextassoc) o [CAtlMap:: GetStartPosition](#getstartposition).

*value*<br/>
Valor que se va a agregar `CAtlMap` al objeto.

### <a name="remarks"></a>Observaciones

Cambia el elemento de valor almacenado en la posición especificada en `CAtlMap` el objeto.

## <a name="catlmapvinargtype"></a><a name="vinargtype"></a>CAtlMap:: VINARGTYPE

Tipo usado cuando se pasa un valor como argumento de entrada.

```cpp
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="catlmapvoutargtype"></a><a name="voutargtype"></a>CAtlMap:: VOUTARGTYPE

Tipo usado cuando se pasa un valor como argumento de salida.

```cpp
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="catlmapcpairm_key"></a><a name="m_key"></a>CAtlMap:: CPair:: m_key

El miembro de datos que almacena el elemento de clave.

```cpp
const K m_key;
```

### <a name="parameters"></a>Parámetros

*K*<br/>
El tipo de elemento de clave.

## <a name="catlmapcpairm_value"></a><a name="m_value"></a>CAtlMap:: CPair:: m_value

El miembro de datos que almacena el elemento de valor.

```cpp
V  m_value;
```

### <a name="parameters"></a>Parámetros

*V*<br/>
El tipo de elemento de valor.

## <a name="see-also"></a>Consulte también

[Ejemplo de marquesina](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
