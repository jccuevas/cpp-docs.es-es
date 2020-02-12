---
title: index (Clase)
ms.date: 03/27/2019
f1_keywords:
- AMP/index
- AMP/Concurrency::index::index
- AMP/Concurrency::index::rank
helpviewer_keywords:
- index structure
ms.assetid: cbe79b08-0ba7-474c-9828-f1a71da39eb3
ms.openlocfilehash: 06a5fa9a2d7e645c46b90ace957d31251baed81c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127808"
---
# <a name="index-class"></a>index (Clase)

Define un vector de índice de *N*dimensiones.

## <a name="syntax"></a>Sintaxis

```cpp
template <int _Rank>
class index;
```

### <a name="parameters"></a>Parámetros

*_Rank*<br/>
Rango, o número de dimensiones.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[index (constructor)](#index_ctor)|Inicializa una nueva instancia de la clase `index`.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operator--](#operator--)|Disminuye cada elemento del objeto `index`.|
|[operator%=](#operator_mod_eq)|Calcula el módulo (resto) de cada elemento del objeto `index` cuando ese elemento se divide por un número.|
|[operator*=](#operator_star_eq)|Multiplica cada elemento del objeto `index` por un número.|
|[operator/=](#operator_div_eq)|Divide cada elemento del objeto `index` por un número.|
|[index:: Operator\[\]](#operator_at)|Devuelve el elemento que se encuentra en el índice especificado.|
|[operator++](#operator_add_add)|Incrementa cada elemento del objeto `index`.|
|[operator+=](#operator_add_eq)|Agrega el número especificado a cada elemento del objeto `index`.|
|[operator=](#operator_eq)|Copia el contenido del objeto `index` especificado en este.|
|[operator-=](#operator_-_eq)|Resta el número especificado de cada elemento del objeto `index`.|

### <a name="public-constants"></a>Constantes públicas

|Nombre|Descripción|
|----------|-----------------|
|[Rank (constante)](#rank)|Almacena el rango del objeto `index`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`index`

## <a name="remarks"></a>Observaciones

La estructura `index` representa un vector de coordenadas de *N* enteros que especifica una posición única en un espacio de *n*dimensiones. Los valores del vector se ordenan del más significativo al menos significativo. Puede recuperar los valores de los componentes mediante el [operador =](#operator_eq).

## <a name="requirements"></a>Requisitos

**Encabezado:** amp.h

**Espacio de nombres:** Concurrency

## <a name="index_ctor"></a>index (constructor)

Inicializa una nueva instancia de la clase index.

```cpp
index() restrict(amp,cpu);

index(
   const index<_Rank>& _Other
) restrict(amp,cpu);

explicit index(
   int _I
) restrict(amp,cpu);

index(
   int _I0,
   int _I1
) restrict(amp,cpu);

index(
   int _I0,
   int _I1,
   int _I2
) restrict(amp,cpu);

explicit index(
   const int _Array[_Rank]
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Array*<br/>
Matriz unidimensional con los valores de rango.

*_I*<br/>
Ubicación del índice en un índice unidimensional.

*_I0*<br/>
La longitud de la dimensión más significativa.

*_I1*<br/>
La longitud de la siguiente dimensión más significativa.

*_I2*<br/>
La longitud de la dimensión menos significativa.

*_Other*<br/>
Objeto de índice en el que se basa el nuevo objeto de índice.

## <a name="operator--"></a>operador--

Disminuye cada elemento del objeto index.

```cpp
index<_Rank>& operator--() restrict(amp,cpu);

index operator--(
   int
) restrict(amp,cpu);
```

### <a name="return-values"></a>Valores devueltos

Para el operador de prefijo, el objeto de índice (* this). Para el operador de sufijo, un nuevo objeto de índice.

## <a name="operator_mod_eq"></a>operador% =

Calcula el módulo (resto) de cada elemento del objeto index cuando ese elemento se divide por el número especificado.

```cpp
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
Número por el que se va a dividir para buscar el módulo.

## <a name="return-value"></a>Valor devuelto

Objeto de índice.

## <a name="operator_star_eq"></a>operador * =

Multiplica cada elemento del objeto index por el número especificado.

```cpp
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
Número que se va a multiplicar.

## <a name="operator_div_eq"></a>operador/=

Divide cada elemento del objeto index por el número especificado.

```cpp
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
Número por el que se va a dividir.

## <a name="operator_at"></a> operator\[\]

Devuelve el componente del índice en la ubicación especificada.

```cpp
int operator[] (
   unsigned _Index
) const restrict(amp,cpu);

int& operator[] (
   unsigned _Index
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
Entero de 0 a la clasificación menos 1.

### <a name="return-value"></a>Valor devuelto

El elemento que se encuentra en el índice especificado.

### <a name="remarks"></a>Observaciones

En el ejemplo siguiente se muestran los valores de componente del índice.

```cpp
// Prints 1 2 3.
concurrency::index<3> idx(1, 2, 3);
std::cout << idx[0] << "\n";
std::cout << idx[1] << "\n";
std::cout << idx[2] << "\n";
```

## <a name="operator_add_add"></a>operador + +

Incrementa cada elemento del objeto index.

```cpp
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```

### <a name="return-value"></a>Valor devuelto

Para el operador de prefijo, el objeto de índice (* this). Para el operador de sufijo, un nuevo objeto de índice.

## <a name="operator_add_eq"></a>operador + =

Agrega el número especificado a cada elemento del objeto index.

```cpp
index<_Rank>& operator+=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator+=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
Número que se va a agregar.

### <a name="return-value"></a>Valor devuelto

Objeto de índice.

## <a name="operator_eq"></a>  operator=

Copia el contenido del objeto de índice especificado en este.

```cpp
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
Objeto de índice desde el que se va a copiar.

### <a name="return-value"></a>Valor devuelto

Referencia a este objeto index.

## <a name="operator_-_eq"></a>operador-=

Resta el número especificado de cada elemento del objeto index.

```cpp
index<_Rank>& operator-=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator-=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
Número que se va a restar.

### <a name="return-value"></a>Valor devuelto

Objeto de índice.

## <a name="rank"></a>Criterios

Obtiene el rango del objeto index.

```cpp
static const int rank = _Rank;
```

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
