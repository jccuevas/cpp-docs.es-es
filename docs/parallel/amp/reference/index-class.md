---
title: index (Clase)
ms.date: 11/04/2016
f1_keywords:
- AMP/index
- AMP/Concurrency::index::index
- AMP/Concurrency::index::rank
helpviewer_keywords:
- index structure
ms.assetid: cbe79b08-0ba7-474c-9828-f1a71da39eb3
ms.openlocfilehash: 054db83e4d8e140af37dcff9a7664ffdf7902325
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284650"
---
# <a name="index-class"></a>index (Clase)

Define un *N*-dimensional índice pographics-cpp-amp.md.

## <a name="syntax"></a>Sintaxis

```
template <int _Rank>
class index;
```

#### <a name="parameters"></a>Parámetros

*_Rank*<br/>
El rango o número de dimensiones.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[índice de Constructor](#ctor)|Inicializa una nueva instancia de la clase `index`.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[operator--](#operator--)|Disminuye cada elemento de la `index` objeto.|
|[operator(mod)=](#operator_mod_eq)|Calcula el módulo (resto) de cada elemento en el `index` cuando dicho elemento se divide por un número de objetos.|
|[operator*=](#operator_star_eq)|Multiplica cada elemento de la `index` objeto según un número.|
|[operator/=](#operator_div_eq)|Divide cada elemento de la `index` objeto según un número.|
|[index::operator\[\]](#operator_at)|Devuelve el elemento que se encuentra en el índice especificado.|
|[operator++](#operator_add_add)|Incrementa cada elemento de la `index` objeto.|
|[operator+=](#operator_add_eq)|Agrega el número especificado a cada elemento de la `index` objeto.|
|[operator=](#operator_eq)|Copia el contenido del elemento especificado `index` objeto en este.|
|[operator-=](#operator_-_eq)|Resta el número especificado de cada elemento de la `index` objeto.|

### <a name="public-constants"></a>Constantes públicas

|nombre|Descripción|
|----------|-----------------|
|[rank Constant](#rank)|Almacena el rango de la `index` objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`index`

## <a name="remarks"></a>Comentarios

El `index` estructura representa un vector de coordenadas de *N* enteros que especifica una posición única en un *N*-espacio de dimensiones. Los valores del vector se ordenan del más significativo al menos significativo. Puede recuperar los valores de los componentes mediante [operador =](#operator_eq).

## <a name="requirements"></a>Requisitos

**Encabezado:** amp.h

**Espacio de nombres**: simultaneidad

## <a name="index_ctor"></a> índice de Constructor

Inicializa una nueva instancia de la clase de índice.

```
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
Una matriz unidimensional con los valores de clasificación.

*_I*<br/>
La ubicación de índice en un índice unidimensional.

*_I0*<br/>
La longitud de la dimensión más significativa.

*_I1*<br/>
La longitud de la dimensión para la mayoría-significativo.

*_I2*<br/>
La longitud de la dimensión menos significativa.

*_Other*<br/>
Un objeto de índice en el que se basa el nuevo objeto de índice.

## <a name="operator--"></a>  operator--

Disminuye cada elemento del objeto index.
```
index<_Rank>& operator--() restrict(amp,cpu);

index operator--(
   int
) restrict(amp,cpu);
```

### <a name="return-values"></a>Valores devueltos

Para el operador de prefijo, el objeto de índice (* esto). Para el operador sufijo, un nuevo objeto de índice.

## <a name="operator_mod_eq"></a>  operator(mod)=

Calcula el módulo (resto) de cada elemento en el objeto de índice cuando dicho elemento se divide por el número especificado.

```
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
El número que se divide por para encontrar el módulo.

## <a name="return-value"></a>Valor devuelto
El objeto de índice.

## <a name="operator_star_eq"></a>  operator*=

Multiplica cada elemento en el objeto de índice por el número especificado.
```
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
El número que se va a multiplicar.

## <a name="operator_div_eq"></a>  operator/=

Divide cada elemento en el objeto de índice por el número especificado.

```
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
Dividir por el número.

## <a name="operator_at"></a> operator\[\]

Devuelve el componente del índice en la ubicación especificada.

```
int operator[] (
   unsigned _Index
) const restrict(amp,cpu);

int& operator[] (
   unsigned _Index
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
Un entero comprendido entre 0 y el rango menos 1.

### <a name="return-value"></a>Valor devuelto

El elemento que se encuentra en el índice especificado.

### <a name="remarks"></a>Comentarios

En el ejemplo siguiente se muestra los valores del componente del índice.
```
// Prints 1 2 3.
concurrency::index<3> idx(1, 2, 3);
std::cout << idx[0] << "\n";
std::cout << idx[1] << "\n";
std::cout << idx[2] << "\n";
```

## <a name="operator_add_add"></a>  operator++

Incrementa cada elemento del objeto index.
```
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```

### <a name="return-value"></a>Valor devuelto

Para el operador de prefijo, el objeto de índice (* esto). Para el operador sufijo, un nuevo objeto de índice.

## <a name="operator_add_eq"></a>  operator+=

Agrega el número especificado a cada elemento del objeto index.
```
index<_Rank>& operator+=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator+=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
El número que se agregará.

### <a name="return-value"></a>Valor devuelto

El objeto de índice.

## <a name="operator_eq"></a>  operator=

Copia el contenido del objeto de índice especificado en este.
```
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
Para copiar desde el objeto de índice.

### <a name="return-value"></a>Valor devuelto

Una referencia a este objeto de índice.

## <a name="operator_-_eq"></a>  operator-=

Resta el número especificado de cada elemento del objeto de índice.
```
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

## <a name="rank"></a>  rango
  Obtiene el rango del objeto index.
```
static const int rank = _Rank;
```

## <a name="see-also"></a>Vea también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
