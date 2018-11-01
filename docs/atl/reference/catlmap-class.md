---
title: CAtlMap (clase)
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
ms.openlocfilehash: 83ac810538bf189d026c0cb9b2a76ded49fdd86c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499695"
---
# <a name="catlmap-class"></a>CAtlMap (clase)

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
|[CAtlMap::KINARGTYPE](#kinargtype)|Tipo que se utiliza cuando se pasa una clave como un argumento de entrada|
|[CAtlMap::KOUTARGTYPE](#koutargtype)|Tipo que se usa cuando una clave se devuelve como un argumento de salida.|
|[CAtlMap::VINARGTYPE](#vinargtype)|Tipo que se utiliza cuando se pasa un valor como argumento de entrada.|
|[CAtlMap::VOUTARGTYPE](#voutargtype)|Tipo que se utiliza cuando se pasa un valor como un argumento de salida.|

### <a name="public-classes"></a>Clases públicas

|Name|Descripción|
|----------|-----------------|
|[Clase CAtlMap::CPair](#cpair_class)|Una clase que contiene los elementos clave y valor.|

### <a name="cpair-data-members"></a>Miembros de datos CPair

|nombre|Descripción|
|----------|-----------------|
|[CPair::m_key](#m_key)|Almacenar el elemento clave de miembro de datos.|
|[CPair::m_value](#m_value)|El miembro de datos almacenar el elemento de valor.|

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CAtlMap::CAtlMap](#catlmap)|El constructor.|
|[CAtlMap:: ~ CAtlMap](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CAtlMap::AssertValid](#assertvalid)|Llame a este método para hacer que una aserción si el `CAtlMap` no es válido.|
|[CAtlMap::DisableAutoRehash](#disableautorehash)|Llame a este método para deshabilitar recombinando automática de la `CAtlMap` objeto.|
|[CAtlMap::EnableAutoRehash](#enableautorehash)|Llame a este método para habilitar recombinando automática de la `CAtlMap` objeto.|
|[CAtlMap::GetAt](#getat)|Llame a este método para devolver el elemento en una posición especificada en el mapa.|
|[CAtlMap::GetCount](#getcount)|Llame a este método para recuperar el número de elementos del mapa.|
|[CAtlMap::GetHashTableSize](#gethashtablesize)|Llame a este método para determinar el número de ubicaciones en la tabla de hash del mapa.|
|[CAtlMap::GetKeyAt](#getkeyat)|Llame a este método para recuperar la clave almacenada en la posición especificada en el `CAtlMap` objeto.|
|[CAtlMap::GetNext](#getnext)|Llame a este método para obtener un puntero al siguiente elemento par almacena en la `CAtlMap` objeto.|
|[CAtlMap::GetNextAssoc](#getnextassoc)|Obtiene el elemento siguiente para efectuar una iteración.|
|[CAtlMap::GetNextKey](#getnextkey)|Llame a este método para recuperar la clave siguiente desde el `CAtlMap` objeto.|
|[CAtlMap::GetNextValue](#getnextvalue)|Llame a este método para obtener el siguiente valor de la `CAtlMap` objeto.|
|[CAtlMap::GetStartPosition](#getstartposition)|Llame a este método para iniciar una iteración de mapa.|
|[CAtlMap::GetValueAt](#getvalueat)|Llame a este método para recuperar el valor almacenado en una posición determinada en el `CAtlMap` objeto.|
|[CAtlMap::InitHashTable](#inithashtable)|Llame a este método para inicializar la tabla hash.|
|[CAtlMap::IsEmpty](#isempty)|Llame a este método para probar un objeto de asignación vacía.|
|[CAtlMap::Lookup](#lookup)|Llame a este método para buscar las claves o valores de la `CAtlMap` objeto.|
|[CAtlMap::Rehash](#rehash)|Llame a este método para recombinar los `CAtlMap` objeto.|
|[CAtlMap::RemoveAll](#removeall)|Llame a este método para quitar todos los elementos de la `CAtlMap` objeto.|
|[CAtlMap::RemoveAtPos](#removeatpos)|Llame a este método para quitar el elemento en la posición especificada en el `CAtlMap` objeto.|
|[CAtlMap::RemoveKey](#removekey)|Llame a este método para quitar un elemento de la `CAtlMap` objeto, dada la clave.|
|[CAtlMap::SetAt](#setat)|Llame a este método para insertar un par de elementos en el mapa.|
|[CAtlMap::SetOptimalLoad](#setoptimalload)|Llame a este método para establecer la carga óptima de la `CAtlMap` objeto.|
|[CAtlMap::SetValueAt](#setvalueat)|Llame a este método para cambiar el valor almacenado en una posición determinada en el `CAtlMap` objeto.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CAtlMap::operator\[\]](catlmap-class.md#operator_at)|Reemplaza o agrega un nuevo elemento a la `CAtlMap`.|

## <a name="remarks"></a>Comentarios

`CAtlMap` proporciona compatibilidad para una matriz de asignación de un tipo dado, administración de una matriz no ordenada de elementos clave y sus valores asociados. Elementos (que consta de una clave y un valor) se almacenan mediante un algoritmo hash, lo que permite una gran cantidad de datos se almacenan y recuperar eficazmente.

El *KTraits* y *VTraits* parámetros son las clases de rasgos que contienen cualquier código complementario necesario para copiar o mover elementos.

Una alternativa a `CAtlMap` ofrecida por la [CRBMap](../../atl/reference/crbmap-class.md) clase. `CRBMap` también almacena los pares clave/valor, pero presenta las características de rendimiento diferente. El tiempo necesario para insertar un elemento, buscar una clave o eliminar una clave de un `CRBMap` es objeto de pedido *log(n)*, donde *n* es el número de elementos. Para `CAtlMap`, todas estas operaciones suele tardan tiempo constante, aunque podrían ser peores escenarios de orden *n*. Por lo tanto, en un caso típico, `CAtlMap` es más rápido.

La otra diferencia entre `CRBMap` y `CAtlMap` se hace evidente cuando se recorre en iteración los elementos almacenados. En un `CRBMap`, los elementos se visitan de forma ordenada. En un `CAtlMap`, no se ordenan los elementos y no se puede inferir ningún orden.

Cuando un número pequeño de elementos debe almacenarse, considere el uso de la [CSimpleMap](../../atl/reference/csimplemap-class.md) clase en su lugar.

Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

##  <a name="assertvalid"></a>  CAtlMap::AssertValid

Llame a este método para hacer que una aserción si el `CAtlMap` objeto no es válido.

```
void AssertValid() const;
```

### <a name="remarks"></a>Comentarios

En las compilaciones de depuración, este método producirá una aserción si el `CAtlMap` objeto no es válido.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlMap::CAtlMap](#catlmap).

##  <a name="catlmap"></a>  CAtlMap::CAtlMap

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
El número de ubicaciones que proporciona punteros a los elementos almacenados. Vea la sección Comentarios más adelante en este tema para obtener una explicación de las ubicaciones.

*fOptimalLoad*<br/>
La proporción de carga óptima.

*fLoThreshold*<br/>
El umbral inferior de la relación de carga.

*fHiThreshold*<br/>
El umbral superior de la relación de carga.

*nBlockSize*<br/>
El tamaño de bloque.

### <a name="remarks"></a>Comentarios

`CAtlMap` hace referencia a todos sus elementos almacenados creando primero un índice mediante un algoritmo hash en la clave. Este índice hace referencia a un "bin" que contiene un puntero a los elementos almacenados. Si la Papelera ya está en uso, se crea una lista vinculada para tener acceso a los elementos subsiguientes. Recorrer una lista es más lento que el acceso directo al elemento correcto y, por tanto, la estructura del mapa debe equilibrar los requisitos de almacenamiento con respecto al rendimiento. Los parámetros predeterminados han sido seleccionados para brindar buenos resultados en la mayoría de los casos.

La proporción de carga es la proporción del número de cubos para el número de elementos almacenados en el objeto de mapa. Cuando se vuelve a calcular la estructura del mapa, el *fOptimalLoad* el valor del parámetro que se usará para calcular el número de ubicaciones necesarias. Este valor se puede cambiar mediante la [CAtlMap::SetOptimalLoad](#setoptimalload) método.

El *fLoThreshold* parámetro es el valor más bajo que la proporción de carga puede alcanzar antes `CAtlMap` se volverá a calcular el tamaño óptimo del mapa.

El *fHiThreshold* parámetro es el valor más alto que la proporción de carga puede alcanzar antes el `CAtlMap` objeto volverá a calcular el tamaño óptimo del mapa.

Este proceso de recálculo (conocido como recombinando) está habilitado de forma predeterminada. Si desea deshabilitar este proceso, quizás al escribir una gran cantidad de datos al mismo tiempo, llamada la [CAtlMap::DisableAutoRehash](#disableautorehash) método. Volver a activarla con la [CAtlMap::EnableAutoRehash](#enableautorehash) método.

El *nBlockSize* parámetro es una medida de la cantidad de memoria asignada cuando se requiere un nuevo elemento. Mayor tamaño de bloque reduce las llamadas a rutinas de asignación de memoria, pero usa más recursos.

Antes de que se pueden almacenar los datos, es necesario inicializar la tabla hash con una llamada a [CAtlMap::InitHashTable](#inithashtable).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]

##  <a name="dtor"></a>  CAtlMap:: ~ CAtlMap

Destructor.

```
~CAtlMap() throw();
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados.

##  <a name="cpair_class"></a>  Clase CAtlMap::CPair

Una clase que contiene los elementos clave y valor.

```
class CPair : public __POSITION
```

### <a name="remarks"></a>Comentarios

Esta clase se utiliza los métodos [CAtlMap::GetNext](#getnext) y [CAtlMap::Lookup](#lookup) para tener acceso a los elementos clave y el valor almacenados en la estructura de asignación.

##  <a name="disableautorehash"></a>  CAtlMap::DisableAutoRehash

Llame a este método para deshabilitar recombinando automática de la `CAtlMap` objeto.

```
void DisableAutoRehash() throw();
```

### <a name="remarks"></a>Comentarios

Cuando vuelve automática está habilitada (que es de forma predeterminada), el número de ubicaciones en la tabla hash se recalculará automáticamente si el valor de carga (la proporción del número de cubos para el número de elementos almacenados en la matriz) supera los valores máximo o mínimos se especificó en el momento en que se creó la asignación.

`DisableAutoRehash` es muy útil cuando un gran número de elementos se agregarán a la asignación a la vez. En lugar de desencadenar el proceso rehashing cada vez que se superan los límites, es más eficaz llamar a `DisableAutoRehash`, agregue los elementos y, por último, llame a [CAtlMap::EnableAutoRehash](#enableautorehash).

##  <a name="enableautorehash"></a>  CAtlMap::EnableAutoRehash

Llame a este método para habilitar recombinando automática de la `CAtlMap` objeto.

```
void EnableAutoRehash() throw();
```

### <a name="remarks"></a>Comentarios

Cuando vuelve automática está habilitada (que es de forma predeterminada), el número de ubicaciones en la tabla hash se recalculará automáticamente si el valor de carga (la proporción del número de cubos para el número de elementos almacenados en la matriz) supera los valores máximo o mínimos se especificó en el momento en que se crea la asignación.

`EnableAutoRefresh` se suele utilizar después de llamar a [CAtlMap::DisableAutoRehash](#disableautorehash).

##  <a name="getat"></a>  CAtlMap::GetAt

Llame a este método para devolver el elemento en una posición especificada en el mapa.

```
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```

### <a name="parameters"></a>Parámetros

*punto de venta*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).

*key*<br/>
Parámetro de plantilla que especifica el tipo de clave del mapa.

*valor*<br/>
Especifica el tipo del valor de la asignación de un parámetro de plantilla.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero para el par de elementos de clave/valor almacenados en el mapa actual.

### <a name="remarks"></a>Comentarios

En las compilaciones de depuración, se producirá un error de aserción si *pos* es igual a NULL.

##  <a name="getcount"></a>  CAtlMap::GetCount

Llame a este método para recuperar el número de elementos del mapa.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de elementos en el objeto de mapa. Un único elemento es un par clave/valor.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlMap::CAtlMap](#catlmap).

##  <a name="gethashtablesize"></a>  CAtlMap::GetHashTableSize

Llame a este método para determinar el número de ubicaciones en la tabla de hash del mapa.

```
UINT GetHashTableSize() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de ubicaciones en la tabla hash. Consulte [CAtlMap::CAtlMap](#catlmap) para obtener una explicación.

##  <a name="getkeyat"></a>  CAtlMap::GetKeyAt

Llame a este método para recuperar la clave almacenada en la posición especificada en el `CAtlMap` objeto.

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parámetros

*punto de venta*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia a la clave almacenada en la posición especificada en el `CAtlMap` objeto.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlMap::CAtlMap](#catlmap).

##  <a name="getnext"></a>  CAtlMap::GetNext

Llame a este método para obtener un puntero al siguiente elemento par almacena en la `CAtlMap` objeto.

```
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parámetros

*punto de venta*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al siguiente par de elementos de clave/valor almacenados en el mapa. El *pos* contador de posición se actualiza después de cada llamada. Si el elemento recuperado es el último en el mapa, *pos* se establece en NULL.

##  <a name="getnextassoc"></a>  CAtlMap::GetNextAssoc

Obtiene el elemento siguiente para efectuar una iteración.

```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parámetros

*punto de venta*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).

*key*<br/>
Parámetro de plantilla que especifica el tipo de clave del mapa.

*valor*<br/>
Especifica el tipo del valor de la asignación de un parámetro de plantilla.

### <a name="remarks"></a>Comentarios

El *pos* contador de posición se actualiza después de cada llamada. Si el elemento recuperado es el último en el mapa, *pos* se establece en NULL.

##  <a name="getnextkey"></a>  CAtlMap::GetNextKey

Llame a este método para recuperar la clave siguiente desde el `CAtlMap` objeto.

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parámetros

*punto de venta*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia a la siguiente clave en el mapa.

### <a name="remarks"></a>Comentarios

Actualiza el contador actual de posición, *pos*. Si no hay ningún más entradas en el mapa, el contador de posición se establece en NULL.

##  <a name="getnextvalue"></a>  CAtlMap::GetNextValue

Llame a este método para obtener el siguiente valor de la `CAtlMap` objeto.

```
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parámetros

*punto de venta*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al siguiente valor en el mapa.

### <a name="remarks"></a>Comentarios

Actualiza el contador actual de posición, *pos*. Si no hay ningún más entradas en el mapa, el contador de posición se establece en NULL.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlMap::CAtlMap](#catlmap).

##  <a name="getstartposition"></a>  CAtlMap::GetStartPosition

Llame a este método para iniciar una iteración de mapa.

```
POSITION GetStartPosition() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve que la posición inicial, o NULL se devuelve si el mapa está vacío.

### <a name="remarks"></a>Comentarios

Llamada a este método para iniciar una iteración de mapa devolviendo una posición de valor que se puede pasar a la `GetNextAssoc` método.

> [!NOTE]
>  La secuencia de iteración no es de predicción

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlMap::CAtlMap](#catlmap).

##  <a name="getvalueat"></a>  CAtlMap::GetValueAt

Llame a este método para recuperar el valor almacenado en una posición determinada en el `CAtlMap` objeto.

```
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parámetros

*punto de venta*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al valor almacenado en la posición especificada en el `CAtlMap` objeto.

##  <a name="inithashtable"></a>  CAtlMap::InitHashTable

Llame a este método para inicializar la tabla hash.

```
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```

### <a name="parameters"></a>Parámetros

*nBins*<br/>
El número de ubicaciones usado por la tabla hash. Consulte [CAtlMap::CAtlMap](#catlmap) para obtener una explicación.

*bAllocNow*<br/>
Una indicación del indicador cuando se debe asignar memoria.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en la inicialización correcta, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

`InitHashTable` debe llamarse antes de que todos los elementos se almacenan en la tabla hash.  Si no se llama explícitamente a este método, se llamará automáticamente la primera vez que se agrega un elemento con el recuento de discretización especificado por el `CAtlMap` constructor.  En caso contrario, el mapa se inicializará mediante el nuevo recuento de discretización especificado por el *nBins* parámetro.

Si el *bAllocNow* parámetro es false, la memoria requerida por la tabla hash no se asignarán hasta que el primero es necesario. Esto puede ser útil si está seguro de que se usará el mapa.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlMap::CAtlMap](#catlmap).

##  <a name="isempty"></a>  CAtlMap::IsEmpty

Llame a este método para probar un objeto de asignación vacía.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el mapa está vacío, FALSE en caso contrario.

##  <a name="kinargtype"></a>  CAtlMap::KINARGTYPE

Tipo que se utiliza cuando se pasa una clave como un argumento de entrada.

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

##  <a name="koutargtype"></a>  CAtlMap::KOUTARGTYPE

Tipo que se usa cuando una clave se devuelve como un argumento de salida.

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

##  <a name="lookup"></a>  CAtlMap::Lookup

Llame a este método para buscar las claves o valores de la `CAtlMap` objeto.

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Especifica la clave que identifica el elemento que se va a buscar.

*valor*<br/>
Variable que recibe el valor buscado.

### <a name="return-value"></a>Valor devuelto

El primer formulario del método devuelve true si se encuentra la clave, en caso contrario, false. Los formularios de la segundo y terceros devuelven un puntero a un [CPair](#cpair_class) que puede utilizarse como una posición para las llamadas a [CAtlMap::GetNext](#getnext) y así sucesivamente.

### <a name="remarks"></a>Comentarios

`Lookup` utiliza un algoritmo hash para encontrar rápidamente el elemento de mapa que contiene una clave que coincida exactamente con el parámetro de clave especificado.

##  <a name="operator_at"></a>  CAtlMap::operator \[\]

Reemplaza o agrega un nuevo elemento a la `CAtlMap`.

```
V& operator[](kinargtype key) throw();
```

### <a name="parameters"></a>Parámetros

*key*<br/>
La clave del elemento para agregar o reemplazar.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia para el valor asociado con la clave especificada.

### <a name="example"></a>Ejemplo

Si la clave ya existe, se reemplaza el elemento. Si la clave no existe, se agrega un nuevo elemento. Vea el ejemplo de [CAtlMap::CAtlMap](#catlmap).

##  <a name="rehash"></a>  CAtlMap::Rehash

Llame a este método para recombinar los `CAtlMap` objeto.

```
void Rehash(UINT nBins = 0);
```

### <a name="parameters"></a>Parámetros

*nBins*<br/>
El nuevo número de cubos para usar en la tabla hash. Consulte [CAtlMap::CAtlMap](#catlmap) para obtener una explicación.

### <a name="remarks"></a>Comentarios

Si *nBins* es 0, `CAtlMap` calcula un número razonable en función del número de elementos del mapa y la configuración de carga óptima. Normalmente el proceso rehashing es automático, pero si [CAtlMap::DisableAutoRehash](#disableautorehash) ha sido llama, este método llevará a cabo el cambio de tamaño necesario.

##  <a name="removeall"></a>  CAtlMap::RemoveAll

Llame a este método para quitar todos los elementos de la `CAtlMap` objeto.

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Comentarios

Borra la `CAtlMap` objeto, libere la memoria utilizada para almacenar los elementos.

##  <a name="removeatpos"></a>  CAtlMap::RemoveAtPos

Llame a este método para quitar el elemento en la posición especificada en el `CAtlMap` objeto.

```
void RemoveAtPos(POSITION pos) throw();
```

### <a name="parameters"></a>Parámetros

*punto de venta*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).

### <a name="remarks"></a>Comentarios

Quita el par clave/valor almacenado en la posición especificada. Se libera la memoria usada para almacenar el elemento. La posición hace referencia a *pos* deja de ser válida y, mientras que la posición de cualquier otro elemento en el mapa sigue siendo válida, no necesariamente lo hacen, conservar el mismo orden.

##  <a name="removekey"></a>  CAtlMap::RemoveKey

Llame a este método para quitar un elemento de la `CAtlMap` objeto, dada la clave.

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parámetros

*key*<br/>
La clave correspondiente a la par de elementos que desea quitar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la clave se encuentra y quita, FALSE en caso de error.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlMap::CAtlMap](#catlmap).

##  <a name="setat"></a>  CAtlMap::SetAt

Llame a este método para insertar un par de elementos en el mapa.

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
El valor de clave para agregar a la `CAtlMap` objeto.

*valor*<br/>
Valor que se agrega a la `CAtlMap` objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve la posición del par clave-valor elemento en el `CAtlMap` objeto.

### <a name="remarks"></a>Comentarios

`SetAt` reemplaza un elemento existente si se encuentra una clave coincidente. Si no se encuentra la clave, se crea un nuevo par clave-valor.

##  <a name="setoptimalload"></a>  CAtlMap::SetOptimalLoad

Llame a este método para establecer la carga óptima de la `CAtlMap` objeto.

```
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
El umbral inferior de la relación de carga.

*fHiThreshold*<br/>
El umbral superior de la relación de carga.

*bRehashNow*<br/>
Marca que indica si se debe volver a calcular la tabla hash.

### <a name="remarks"></a>Comentarios

Este método vuelve a definir el valor óptimo de carga para el `CAtlMap` objeto. Consulte [CAtlMap::CAtlMap](#catlmap) para obtener una explicación de los distintos parámetros. Si *bRehashNow* es true y el número de elementos está fuera de los valores mínimo y máximos, se vuelve a calcular la tabla hash.

##  <a name="setvalueat"></a>  CAtlMap::SetValueAt

Llame a este método para cambiar el valor almacenado en una posición determinada en el `CAtlMap` objeto.

```
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```

### <a name="parameters"></a>Parámetros

*punto de venta*<br/>
El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).

*valor*<br/>
Valor que se agrega a la `CAtlMap` objeto.

### <a name="remarks"></a>Comentarios

Cambia el elemento de valor almacenado en la posición especificada en el `CAtlMap` objeto.

##  <a name="vinargtype"></a>  CAtlMap::VINARGTYPE

Tipo que se utiliza cuando se pasa un valor como argumento de entrada.

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

##  <a name="voutargtype"></a>  CAtlMap::VOUTARGTYPE

Tipo que se utiliza cuando se pasa un valor como un argumento de salida.

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

##  <a name="m_key"></a>  CAtlMap::CPair::m_key

Almacenar el elemento clave de miembro de datos.

```
const K m_key;
```

### <a name="parameters"></a>Parámetros

*K*<br/>
El tipo de elemento de clave.

##  <a name="m_value"></a>  CAtlMap::CPair::m_value

El miembro de datos almacenar el elemento de valor.

```
V  m_value;
```

### <a name="parameters"></a>Parámetros

*V*<br/>
El tipo de elemento de valor.

## <a name="see-also"></a>Vea también

[Ejemplo de marquesina](../../visual-cpp-samples.md)<br/>
[Ejemplo UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
