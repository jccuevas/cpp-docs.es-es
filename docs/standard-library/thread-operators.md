---
title: Operadores de &lt;thread&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: []
ms.assetid: e6bb6c0f-64f9-4cb2-9ff2-05b88a6ba7ac
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 7e849e8585b372b5b423a6c960aa926ac7d5cfec
ms.lasthandoff: 02/24/2017

---
# <a name="ltthreadgt-operators"></a>Operadores de &lt;thread&gt;
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator&gt;](#operator_gt_)|[operator&gt;=](#operator_gt__eq)|  
|[operator&lt;](#operator_lt_)|[operator&lt;&lt;](#operator_lt__lt_)|[operator&lt;=](#operator_lt__eq)|  
|[operator==](#operator_eq_eq)|  
  
##  <a name="operator_gt__eq"></a>  operator&gt;=  
 Determina si un objeto `thread::id` es mayor o igual que otro objeto.  
  
```cpp  
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>Parámetros  
 `Left`  
 Objeto `thread::id` izquierdo.  
  
 `Right`  
 Objeto `thread::id` derecho.  
  
### <a name="return-value"></a>Valor devuelto  
 `!(Left < Right)`  
  
### <a name="remarks"></a>Comentarios  
 Esta función no produce ninguna excepción.  
  
##  <a name="operator_gt_"></a>  operator&gt;  
 Determina si un objeto `thread::id` es mayor que otro objeto.  
  
```cpp  
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>Parámetros  
 `Left`  
 Objeto `thread::id` izquierdo.  
  
 `Right`  
 Objeto `thread::id` derecho.  
  
### <a name="return-value"></a>Valor devuelto  
 `Right < Left`  
  
### <a name="remarks"></a>Comentarios  
 Esta función no produce ninguna excepción.  
  
##  <a name="operator_lt__eq"></a>  operator&lt;=  
 Determina si un objeto `thread::id` es menor o igual que otro objeto.  
  
```cpp  
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>Parámetros  
 `Left`  
 Objeto `thread::id` izquierdo.  
  
 `Right`  
 Objeto `thread::id` derecho.  
  
### <a name="return-value"></a>Valor devuelto  
 `!(Right < Left)`  
  
### <a name="remarks"></a>Comentarios  
 Esta función no produce ninguna excepción.  
  
##  <a name="operator_lt_"></a>  operator&lt;  
 Determina si un objeto `thread::id` es menor que otro objeto.  
  
```cpp  
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>Parámetros  
 `Left`  
 Objeto `thread::id` izquierdo.  
  
 `Right`  
 Objeto `thread::id` derecho.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si `Left` precede a `Right` en la ordenación total. De lo contrario es `false`.  
  
### <a name="remarks"></a>Comentarios  
 El operador define una ordenación total en todos los objetos `thread::id`. Estos objetos pueden usarse como claves en contenedores asociativos.  
  
 Esta función no produce ninguna excepción.  
  
##  <a name="operator_neq"></a>  operator!=  
 Compara dos objetos `thread::id` para determinar si no son iguales.  
  
```cpp  
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>Parámetros  
 `Left`  
 Objeto `thread::id` izquierdo.  
  
 `Right`  
 Objeto `thread::id` derecho.  
  
### <a name="return-value"></a>Valor devuelto  
 `!(Left == Right)`  
  
### <a name="remarks"></a>Comentarios  
 Esta función no produce ninguna excepción.  
  
##  <a name="operator_eq_eq"></a>  operator==  
 Compara dos objetos `thread::id` para determinar si son iguales.  
  
```cpp  
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>Parámetros  
 `Left`  
 Objeto `thread::id` izquierdo.  
  
 `Right`  
 Objeto `thread::id` derecho.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si los dos objetos representan el mismo subproceso de ejecución o si ninguno de estos objetos representa un subproceso de ejecución. De lo contrario es `false`.  
  
### <a name="remarks"></a>Comentarios  
 Esta función no produce ninguna excepción.  
  
##  <a name="operator_lt__lt_"></a>  operator&lt;&lt;  
 Inserta una representación de texto de un objeto `thread::id` en una secuencia.  
  
```cpp  
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```  
  
### <a name="parameters"></a>Parámetros  
 `Ostr`  
 Un objeto [basic_ostream](../standard-library/basic-ostream-class.md).  
  
 `Id`  
 Objeto `thread::id`.  
  
### <a name="return-value"></a>Valor devuelto  
 `Ostr`Operador  
  
### <a name="remarks"></a>Comentarios  
 Esta función inserta `Id` en `Ostr`.  
  
 Si dos objetos `thread::id` son iguales, las representaciones de texto insertadas de dichos objetos son iguales.  
  
## <a name="see-also"></a>Vea también  
 [\<thread>](../standard-library/thread.md)




