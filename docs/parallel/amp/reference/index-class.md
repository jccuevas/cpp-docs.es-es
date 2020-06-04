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
ms.openlocfilehash: 50222015e6b365dc161fd4334067c26c7f288337
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365150"
---
# <a name="index-class"></a>index (Clase)

Define *un*vector de índice de n dimensiones.

## <a name="syntax"></a>Sintaxis

```cpp
template <int _Rank>
class index;
```

### <a name="parameters"></a>Parámetros

*_Rank*<br/>
El rango o el número de dimensiones.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[constructor de índices](#index_ctor)|Inicializa una nueva instancia de la clase `index`.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operador--](#operator--)|Disminuye cada elemento del `index` objeto.|
|[operadora%](#operator_mod_eq)|Calcula el módulo (resto) de cada `index` elemento del objeto cuando ese elemento se divide por un número.|
|[operador*](#operator_star_eq)|Multiplica cada elemento `index` del objeto por un número.|
|[operador/](#operator_div_eq)|Divide cada elemento `index` del objeto por un número.|
|[index::operator\[\]](#operator_at)|Devuelve el elemento que se encuentra en el índice especificado.|
|[operador++](#operator_add_add)|Incrementa cada elemento `index` del objeto.|
|[operador +o](#operator_add_eq)|Agrega el número especificado a cada `index` elemento del objeto.|
|[operador](#operator_eq)|Copia el contenido del `index` objeto especificado en éste.|
|[operador-](#operator_-_eq)|Resta el número especificado de `index` cada elemento del objeto.|

### <a name="public-constants"></a>Constantes públicas

|Nombre|Descripción|
|----------|-----------------|
|[rango Constante](#rank)|Almacena el rango `index` del objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`index`

## <a name="remarks"></a>Observaciones

La `index` estructura representa un vector de coordenadas de *N* enteros que especifica una posición única en un espacio dimensional *N.* Los valores del vector se ordenan de más significativo a menos significativo. Puede recuperar los valores de los componentes mediante [operator](#operator_eq).

## <a name="requirements"></a>Requisitos

**Encabezado:** amp.h

**Espacio de nombres:** Concurrencia

## <a name="index-constructor"></a><a name="index_ctor"></a>constructor de índices

Inicializa una nueva instancia de la clase de índice.

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
Matriz unidimensional con los valores de clasificación.

*_I*<br/>
La ubicación del índice en un índice unidimensional.

*_I0*<br/>
La longitud de la dimensión más significativa.

*_I1*<br/>
La longitud de la dimensión siguiente a la más significativa.

*_I2*<br/>
La longitud de la dimensión menos significativa.

*_Other*<br/>
Objeto de índice en el que se basa el nuevo objeto de índice.

## <a name="operator--"></a><a name="operator--"></a>operador--

Disminuye cada elemento del objeto de índice.

```cpp
index<_Rank>& operator--() restrict(amp,cpu);

index operator--(
   int
) restrict(amp,cpu);
```

### <a name="return-values"></a>Valores devueltos

Para el operador de prefijo, el objeto de índice (*this). Para el operador de sufijo, un nuevo objeto de índice.

## <a name="operator"></a><a name="operator_mod_eq"></a>operadora%

Calcula el módulo (resto) de cada elemento del objeto de índice cuando ese elemento se divide por el número especificado.

```cpp
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
El número por el que se debe dividir para encontrar el módulo.

## <a name="return-value"></a>Valor devuelto

El objeto de índice.

## <a name="operator"></a><a name="operator_star_eq"></a>operador*

Multiplica cada elemento del objeto de índice por el número especificado.

```cpp
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
El número que se debe multiplicar.

## <a name="operator"></a><a name="operator_div_eq"></a>operador/

Divide cada elemento del objeto de índice por el número especificado.

```cpp
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
El número por el que dividir.

## <a name="operator"></a><a name="operator_at"></a>Operador\[\]

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
Un entero de 0 a la clasificación menos 1.

### <a name="return-value"></a>Valor devuelto

El elemento que está en el índice especificado.

### <a name="remarks"></a>Observaciones

En el ejemplo siguiente se muestran los valores de componente del índice.

```cpp
// Prints 1 2 3.
concurrency::index<3> idx(1, 2, 3);
std::cout << idx[0] << "\n";
std::cout << idx[1] << "\n";
std::cout << idx[2] << "\n";
```

## <a name="operator"></a><a name="operator_add_add"></a>operador++

Incrementa cada elemento del objeto de índice.

```cpp
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```

### <a name="return-value"></a>Valor devuelto

Para el operador de prefijo, el objeto de índice (*this). Para el operador de sufijo, un nuevo objeto de índice.

## <a name="operator"></a><a name="operator_add_eq"></a>operador +o

Agrega el número especificado a cada elemento del objeto de índice.

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
El número que se va a agregar.

### <a name="return-value"></a>Valor devuelto

El objeto de índice.

## <a name="operator"></a><a name="operator_eq"></a>operador

Copia el contenido del objeto de índice especificado en éste.

```cpp
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
El objeto de índice desde el que se va a copiar.

### <a name="return-value"></a>Valor devuelto

Una referencia a este objeto de índice.

## <a name="operator-"></a><a name="operator_-_eq"></a>operador-

Resta el número especificado de cada elemento del objeto de índice.

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
El número que se va a restar.

### <a name="return-value"></a>Valor devuelto

El objeto de índice.

## <a name="rank"></a><a name="rank"></a>rango

Obtiene el rango del objeto de índice.

```cpp
static const int rank = _Rank;
```

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
