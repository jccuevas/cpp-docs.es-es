---
title: Operadores de espacio de nombres de simultaneidad (AMP) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7cc8e24c8fd1524ebaaf6c2a8edaec05ab865733
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="concurrency-namespace-operators-amp"></a>Operadores de espacio de nombres de simultaneidad (AMP)
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator%](#operator_mod)|[operator*](#operator_star)|  
|[operator+](#operator_add)|[operator-](#operator-)|[operator/](#operator_div)|  
|[operator==](#operator_eq_eq)|  
  
##  <a name="operator_eq_eq"></a>  operator==   
 Determina si los argumentos especificados son iguales.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
bool operator== (
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Rank`  
 El rango de los argumentos de la tupla.  
  
 `_Lhs`  
 Una de las tuplas para comparar.  
  
 `_Rhs`  
 Una de las tuplas para comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si las tuplas son iguales; en caso contrario, `false`.  
  
##  <a name="operator_neq"></a>  operator!=   
 Determina si los argumentos especificados no son iguales.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
bool operator!= (
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Rank`  
 El rango de los argumentos de la tupla.  
  
 `_Lhs`  
 Una de las tuplas para comparar.  
  
 `_Rhs`  
 Una de las tuplas para comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si las tuplas no son iguales; en caso contrario, `false`.  
  
##  <a name="operator_add"></a>  operator+   

 Calcula la suma de todos los componentes de los argumentos especificados.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Rank`  
 El rango de los argumentos de la tupla.  
  
 `_Lhs`  
 Uno de los argumentos que se van a agregar.  
  
 `_Rhs`  
 Uno de los argumentos que se van a agregar.  
  
### <a name="return-value"></a>Valor devuelto  
 La suma de todos los de los argumentos especificados.  
  
##  <a name="operator-"></a>  operator-   

 Calcula la diferencia de todos los componentes entre los argumentos especificados.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator-(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Rank`  
 El rango de los argumentos de la tupla.  
  
 `_Lhs`  
 Argumento que se va a restar.  
  
 `_Rhs`  
 El argumento que se resta.  
  
### <a name="return-value"></a>Valor devuelto  
 La diferencia de todos los entre los argumentos especificados.  
  
##  <a name="operator_star"></a>  operator*   

 Calcula el producto de todos los componentes de los argumentos especificados.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator*(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator*(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp, cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Rank`  
 El rango de los argumentos de la tupla.  
  
 `_Lhs`  
 Una de las tuplas para multiplicar.  
  
 `_Rhs`  
 Una de las tuplas para multiplicar.  
  
### <a name="return-value"></a>Valor devuelto  
 El producto de todos los de los argumentos especificados.  
  

##  <a name="operator_div"></a>  operator/   
 Calcula el cociente de todos los componentes de los argumentos especificados.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator/(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator/(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Rank`  
 El rango de los argumentos de la tupla.  
  
 `_Lhs`  
 La tupla que se va a dividir.  
  
 `_Rhs`  
 La tupla dividir por.  
  
### <a name="return-value"></a>Valor devuelto  
 El cociente de todos los de los argumentos especificados.  
  
##  <a name="operator_mod"></a>  operator%   

 Calcula el módulo del primer argumento especificado dividido por el segundo argumento especificado.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator%(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator%(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Rank`  
 El rango de los argumentos de la tupla.  
  
 `_Lhs`  
 La tupla desde el que el módulo se calcula.  
  
 `_Rhs`  
 La tupla al módulo por.  
  
### <a name="return-value"></a>Valor devuelto  
 El resultado del primer módulo de argumento especificado el segundo argumento especificado.  
  
## <a name="see-also"></a>Vea también  
 [Namespace de simultaneidad](concurrency-namespace-cpp-amp.md)
