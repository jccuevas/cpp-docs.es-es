---
title: Extent (clase) (C++ AMP) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp/Concurrency::extent
dev_langs:
- C++
helpviewer_keywords:
- extent structure
ms.assetid: edb5de3d-3935-4dbb-8365-4cc6c4fb0269
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 8aa89b882ed075a8cdf0166d43fde1a5bfe7683d
ms.lasthandoff: 02/24/2017

---
# <a name="extent-class-c-amp"></a>extent (Clase) (C++ AMP)
Representa un vector de *N* valores enteros que especifican los límites de un *N*-espacio de dimensiones que tiene un origen de 0. Los valores del vector se ordenan de la más importante a la menos importante.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
template <int _Rank>  
class extent;  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Rank`  
 El rango de la `extent` objeto.  

 ## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp.h  
  
 **Espacio de nombres:** Concurrency  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Constructor de extensión](#ctor)|Inicializa una nueva instancia de la clase `extent`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Contains (método)](#contains)|Comprueba que el especificado `extent` objeto tiene el rango especificado.|  
|[tamaño (método)](#size)|Devuelve el tamaño total lineal de la extensión (en unidades de elementos).|  
|[mosaico (método)](#tile)|Genera un `tiled_extent` especificó el objeto con las extensiones de mosaico proporcionado por dimensiones.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Operator-(operador)](#operator_min)|Devuelve un nuevo `extent` objeto creado restando el `index` elementos del `extent` elementos.|  
|[operador--(operador)](#operator_min_min)|Disminuye cada elemento de la `extent` objeto.|  
|[Operator % = (operador)](#operator_mod_eq)|Calcula el módulo (resto) de cada elemento de la `extent` del objeto cuando dicho elemento se divide por un número.|  
|[operador * = (operador)](#operator_star_eq)|Multiplica cada elemento de la `extent` objeto mediante un número.|  
|[operador / = (operador)](#operator_min_eq)|Divide cada elemento de la `extent` objeto mediante un número.|  
|[Extent\[\]](#operator_at)|Devuelve el elemento situado en el índice especificado.|  
|[operador + (operador)](#operator_add)|Devuelve un nuevo `extent` objeto que se crea agregando el correspondiente `index` y `extent` elementos.|  
|[operador ++ (operador)](#operator_add_add)|Incrementa en cada elemento de la `extent` objeto.|  
|[operador += (operador)](#operator_add_eq)|Suma el número especificado para cada elemento de la `extent` objeto.|  
|[operador = (operador)](#operator_eq)|Copia el contenido de otro `extent` objeto en éste.|  
|[Operator-= (operador)](#operator_min_eq)|Resta el número especificado de cada elemento de la `extent` objeto.|  

  
### <a name="public-constants"></a>Constantes públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Rank (constante)](#rank)|Obtiene el rango de la `extent` objeto.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `extent`  


## <a name="a-namecontainsa-contains"></a><a name="contains"></a>contiene 

Indica si el texto especificado [índice](index-class.md) valor está dentro del objeto 'extensión'.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
bool contains(const index<rank>& _Index) const restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Index`  
 El `index` valor que desea probar.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el texto especificado `index` valor se incluye en el `extent` objeto; en caso contrario, `false`.  
  
##  <a name="a-namectora-extent"></a><a name="ctor"></a>extensión 

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
 `_Array`  
 Una matriz de `_Rank` enteros que se usa para crear el nuevo `extent` objeto.  
  
 `_I`  
 La longitud de la extensión.  
  
 `_I0`  
 La longitud de la dimensión más importante.  
  
 `_I1`  
 La longitud de la dimensión siguiente-a-más significativo.  
  
 `_I2`  
 La longitud de la dimensión menos significativa.  
  
 `_Other`  
 Un `extent` objeto en el que el nuevo `extent` se basa el objeto.  
  
## <a name="remarks"></a>Comentarios  
 El constructor sin parámetros inicializa un `extent` objeto que tiene un rango de tres.  
  
 Si una matriz se utiliza para construir un `extent` de objeto, la longitud de la matriz debe coincidir con el rango de la `extent` objeto.  
  
##  <a name="a-nameoperatormodeqa-operator"></a><a name="operator_mod_eq"></a>operator % = 

Calcula el módulo (resto) de cada elemento de la medida' ' cuando dicho elemento se divide por un número.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
extent<_Rank>& operator%=(int _Rhs) restrict(cpu, direct3d);  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Rhs`  
 El número para encontrar el módulo de.  
  
### <a name="return-value"></a>Valor devuelto  
 Objeto `extent`.  
  
##  <a name="a-nameoperatorstareqa-operator"></a><a name="operator_star_eq"></a>operador * = 

Multiplica cada elemento en el objeto 'extensión' por el número especificado.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
extent<_Rank>& operator*=(int _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Rhs`  
 Número que se va a multiplicar.  
  
### <a name="return-value"></a>Valor devuelto  
 Objeto `extent`.  
  
## <a name="a-nameoperatoradda-operator"></a><a name="operator_add"></a>operator + 

