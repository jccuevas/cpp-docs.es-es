---
title: Index (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AMP/index
- AMP/Concurrency::index::index
- AMP/Concurrency::index::rank
dev_langs: C++
helpviewer_keywords: index structure
ms.assetid: cbe79b08-0ba7-474c-9828-f1a71da39eb3
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8a1c4213ee94c063a7dff2a5b2c5e156b0ee91a7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="index-class"></a>index (Clase)
Define un *N*-dimensional índice pographics-cpp-amp.md.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <int _Rank>  
class index;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `_Rank`  
 El rango o el número de dimensiones.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[índice de Constructor](#ctor)|Inicializa una nueva instancia de la clase `index`.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[operator--](#operator--)|Disminuye cada elemento de la `index` objeto.|  
|[Operator(MOD) =](#operator_mod_eq)|Calcula el módulo (resto) de cada elemento de la `index` del objeto cuando dicho elemento se divide por un número.|  
|[operator*=](#operator_star_eq)|Multiplica cada elemento de la `index` objeto mediante un número.|  
|[operator/=](#operator_div_eq)|Divide cada elemento de la `index` objeto mediante un número.|  
|[Index:: operator\[\]](#operator_at)|Devuelve el elemento situado en el índice especificado.|  
|[operator++](#operator_add_add)|Incrementa cada elemento de la `index` objeto.|  
|[operator+=](#operator_add_eq)|Suma el número especificado para cada elemento de la `index` objeto.|  
|[operator=](#operator_eq)|Copia el contenido del elemento especificado `index` objeto en éste.|  
|[operator-=](#operator_-_eq)|Resta el número especificado de cada elemento de la `index` objeto.|  

  
### <a name="public-constants"></a>Constantes públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Rank (constante)](#rank)|Almacena el rango de la `index` objeto.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `index`  
  
## <a name="remarks"></a>Comentarios  
 El `index` estructura representa un vector de coordenadas de *N* enteros que especifica una posición única en una *N*-espacio de dimensiones. Los valores del vector se ordenan de la más importante a la menos importante. Puede recuperar los valores de los componentes mediante [operador =](#operator_eq).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp.h  
  
 **Espacio de nombres:** Concurrency  


## <a name="index_ctor"></a>índice de Constructor
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

_Array  
Una matriz unidimensional con los valores de clasificación.  
_HE  
La ubicación de índice en un índice unidimensional.  
_I0  
La longitud de la dimensión más significativa.  
_I1  
La longitud de la dimensión siguiente-a-más significativo.  
_I2  
La longitud de la dimensión menos significativa.  
_Other  
Un objeto de índice en el que se basa el nuevo objeto de índice.  

## <a name="operator--"></a>operador--
Disminuye cada elemento de objeto de índice.  
```  
index<_Rank>& operator--() restrict(amp,cpu);  

index operator--(
   int
) restrict(amp,cpu);
```  
### <a name="return-values"></a>Valores devueltos
Para el operador de prefijo, el objeto de índice (* esto). Para el operador de sufijo, un nuevo objeto de índice.

## <a name="operator_mod_eq"></a>Operator(MOD) =   
Calcula el módulo (resto) de cada elemento en el objeto index cuando dicho elemento se divide por el número especificado.

```  
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```  
### <a name="parameters"></a>Parámetros
_Rhs el número que se va a dividir por para encontrar el módulo.
El objeto de índice de valor devuelto.

## <a name="operator_star_eq"></a>operador * =   
Multiplica cada elemento en el objeto de índice en el número especificado.
```
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros
_Rhs el número que se va a multiplicar.

## <a name="operator_div_eq"></a>operador / = 
Divide cada elemento en el objeto de índice por el número especificado.

```
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
``` 
### <a name="parameters"></a>Parámetros
_Rhs el número que se va a dividir.

## <a name="operator_at"></a>  operator\[\]  
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
_Index un entero comprendido entre 0 y el rango menos 1.

### <a name="return-value"></a>Valor devuelto
El elemento situado en el índice especificado.

### <a name="remarks"></a>Comentarios
En el ejemplo siguiente se muestra los valores del componente del índice.
```  
// Prints 1 2 3.
concurrency::index<3> idx(1, 2, 3);
std::cout << idx[0] << "\n";
std::cout << idx[1] << "\n";
std::cout << idx[2] << "\n";
```

## <a name="operator_add_add"></a>operator ++   
Incrementa cada elemento de objeto de índice.
```  
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```  
### <a name="return-value"></a>Valor devuelto
Para el operador de prefijo, el objeto de índice (* esto). Para el operador de sufijo, un nuevo objeto de índice.

## <a name="operator_add_eq"></a>+= (operador)   
Suma el número especificado para cada elemento de objeto de índice.
```  
index<_Rank>& operator+=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator+=(
   int _Rhs
) restrict(amp,cpu);
``` 
### <a name="parameters"></a>Parámetros
_Rhs el número para agregar.

### <a name="return-value"></a>Valor devuelto
El objeto de índice.

## <a name="operator_eq"></a>  operator=   
Copia el contenido del objeto de índice especificado en éste.
```  
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
``` 
### <a name="parameters"></a>Parámetros
_Other el objeto de índice que lo copien.

### <a name="return-value"></a>Valor devuelto
Una referencia a este objeto de índice.

## <a name="operator_-_eq"></a>operador =
Resta el número especificado de cada elemento de objeto de índice.
```  
index<_Rank>& operator-=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator-=(
   int _Rhs
) restrict(amp,cpu);
```  
### <a name="parameters"></a>Parámetros
_Rhs el número que se resta.

### <a name="return-value"></a>Valor devuelto
El objeto de índice.   

## <a name="rank"></a>Rango  
  Obtiene el rango del objeto de índice.
```
static const int rank = _Rank;
``` 
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
