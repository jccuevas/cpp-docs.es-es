---
title: extent (Clase) (C++ AMP)
ms.date: 03/27/2019
f1_keywords:
- extent
- AMP/extent
- AMP/Concurrency::extent::extent
- AMP/Concurrency::extent::contains
- AMP/Concurrency::extent::size
- AMP/Concurrency::extent::tile
- AMP/Concurrency::extent::rank Constant
helpviewer_keywords:
- extent structure
ms.assetid: edb5de3d-3935-4dbb-8365-4cc6c4fb0269
ms.openlocfilehash: 3e8dae7b76ea2efc852486a19f5d298cda477012
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126726"
---
# <a name="extent-class-c-amp"></a>extent (Clase) (C++ AMP)

Representa un vector de valores enteros de *n* que especifican los límites de un espacio de *n*dimensiones que tiene un origen de 0. Los valores del vector se ordenan del más significativo al menos significativo.

## <a name="syntax"></a>Sintaxis

```cpp
template <int _Rank>
class extent;
```

### <a name="parameters"></a>Parámetros

*_Rank*<br/>
Rango del objeto de `extent`.

## <a name="requirements"></a>Requisitos

**Encabezado:** amp.h

**Espacio de nombres:** Concurrency

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Constructor de extensión](#ctor)|Inicializa una nueva instancia de la clase `extent`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[contains](#contains)|Comprueba si el objeto de `extent` especificado tiene el rango especificado.|
|[size](#size)|Devuelve el tamaño lineal total de la extensión (en unidades de elementos).|
|[posición](#tile)|Genera un objeto `tiled_extent` con las extensiones de mosaico proporcionadas por las dimensiones especificadas.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operator-](#operator_min)|Devuelve un nuevo objeto `extent` que se crea restando los elementos `index` de los elementos `extent` correspondientes.|
|[operator--](#operator_min_min)|Disminuye cada elemento del objeto `extent`.|
|[operator%=](#operator_mod_eq)|Calcula el módulo (resto) de cada elemento del objeto `extent` cuando ese elemento se divide por un número.|
|[operator*=](#operator_star_eq)|Multiplica cada elemento del objeto `extent` por un número.|
|[operator/=](#operator_min_eq)|Divide cada elemento del objeto `extent` por un número.|
|[extent:: Operator\[\]](#operator_at)|Devuelve el elemento que se encuentra en el índice especificado.|
|[operator+](#operator_add)|Devuelve un nuevo objeto `extent` que se crea agregando los elementos `extent` y `index` correspondientes.|
|[operator++](#operator_add_add)|Incrementa cada elemento del objeto `extent`.|
|[operator+=](#operator_add_eq)|Agrega el número especificado a cada elemento del objeto `extent`.|
|[operator=](#operator_eq)|Copia el contenido de otro objeto `extent` en este.|
|[operator-=](#operator_min_eq)|Resta el número especificado de cada elemento del objeto `extent`.|

### <a name="public-constants"></a>Constantes públicas

|Nombre|Descripción|
|----------|-----------------|
|[Rank (constante)](#rank_constant)|Obtiene el rango del objeto `extent`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`extent`

## <a name="contains"></a>tuviera

Indica si el valor de [Índice](index-class.md) especificado está incluido en el objeto ' extent '.

### <a name="syntax"></a>Sintaxis

```cpp
bool contains(const index<rank>& _Index) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
Valor `index` que se va a comprobar.

### <a name="return-value"></a>Valor devuelto

**true** si el valor de *Índice* especificado está contenido en el objeto `extent`; en caso contrario, **false**.

## <a name="ctor"></a>expresa

Inicializa una nueva instancia de la clase ' extent '.

### <a name="syntax"></a>Sintaxis

```cpp
extent() restrict(amp,cpu);
extent(const extent<_Rank>& _Other) restrict(amp,cpu);
explicit extent(int _I) restrict(amp,cpu);
extent(int _I0,  int _I1) restrict(amp,cpu);
extent(int _I0,  int _I1, int _I2) restrict(amp,cpu);
explicit extent(const int _Array[_Rank])restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Array*<br/>
Matriz de enteros `_Rank` que se utiliza para crear el nuevo objeto `extent`.

*_I*<br/>
La longitud de la extensión.

*_I0*<br/>
La longitud de la dimensión más significativa.

*_I1*<br/>
La longitud de la siguiente dimensión más significativa.

*_I2*<br/>
La longitud de la dimensión menos significativa.

*_Other*<br/>
Objeto `extent` en el que se basa el nuevo objeto `extent`.

## <a name="remarks"></a>Observaciones

El constructor predeterminado Inicializa un objeto `extent` que tiene un rango de tres.

Si se utiliza una matriz para construir un objeto de `extent`, la longitud de la matriz debe coincidir con el rango del objeto `extent`.

## <a name="operator_mod_eq"></a>operador% =

Calcula el módulo (resto) de cada elemento de la ' extensión ' cuando ese elemento se divide por un número.

### <a name="syntax"></a>Sintaxis

```cpp
extent<_Rank>& operator%=(int _Rhs) restrict(cpu, direct3d);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
Número para el que se va a buscar el módulo.

### <a name="return-value"></a>Valor devuelto

Objeto `extent`.

## <a name="operator_star_eq"></a>operador * =

Multiplica cada elemento del objeto ' extent ' por el número especificado.

### <a name="syntax"></a>Sintaxis

```cpp
extent<_Rank>& operator*=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
Número que se va a multiplicar.

### <a name="return-value"></a>Valor devuelto

Objeto `extent`.

## <a name="operator_add"></a>operador +

Devuelve un nuevo objeto `extent` creado agregando los elementos `extent` y `index` correspondientes.

### <a name="syntax"></a>Sintaxis

```cpp
extent<_Rank> operator+(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
`index` objeto que contiene los elementos que se van a agregar.

### <a name="return-value"></a>Valor devuelto

El nuevo objeto `extent`.

## <a name="operator_add_add"></a>operador + +

Incrementa cada elemento del objeto ' extent '.

### <a name="syntax"></a>Sintaxis

```cpp
extent<_Rank>& operator++() restrict(amp,cpu);
extent<_Rank> operator++(int)restrict(amp,cpu);
```

### <a name="return-value"></a>Valor devuelto

Para el operador de prefijo, el objeto de `extent` (`*this`). Para el operador de sufijo, un nuevo objeto de `extent`.

## <a name="operator_add_eq"></a>operador + =

Agrega el número especificado a cada elemento del objeto ' extent '.

### <a name="syntax"></a>Sintaxis

```cpp
extent<_Rank>& operator+=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
Número, índice o extensión que se va a agregar.

### <a name="return-value"></a>Valor devuelto

El objeto `extent` resultante.

## <a name="operator_min"></a>Operator

Crea un nuevo objeto `extent` restando cada elemento del objeto `index` especificado del elemento correspondiente de este objeto `extent`.

### <a name="syntax"></a>Sintaxis

```cpp
extent<_Rank> operator-(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
`index` objeto que contiene los elementos que se van a restar.

### <a name="return-value"></a>Valor devuelto

El nuevo objeto `extent`.

## <a name="operator_min_min"></a>operador--

Disminuye cada elemento en el objeto ' extent '.

### <a name="syntax"></a>Sintaxis

```cpp
extent<_Rank>& operator--() restrict(amp,cpu);
extent<_Rank> operator--(int)restrict(amp,cpu);
```

### <a name="return-value"></a>Valor devuelto

Para el operador de prefijo, el objeto de `extent` (`*this`). Para el operador de sufijo, un nuevo objeto de `extent`.

## <a name="operator_div_eq"></a>operador/=

Divide cada elemento del objeto ' extent ' por el número especificado.

### <a name="syntax"></a>Sintaxis

```cpp
extent<_Rank>& operator/=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
Número por el que se va a dividir.

### <a name="return-value"></a>Valor devuelto

Objeto `extent`.

## <a name="operator_min_eq"></a>operador-=

Resta el número especificado de cada elemento del objeto ' extent '.

### <a name="syntax"></a>Sintaxis

```cpp
extent<_Rank>& operator-=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
Número que se va a restar.

### <a name="return-value"></a>Valor devuelto

El objeto `extent` resultante.

## <a name="operator_eq"></a>operador =

Copia el contenido de otro objeto ' extent ' en este.

### <a name="syntax"></a>Sintaxis

```cpp
extent<_Rank>& operator=(const extent<_Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
Objeto de `extent` del que se va a copiar.

### <a name="return-value"></a>Valor devuelto

Referencia a este objeto `extent`.

## <a name="operator_at"></a>extent:: Operator \[\]

Devuelve el elemento que se encuentra en el índice especificado.

### <a name="syntax"></a>Sintaxis

```cpp
int operator[](unsigned int _Index) const restrict(amp,cpu);
int& operator[](unsigned int _Index) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
Entero de 0 a la clasificación menos 1.

### <a name="return-value"></a>Valor devuelto

El elemento que se encuentra en el índice especificado.

## <a name="rank_constant"></a>criterios

Almacena el rango del objeto ' extent '.

### <a name="syntax"></a>Sintaxis

```cpp
static const int rank = _Rank;
```

## <a name="size"></a>ajusta

Devuelve el tamaño lineal total del objeto `extent` (en unidades de elementos).

### <a name="syntax"></a>Sintaxis

```cpp
unsigned int size() const restrict(amp,cpu);
```

## <a name="tile"></a>posición

Genera un objeto tiled_extent con las dimensiones de mosaico especificadas.

```cpp
template <int _Dim0>
tiled_extent<_Dim0> tile() const ;

template <int _Dim0, int _Dim1>
tiled_extent<_Dim0, _Dim1> tile() const ;

template <int _Dim0, int _Dim1, int _Dim2>
tiled_extent<_Dim0, _Dim1, _Dim2> tile() const ;
```

### <a name="parameters"></a>Parámetros

*_Dim0*<br/>
El componente más significativo de la extensión en mosaico.
*_Dim1*<br/>
El siguiente componente más significativo de la extensión en mosaico.
*_Dim2*<br/>
El componente menos significativo de la extensión en mosaico.

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
