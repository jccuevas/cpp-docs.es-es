---
title: Clase CMap
ms.date: 11/04/2016
f1_keywords:
- CMap
- AFXTEMPL/CMap
- AFXTEMPL/CMap::CPair
- AFXTEMPL/CMap::CMap
- AFXTEMPL/CMap::GetCount
- AFXTEMPL/CMap::GetHashTableSize
- AFXTEMPL/CMap::GetNextAssoc
- AFXTEMPL/CMap::GetSize
- AFXTEMPL/CMap::GetStartPosition
- AFXTEMPL/CMap::InitHashTable
- AFXTEMPL/CMap::IsEmpty
- AFXTEMPL/CMap::Lookup
- AFXTEMPL/CMap::PGetFirstAssoc
- AFXTEMPL/CMap::PGetNextAssoc
- AFXTEMPL/CMap::PLookup
- AFXTEMPL/CMap::RemoveAll
- AFXTEMPL/CMap::RemoveKey
- AFXTEMPL/CMap::SetAt
helpviewer_keywords:
- CMap [MFC], CPair
- CMap [MFC], CMap
- CMap [MFC], GetCount
- CMap [MFC], GetHashTableSize
- CMap [MFC], GetNextAssoc
- CMap [MFC], GetSize
- CMap [MFC], GetStartPosition
- CMap [MFC], InitHashTable
- CMap [MFC], IsEmpty
- CMap [MFC], Lookup
- CMap [MFC], PGetFirstAssoc
- CMap [MFC], PGetNextAssoc
- CMap [MFC], PLookup
- CMap [MFC], RemoveAll
- CMap [MFC], RemoveKey
- CMap [MFC], SetAt
ms.assetid: 640a45ab-0993-4def-97ec-42cc78eb10b9
ms.openlocfilehash: 9a3c92a0a8c3d40e4cc3d289cc0221ff7cdb2e11
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370096"
---
# <a name="cmap-class"></a>Clase CMap

Una clase de colección de diccionarios que asigna claves únicas a valores.

## <a name="syntax"></a>Sintaxis

```
template<class KEY, class ARG_KEY, class VALUE, class ARG_VALUE>class CMap : public CObject
```

#### <a name="parameters"></a>Parámetros

*Clave*<br/>
Clase del objeto utilizado como clave del mapa.

*ARG_KEY*<br/>
Tipo de datos utilizado para argumentos *KEY;* por lo general una referencia a *KEY*.

*Valor*<br/>
Clase del objeto almacenado en el mapa.

*ARG_VALUE*<br/>
Tipo de datos utilizado para argumentos *VALUE;* normalmente una referencia a *VALUE*.

## <a name="members"></a>Miembros

### <a name="public-structures"></a>Estructuras públicas