Devuelve un nuevo `extent` objeto creado mediante la adición de la correspondiente `index` y `extent` elementos.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
extent<_Rank> operator+(const index<_Rank>& _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Rhs`  
 La `index` objeto que contiene los elementos que se va a agregar.  
  
### <a name="return-value"></a>Valor devuelto  
 El nuevo objeto `extent`.  
  
##  <a name="a-nameoperatoraddadda-operator"></a><a name="operator_add_add"></a>operator ++ 

Incrementa cada elemento del objeto 'extensión'.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
extent<_Rank>& operator++() restrict(amp,cpu);    
extent<_Rank> operator++(int)restrict(amp,cpu);  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Para el operador de prefijo, el `extent` objeto (`*this`). Para el operador de sufijo, un nuevo `extent` objeto.  
  
##  <a name="a-nameoperatoraddeqa-operator"></a><a name="operator_add_eq"></a>+= (operador) 

Suma el número especificado para cada elemento del objeto 'extensión'.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
extent<_Rank>& operator+=(const extent<_Rank>& _Rhs) restrict(amp,cpu);    
extent<_Rank>& operator+=(const index<_Rank>& _Rhs) restrict(amp,cpu);    
extent<_Rank>& operator+=(int _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Rhs`  
 El número, índice o extensión a agregar.  
  
### <a name="return-value"></a>Valor devuelto  
 El objeto `extent` resultante.  
  
##  <a name="a-nameoperatormina-operator-"></a><a name="operator_min"></a>operator- 

Crea un nuevo `extent` objeto restando cada elemento de la manera especificada `index` objeto desde el elemento correspondiente en este `extent` objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
extent<_Rank> operator-(const index<_Rank>& _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Rhs`  
 La `index` objeto que contiene los elementos que se va a restar.  
  
### <a name="return-value"></a>Valor devuelto  
 El nuevo objeto `extent`.  
  
##  <a name="a-nameoperatorminmina-operator--"></a><a name="operator_min_min"></a>operador-- 

Disminuye cada elemento en el objeto 'extensión'.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
extent<_Rank>& operator--() restrict(amp,cpu);    
extent<_Rank> operator--(int)restrict(amp,cpu);  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Para el operador de prefijo, el `extent` objeto (`*this`). Para el operador de sufijo, un nuevo `extent` objeto.  
  
##  <a name="a-nameoperatordiveqa-operator"></a><a name="operator_div_eq"></a>/ = (operador) 

Divide cada elemento en el objeto 'extensión' por el número especificado.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
extent<_Rank>& operator/=(int _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Rhs`  
 Número que se va a dividir por.  
  
### <a name="return-value"></a>Valor devuelto  
 Objeto `extent`.  
  
##  <a name="a-nameoperatormineqa-operator-"></a><a name="operator_min_eq"></a>operador = 

Resta el número especificado de cada elemento del objeto 'extensión'.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
extent<_Rank>& operator-=(const extent<_Rank>& _Rhs) restrict(amp,cpu);    
extent<_Rank>& operator-=(const index<_Rank>& _Rhs) restrict(amp,cpu);    
extent<_Rank>& operator-=(int _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Rhs`  
 El número que se resta.  
  
### <a name="return-value"></a>Valor devuelto  
 El objeto `extent` resultante.  
  
##  <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>operador = 

Copia el contenido de otro objeto 'extensión' en éste.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
extent<_Rank>& operator=(const extent<_Rank>& _Other) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `extent` objeto que se va a copiar de.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a este `extent` objeto.  
  
##  <a name="a-nameoperatorata-extentoperator-"></a><a name="operator_at"></a>Extent\[\] 
Devuelve el elemento situado en el índice especificado.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
int operator[](unsigned int _Index) const restrict(amp,cpu);    
int& operator[](unsigned int _Index) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Index`  
 Un entero entre 0 y el rango menos 1.  
  
### <a name="return-value"></a>Valor devuelto  
 El elemento que se encuentra en el índice especificado.  
  
##  <a name="a-namerankconstanta-rank"></a><a name="rank_constant"></a>rango 

Almacena el rango del objeto 'extensión'.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="a-namesizea-size"></a><a name="size"></a>tamaño 

Devuelve el tamaño total lineal de la `extent` objeto (en unidades de elementos).  
  
### <a name="syntax"></a>Sintaxis  

```  
unsigned int size() const restrict(amp,cpu);  
```  
  
## <a name="a-nametilea-tile"></a><a name="tile"></a>Mosaico 

Genera un objeto tiled_extent () con las dimensiones del mosaico especificado.

```
template <int _Dim0>
tiled_extent<_Dim0> tile() const ;

template <int _Dim0, int _Dim1>
tiled_extent<_Dim0, _Dim1> tile() const ;

template <int _Dim0, int _Dim1, int _Dim2>
tiled_extent<_Dim0, _Dim1, _Dim2> tile() const ;
```  
### <a name="parameters"></a>Parámetros
`_Dim0`El componente más importante de la extensión del mosaico.
`_Dim1`El componente siguiente-a-más significativo de la extensión del mosaico.
`_Dim2`El componente menos significativo de la extensión del mosaico.


  
## <a name="see-also"></a>Vea también  
 [Namespace de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)

