---
title: Extent (clase) (C++ AMP) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- extent
- AMP/extent
- AMP/Concurrency::extent::extent
- AMP/Concurrency::extent::contains
- AMP/Concurrency::extent::size
- AMP/Concurrency::extent::tile
- AMP/Concurrency::extent::rank Constant
dev_langs:
- C++
helpviewer_keywords:
- extent structure
ms.assetid: edb5de3d-3935-4dbb-8365-4cc6c4fb0269
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71a02b89e7b2098f8a125d1477cff2a0d1cda30a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429973"
---
# <a name="extent-class-c-amp"></a>extent (Clase) (C++ AMP)

Representa un vector de *N* valores enteros que especifican los límites de un *N*-espacio de dimensiones que tiene un origen de 0. Los valores del vector se ordenan del más significativo al menos significativo.

### <a name="syntax"></a>Sintaxis

```
template <int _Rank>
class extent;
```

### <a name="parameters"></a>Parámetros

*_Rank*<br/>
El rango de la `extent` objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** amp.h

**Espacio de nombres:** Concurrency

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[Constructor de extensión](#ctor)|Inicializa una nueva instancia de la clase `extent`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[Contiene](#contains)|Comprueba que el especificado `extent` objeto tiene el rango especificado.|
|[size](#size)|Devuelve el tamaño lineal total de la extensión (en unidades de elementos).|
|[icono](#tile)|Genera un `tiled_extent` objeto con extensiones de mosaico proporcionadas por las dimensiones especificadas.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[operator-](#operator_min)|Devuelve un nuevo `extent` objeto creado al restar la `index` elementos de las correspondientes `extent` elementos.|
|[operator--](#operator_min_min)|Disminuye cada elemento de la `extent` objeto.|
|[operator%=](#operator_mod_eq)|Calcula el módulo (resto) de cada elemento en el `extent` cuando dicho elemento se divide por un número de objetos.|
|[operator*=](#operator_star_eq)|Multiplica cada elemento de la `extent` objeto según un número.|
|[operator/=](#operator_min_eq)|Divide cada elemento de la `extent` objeto según un número.|
|[Extent:: operator\[\]](#operator_at)|Devuelve el elemento que se encuentra en el índice especificado.|
|[operator+](#operator_add)|Devuelve un nuevo `extent` objeto que se crea al agregar los correspondientes `index` y `extent` elementos.|
|[operator++](#operator_add_add)|Incrementa cada elemento de la `extent` objeto.|
|[operator+=](#operator_add_eq)|Agrega el número especificado a cada elemento de la `extent` objeto.|
|[operator=](#operator_eq)|Copia el contenido de otro `extent` objeto en este.|
|[operator-=](#operator_min_eq)|Resta el número especificado de cada elemento de la `extent` objeto.|

### <a name="public-constants"></a>Constantes públicas

|nombre|Descripción|
|----------|-----------------|
|[Rank (constante)](#rank)|Obtiene el rango de la `extent` objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`extent`

## <a name="contains"></a> Contiene

Indica si el texto especificado [índice](index-class.md) valor está dentro del objeto 'extensión'.

### <a name="syntax"></a>Sintaxis

```
bool contains(const index<rank>& _Index) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
El `index` valor para la prueba.

### <a name="return-value"></a>Valor devuelto

`true` Si el texto especificado `index` valor está incluido en el `extent` objeto; en caso contrario, `false`.

##  <a name="ctor"></a> extensión

Inicializa una nueva instancia de la clase 'extensión'.

### <a name="syntax"></a>Sintaxis

```
extent() restrict(amp,cpu);
extent(const extent<_Rank>& _Other) restrict(amp,cpu);
explicit extent(int _I) restrict(amp,cpu);
extent(int _I0,  int _I1) restrict(amp,cpu);
extent(int _I0,  int _I1, int _I2) restrict(amp,cpu);
explicit extent(const int _Array[_Rank])restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Array*<br/>
Una matriz de `_Rank` enteros que se usa para crear el nuevo `extent` objeto.

*_I*<br/>
La longitud de la extensión.

*_I0*<br/>
La longitud de la dimensión más significativa.

*_I1*<br/>
La longitud de la dimensión para la mayoría-significativo.

*_I2*<br/>
La longitud de la dimensión menos significativa.

*_Otro*<br/>
Un `extent` objeto en el que el nuevo `extent` se basa el objeto.

## <a name="remarks"></a>Comentarios

El constructor sin parámetros inicializa un `extent` objeto que tiene un rango de tres.

Si una matriz se usa para construir un `extent` objeto, la longitud de la matriz debe coincidir con el rango de la `extent` objeto.

##  <a name="operator_mod_eq"></a> operator % =

Calcula el módulo (resto) de cada elemento de la extensión' ' cuando este elemento se divide por un número.

### <a name="syntax"></a>Sintaxis

```
extent<_Rank>& operator%=(int _Rhs) restrict(cpu, direct3d);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
El número para encontrar el módulo de.

### <a name="return-value"></a>Valor devuelto

Objeto `extent`.

##  <a name="operator_star_eq"></a> operador * =

Multiplica cada elemento en el objeto 'alcance' por el número especificado.

### <a name="syntax"></a>Sintaxis

```
extent<_Rank>& operator*=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
El número que se va a multiplicar.

### <a name="return-value"></a>Valor devuelto

Objeto `extent`.

## <a name="operator_add"></a> operator +

Devuelve un nuevo `extent` objeto creado mediante la adición de la correspondiente `index` y `extent` elementos.

### <a name="syntax"></a>Sintaxis

```
extent<_Rank> operator+(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
La `index` objeto que contiene los elementos que se va a agregar.

### <a name="return-value"></a>Valor devuelto

El nuevo objeto `extent`.

##  <a name="operator_add_add"></a> operator ++

Incrementa cada elemento del objeto 'extensión'.

### <a name="syntax"></a>Sintaxis

```
extent<_Rank>& operator++() restrict(amp,cpu);
extent<_Rank> operator++(int)restrict(amp,cpu);
```

### <a name="return-value"></a>Valor devuelto

Para el operador de prefijo, el `extent` objeto (`*this`). Para el operador sufijo, un nuevo `extent` objeto.

##  <a name="operator_add_eq"></a> operator +=

Agrega el número especificado a cada elemento del objeto 'extensión'.

### <a name="syntax"></a>Sintaxis

```
extent<_Rank>& operator+=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
El número, índice o extensión para agregar.

### <a name="return-value"></a>Valor devuelto

El objeto `extent` resultante.

##  <a name="operator_min"></a> operator-

Crea un nuevo `extent` objeto restando cada elemento en la instancia especificada `index` objeto desde el elemento correspondiente de este `extent` objeto.

### <a name="syntax"></a>Sintaxis

```
extent<_Rank> operator-(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
La `index` objeto que contiene los elementos que se va a restar.

### <a name="return-value"></a>Valor devuelto

El nuevo objeto `extent`.

##  <a name="operator_min_min"></a> operator--

Disminuye cada elemento en el objeto 'extensión'.

### <a name="syntax"></a>Sintaxis

```
extent<_Rank>& operator--() restrict(amp,cpu);
extent<_Rank> operator--(int)restrict(amp,cpu);
```

### <a name="return-value"></a>Valor devuelto

Para el operador de prefijo, el `extent` objeto (`*this`). Para el operador sufijo, un nuevo `extent` objeto.

##  <a name="operator_div_eq"></a> operador / =

Divide cada elemento en el objeto 'alcance' por el número especificado.

### <a name="syntax"></a>Sintaxis

```
extent<_Rank>& operator/=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
Dividir por el número.

### <a name="return-value"></a>Valor devuelto

Objeto `extent`.

##  <a name="operator_min_eq"></a> operador =

Resta el número especificado de cada elemento del objeto 'extensión'.

### <a name="syntax"></a>Sintaxis

```
extent<_Rank>& operator-=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
El número que se va a restar.

### <a name="return-value"></a>Valor devuelto

El objeto `extent` resultante.

##  <a name="operator_eq"></a> operator=

Copia el contenido de otro objeto de 'alcance' en este.

### <a name="syntax"></a>Sintaxis

```
extent<_Rank>& operator=(const extent<_Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Otro*<br/>
La `extent` objeto que se va a copiar desde.

### <a name="return-value"></a>Valor devuelto

Una referencia a este `extent` objeto.

##  <a name="operator_at"></a> Extent:: operator \[\]

Devuelve el elemento que se encuentra en el índice especificado.

### <a name="syntax"></a>Sintaxis

```
int operator[](unsigned int _Index) const restrict(amp,cpu);
int& operator[](unsigned int _Index) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
Un entero comprendido entre 0 y el rango menos 1.

### <a name="return-value"></a>Valor devuelto

El elemento que se encuentra en el índice especificado.

##  <a name="rank_constant"></a> rango

Almacena el rango del objeto 'extensión'.

### <a name="syntax"></a>Sintaxis

```
static const int rank = _Rank;
```

##  <a name="size"></a> Tamaño

Devuelve el tamaño lineal total de la `extent` objeto (en unidades de elementos).

### <a name="syntax"></a>Sintaxis

```
unsigned int size() const restrict(amp,cpu);
```

## <a name="tile"></a> icono

Genera un objeto tiled_extent con las dimensiones especificadas de mosaico.

```
template <int _Dim0>
tiled_extent<_Dim0> tile() const ;

template <int _Dim0, int _Dim1>
tiled_extent<_Dim0, _Dim1> tile() const ;

template <int _Dim0, int _Dim1, int _Dim2>
tiled_extent<_Dim0, _Dim1, _Dim2> tile() const ;
```
### <a name="parameters"></a>Parámetros

*_Dim0*<br/>
El componente más significativo de la extensión del mosaico.
*_Dim1*<br/>
El siguiente-a-componente más significativo de la extensión del mosaico.
*_Dim2*<br/>
El componente menos significativo de la extensión del mosaico.

## <a name="see-also"></a>Vea también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