|Nombre|Descripción|
|----------|-----------------|
|[CMap::CPair](#cpair)|Estructura anidada que contiene un valor de clave y el valor del objeto asociado.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMap::CMap](#cmap)|Construye una colección que asigna claves a valores.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMap::GetCount](#getcount)|Devuelve el número de elementos de este mapa.|
|[CMap::GetHashTableSize](#gethashtablesize)|Devuelve el número de elementos de la tabla hash.|
|[CMap::GetNextAssoc](#getnextassoc)|Obtiene el siguiente elemento para iterar.|
|[CMap::GetSize](#getsize)|Devuelve el número de elementos de este mapa.|
|[CMap::GetStartPosition](#getstartposition)|Devuelve la posición del primer elemento.|
|[CMap::InitHashTable](#inithashtable)|Inicializa la tabla hash y especifica su tamaño.|
|[CMap::IsEmpty](#isempty)|Comprueba la condición de mapa vacío (sin elementos).|
|[CMap::Lookup](#lookup)|Busca el valor asignado a una clave determinada.|
|[CMap::PGetFirstAssoc](#pgetfirstassoc)|Devuelve un puntero al primer elemento.|
|[CMap::PGetNextAssoc](#pgetnextassoc)|Obtiene un puntero al siguiente elemento para iterar.|
|[CMap::PLookup](#plookup)|Devuelve un puntero a una clave cuyo valor coincide con el valor especificado.|
|[CMap::RemoveAll](#removeall)|Elimina todos los elementos de este mapa.|
|[CMap::RemoveKey](#removekey)|Quita un elemento especificado por una clave.|
|[CMap::SetAt](#setat)|Inserta un elemento en el mapa; reemplaza un elemento existente si se encuentra una clave coincidente.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMap::operador \[\]](#operator_at)|Inserta un elemento en el mapa `SetAt`— sustitución del operador para .|

## <a name="remarks"></a>Observaciones

Una vez que haya insertado un par clave-valor (elemento) en el mapa, puede recuperar o eliminar el par de forma eficaz utilizando la clave para acceder a él. También puede iterar sobre todos los elementos del mapa.

Se utiliza una variable de tipo POSITION para el acceso alternativo a las entradas. Puede utilizar una POSITION para "recordar" una entrada y recorrer en iteración el mapa. Podría pensar que esta iteración es secuencial por valor de clave; no lo es. La secuencia de elementos recuperados es indeterminada.

Ciertas funciones miembro de esta clase llaman a funciones auxiliares globales que se deben personalizar para la mayoría de los usos de la `CMap` clase. Consulte [Ayudantes de clase de colección](../../mfc/reference/collection-class-helpers.md) en la sección Macros y globales de la **referencia de MFC**.

`CMap`reemplaza [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) para admitir la serialización y el volcado de sus elementos. Si un mapa se almacena `Serialize`en un archivo mediante , cada elemento de mapa se serializa a su vez. La implementación `SerializeElements` predeterminada de la función auxiliar realiza una escritura bit a bit. Para obtener información acerca de la `CObject` serialización de elementos de colección de punteros derivados de u otros tipos definidos por el usuario, vea [Cómo: crear una colección con seguridad](../../mfc/how-to-make-a-type-safe-collection.md)de tipos .

Si necesita un volcado de diagnóstico de los elementos individuales del mapa (las claves y los valores), debe establecer la profundidad del contexto de volcado en 1 o superior.

Cuando `CMap` se elimina un objeto, o cuando se quitan sus elementos, se quitan las claves y los valores.

La derivación de la clase de mapa es similar a la derivación de lista. Consulte el artículo [Colecciones](../../mfc/collections.md) para obtener una ilustración de la derivación de una clase de lista de propósito especial.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CMap`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtempl.h

## <a name="cmapcmap"></a><a name="cmap"></a>CMap::CMap

Construye un mapa vacío.

```
CMap(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parámetros

*nBlockSize*<br/>
Especifica la granularidad de asignación de memoria para extender el mapa.

### <a name="remarks"></a>Observaciones

A medida que el mapa crece, la memoria se asigna en unidades de entradas *nBlockSize.*

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#56](../../mfc/codesnippet/cpp/cmap-class_1.cpp)]

## <a name="cmapcpair"></a><a name="cpair"></a>CMap::CPair

Contiene un valor de clave y el valor del objeto asociado.

### <a name="remarks"></a>Observaciones

Se trata de una estructura anidada dentro de la clase [CMap](../../mfc/reference/cmap-class.md).

La estructura se compone de dos campos:

- `key`El valor real del tipo de clave.

- `value`El valor del objeto asociado.

Se utiliza para almacenar los valores devueltos de [CMap::PLookup](#plookup), [CMap::PGetFirstAssoc](#pgetfirstassoc)y [CMap::PGetNextAssoc](#pgetnextassoc).

### <a name="example"></a>Ejemplo

Para obtener un ejemplo de uso, vea el ejemplo de [CMap::PLookup](#plookup).

## <a name="cmapgetcount"></a><a name="getcount"></a>CMap::GetCount

Recupera el número de elementos del mapa.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CMap::Lookup](#lookup).

## <a name="cmapgethashtablesize"></a><a name="gethashtablesize"></a>CMap::GetHashTableSize

Determina el número de elementos de la tabla hash para el mapa.

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos de la tabla hash.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#57](../../mfc/codesnippet/cpp/cmap-class_2.cpp)]

## <a name="cmapgetnextassoc"></a><a name="getnextassoc"></a>CMap::GetNextAssoc

Recupera el elemento `rNextPosition`de mapa `rNextPosition` en , a continuación, se actualiza para hacer referencia al siguiente elemento del mapa.

```
void GetNextAssoc(
    POSITION& rNextPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>Parámetros

*rNextPosition*<br/>
Especifica una referencia a un valor `GetNextAssoc` POSITION `GetStartPosition` devuelto por una llamada o anterior.

*Clave*<br/>
Parámetro de plantilla que especifica el tipo de clave del mapa.

*rKey*<br/>
Especifica la clave devuelta del elemento recuperado.

*Valor*<br/>
Parámetro de plantilla que especifica el tipo del valor del mapa.

*rValue*<br/>
Especifica el valor devuelto del elemento recuperado.

### <a name="remarks"></a>Observaciones

Esta función es más útil para recorrer en iteración todos los elementos del mapa. Tenga en cuenta que la secuencia de posición no es necesariamente la misma que la secuencia de valores de clave.

Si el elemento recuperado es el último del mapa, el nuevo valor de *rNextPosition* se establece en NULL.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CMap::SetAt](#setat).

## <a name="cmapgetsize"></a><a name="getsize"></a>CMap::GetSize

Devuelve el número de elementos de mapa.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos en el mapa.

### <a name="remarks"></a>Observaciones

Llame a este método para recuperar el número de elementos en el mapa.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

## <a name="cmapgetstartposition"></a><a name="getstartposition"></a>CMap::GetStartPosition

Inicia una iteración de mapa devolviendo `GetNextAssoc` un valor POSITION que se puede pasar a una llamada.

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor POSITION que indica una posición inicial para iterar el mapa; null si el mapa está vacío.

### <a name="remarks"></a>Observaciones

La secuencia de iteración no es predecible; por lo tanto, el "primer elemento en el mapa" no tiene un significado especial.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CMap::SetAt](#setat).

## <a name="cmapinithashtable"></a><a name="inithashtable"></a>CMap::InitHashTable

Inicializa la tabla hash.

```
void InitHashTable(UINT hashSize, BOOL  bAllocNow = TRUE);
```

### <a name="parameters"></a>Parámetros

*hashSize*<br/>
Número de entradas en la tabla hash.

*bAllocNow*<br/>
Si TRUE, asigna la tabla hash tras la inicialización; de lo contrario, la tabla se asigna cuando es necesario.

### <a name="remarks"></a>Observaciones

Para obtener el mejor rendimiento, el tamaño de la tabla hash debe ser un número primo. Para minimizar las colisiones, el tamaño debe ser aproximadamente un 20 por ciento mayor que el conjunto de datos previsto más grande.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CMap::Lookup](#lookup).

## <a name="cmapisempty"></a><a name="isempty"></a>CMap::IsEmpty

Determina si el mapa está vacío.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si este mapa no contiene elementos; de lo contrario 0.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CMap::RemoveAll](#removeall).

## <a name="cmaplookup"></a><a name="lookup"></a>CMap::Lookup

Busca el valor asignado a una clave determinada.

```
BOOL Lookup(ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>Parámetros

*ARG_KEY*<br/>
Parámetro de plantilla que especifica el tipo del valor de *clave.*

*key*<br/>
Especifica la clave que identifica el elemento que se va a buscar.

*Valor*<br/>
Especifica el tipo del valor que se va a buscar.

*rValue*<br/>
Recibe el valor de buscado.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encontró el elemento; de lo contrario 0.

### <a name="remarks"></a>Observaciones

`Lookup`utiliza un algoritmo hash para encontrar rápidamente el elemento de mapa con una clave que coincida exactamente con la clave dada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

## <a name="cmapoperator--"></a><a name="operator_at"></a>CMap::operador [ ]

Un sustituto conveniente `SetAt` para la función miembro.

```
VALUE& operator[](arg_key key);
```

### <a name="parameters"></a>Parámetros

*Valor*<br/>
Parámetro de plantilla que especifica el tipo del valor de mapa.

*ARG_KEY*<br/>
Parámetro de plantilla que especifica el tipo del valor de clave.

*key*<br/>
La clave utilizada para recuperar el valor del mapa.

### <a name="remarks"></a>Observaciones

Por lo tanto, solo se puede utilizar en el lado izquierdo de una instrucción de asignación (un valor l). Si no hay ningún elemento de mapa con la clave especificada, se crea un nuevo elemento.

No hay ningún "lado derecho" (valor r) equivalente a este operador porque existe la posibilidad de que no se encuentre una clave en el mapa. Utilice `Lookup` la función miembro para la recuperación de elementos.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CMap::Lookup](#lookup).

## <a name="cmappgetfirstassoc"></a><a name="pgetfirstassoc"></a>CMap::PGetFirstAssoc

Devuelve la primera entrada del objeto de mapa.

```
const CPair* PGetFirstAssoc() const;
CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la primera entrada del mapa; ver [CMap::CPair](#cpair). Si el mapa no contiene ninguna entrada, el valor es NULL.

### <a name="remarks"></a>Observaciones

Llame a esta función para devolver un puntero el primer elemento en el objeto de mapa.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#59](../../mfc/codesnippet/cpp/cmap-class_4.cpp)]

## <a name="cmappgetnextassoc"></a><a name="pgetnextassoc"></a>CMap::PGetNextAssoc

Recupera el elemento de mapa al que apunta *pAssocRec*.

```
const CPair *PGetNextAssoc(const CPair* pAssocRet) const;

CPair *PGetNextAssoc(const CPair* pAssocRet);
```

### <a name="parameters"></a>Parámetros

*pAssocRet*<br/>
Apunta a una entrada de mapa devuelta por una llamada [PGetNextAssoc](#pgetnextassoc) o [CMap::PGetFirstAssoc](#pgetfirstassoc) anterior.

### <a name="return-value"></a>Valor devuelto

Un puntero a la siguiente entrada en el mapa; ver [CMap::CPair](#cpair). Si el elemento es el último del mapa, el valor es NULL.

### <a name="remarks"></a>Observaciones

Llame a este método para recorrer en iteración todos los elementos del mapa. Recupere el primer elemento `PGetFirstAssoc` con una llamada y, a `PGetNextAssoc`continuación, iterar a través del mapa con llamadas sucesivas a .

### <a name="example"></a>Ejemplo

Vea el ejemplo [de CMap::PGetFirstAssoc](#pgetfirstassoc).

## <a name="cmapplookup"></a><a name="plookup"></a>CMap::PLookup

Busca el valor asignado a una clave determinada.

```
const CPair* PLookup(ARG_KEY key) const;
CPair* PLookup(ARG_KEY key);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Clave para el elemento que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Un puntero a una estructura de clave; ver [CMap::CPair](#cpair). Si no se `CMap::PLookup` encuentra ninguna coincidencia, devuelve NULL.

### <a name="remarks"></a>Observaciones

Llame a este método para buscar un elemento de mapa con una clave que coincida exactamente con la clave dada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#60](../../mfc/codesnippet/cpp/cmap-class_5.cpp)]

## <a name="cmapremoveall"></a><a name="removeall"></a>CMap::RemoveAll

Quita todos los valores de este mapa `DestructElements`llamando a la función auxiliar global .

```
void RemoveAll();
```

### <a name="remarks"></a>Observaciones

La función funciona correctamente si el mapa ya está vacío.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#61](../../mfc/codesnippet/cpp/cmap-class_6.cpp)]

## <a name="cmapremovekey"></a><a name="removekey"></a>CMap::RemoveKey

Busca la entrada de mapa correspondiente a la clave suministrada; entonces, si se encuentra la clave, quita la entrada.

```
BOOL RemoveKey(ARG_KEY key);
```

### <a name="parameters"></a>Parámetros

*ARG_KEY*<br/>
Parámetro de plantilla que especifica el tipo de la clave.

*key*<br/>
Clave para el elemento que se va a quitar.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la entrada se encontró y se quitó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La `DestructElements` función auxiliar se utiliza para quitar la entrada.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CMap::SetAt](#setat).

## <a name="cmapsetat"></a><a name="setat"></a>CMap::SetAt

El principal significa insertar un elemento en un mapa.

```
void SetAt(ARG_KEY key, ARG_VALUE newValue);
```

### <a name="parameters"></a>Parámetros

*ARG_KEY*<br/>
Parámetro de plantilla que especifica el tipo del parámetro *key.*

*key*<br/>
Especifica la clave del nuevo elemento.

*ARG_VALUE*<br/>
Parámetro de plantilla que especifica el tipo del parámetro *newValue.*

*newValue*<br/>
Especifica el valor del nuevo elemento.

### <a name="remarks"></a>Observaciones

Primero, la llave se mira hacia arriba. Si se encuentra la clave, se cambia el valor correspondiente; de lo contrario se crea un nuevo par clave-valor.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#62](../../mfc/codesnippet/cpp/cmap-class_7.cpp)]

## <a name="see-also"></a>Consulte también

[RECOPILACIÓN de muestras de MFC](../../overview/visual-cpp-samples.md)<br/>
[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
