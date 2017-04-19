---
title: Operadores de &lt;chrono&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- chrono/std::operator modulo
ms.assetid: c5a19267-4684-40c1-b7a9-cc1012b058f3
caps.latest.revision: 8
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: c2ea4241ef1db4989caf8cdc6a16044d9c9381f6
ms.lasthandoff: 02/24/2017

---
# <a name="ltchronogt-operators"></a>Operadores de &lt;chrono&gt;
||||  
|-|-|-|  
|[operator modulo](#operator_modulo)|[operator!=](#operator_neq)|[operator&gt;](#operator_gt_)|  
|[operator&gt;=](#operator_gt__eq)|[operator&lt;](#operator_lt_)|[operator&lt;=](#operator_lt__eq)|  
|[operator*](#operator_star)|[operator+](#operator_add)|[operator-](#operator-)|  
|[operator/](#operator_)|[operator==](#operator_eq_eq)|  
  
##  <a name="operator-"></a>  operator-  
 Operador para la resta o la negación de objetos [duration](../standard-library/duration-class.md) y [time_point](../standard-library/time-point-class.md).  
  
```  
template <class Rep1, class Period1, class Rep2, class Period2>  
constexpr typename common_type<duration<Rep1, Period1>, duration<Rep2, Period2>>::type 
   operator-(
       const duration<Rep1, Period1>& Left, 
       cconst duration<Rep2, Period2>& Right);
 
template <class Clock, class Duration1, class Rep2, class Period2>  
constexpr time_point<Clock, typename common_type<Duration1, duration<Rep2, Period2>>::type  
   operator-(
       const time_point<Clock, Duration1>& Time, 
       const duration<Rep2, Period2>& Dur);

 
template <class Clock, class Duration1, class Duration2>  
constexpr typename common_type<Duration1, Duration2>::type 
   operator-(
       const time_point<Clock, Duration1>& Left, 
       const time_point<Clock, Duration2>& Right);
```  
  
### <a name="parameters"></a>Parámetros  
 `Left`  
 Objeto `duration` o `time_point` izquierdo.  
  
 `Right`  
 Objeto `duration` o `time_point` derecho.  
  
 `Time`  
 Objeto `time_point`.  
  
 `Dur`  
 Objeto `duration`.  
  
### <a name="return-value"></a>Valor devuelto  
 La primera función devuelve un objeto `duration` cuya longitud del intervalo es la diferencia entre los intervalos de tiempo de los dos argumentos.  
  
 La segunda función devuelve un objeto `time_point` que representa un punto en el tiempo que está desplazado, por la negación del intervalo de tiempo representado por `Dur`, con respecto al punto en el tiempo especificado por `Time`.  
  
 La tercera función devuelve un objeto `duration` que representa el intervalo de tiempo entre `Left` y `Right`.  
  
##  <a name="operator_neq"></a>  operator!=  
 Operador de desigualdad para objetos [duration](../standard-library/duration-class.md) o [time_point](../standard-library/time-point-class.md).  
  
```  
template <class Rep1, class Period1, class Rep2, class Period2>  
constexpr bool operator!=(
    const duration<Rep1, Period1>& Left,  
    const duration<Rep2, Period2>& Right);

 
template <class Clock, class Duration1, class Duration2>  
constexpr bool operator!=(
    const time_point<Clock, Duration1>& Left,  
    const time_point<Clock, Duration2>& Right);
```  
  
### <a name="parameters"></a>Parámetros  
 `Left`  
 Objeto `duration` o `time_point` izquierdo.  
  
 `Right`  
 Objeto `duration` o `time_point` derecho.  
  
### <a name="return-value"></a>Valor devuelto  
 Cada función devuelve `!(Left == Right)`.  
  
##  <a name="operator_star"></a>  operator*  
 Operador de multiplicación para objetos [duration](../standard-library/chrono-operators.md#operator_star).  
  
```  
template <class Rep1, class Period1, class Rep2>  
constexpr duration<typename common_type<Rep1, Rep2>::type, Period1> 
   operator*(
      const duration<Rep1, Period1>& Dur, 
      const Rep2& Mult);

 
template <class Rep1, class Rep2, class Period2>  
constexpr duration<typename common_type<Rep1, Rep2>::type, Period2> 
   operator*(
       const Rep1& Mult,
       const duration<Rep2, 
       Period2>& Dur);
```  
  
### <a name="parameters"></a>Parámetros  
 `Dur`  
 Objeto `duration`.  
  
 `Mult`  
 Valor entero.  
  
### <a name="return-value"></a>Valor devuelto  
 Cada función devuelve un objeto `duration` cuya longitud del intervalo es `Mult` multiplicada por la longitud de `Dur`.  
  
 A menos que `is_convertible<Rep2, common_type<Rep1, Rep2>>`*sea True*, la primera función no participa en la resolución de sobrecarga. Para obtener más información, vea [<type_traits>](../standard-library/type-traits.md).  
  
 A menos que `is_convertible<Rep1, common_type<Rep1, Rep2>>`*sea True*, la segunda función no participa en la resolución de sobrecarga. Para obtener más información, vea [<type_traits>](../standard-library/type-traits.md).  
  
##  <a name="operator_"></a>  operator/  
 Operador de división para objetos [duration](../standard-library/chrono-operators.md#operator_star).  
  
```  
template <class Rep1, class Period1, class Rep2>  
constexpr duration<typename common_type<Rep1, Rep2>::type, Period1> 
   operator/(
     const duration<Rep1, Period1>& Dur,  
     const Rep2& Div);

 
template <class Rep1, class Period1, class Rep2, class Period2>  
constexpr typename common_type<Rep1, Rep2>::type 
   operator/(
     const duration<Rep1, Period1>& Left,  
     const duration<Rep2, Period2>& Right);
```  
  
### <a name="parameters"></a>Parámetros  
 `Dur`  
 Objeto `duration`.  
  
 `Div`  
 Valor entero.  
  
 `Left`  
 Objeto `duration` izquierdo.  
  
 `Right`  
 Objeto `duration` derecho.  
  
### <a name="return-value"></a>Valor devuelto  
 El primer operador devuelve un objeto de duración cuya longitud del intervalo es la longitud de `Dur` dividida por el valor `Div`.  
  
 El segundo operador devuelve la relación entre las longitudes de intervalo de `Left` y `Right`.  
  
 A menos que `is_convertible<Rep2, common_type<Rep1, Rep2>>`*sea True*, y `Rep2` no sea una creación de instancia de `duration`, el primer operador no participa en la resolución de sobrecarga. Para obtener más información, vea [<type_traits>](../standard-library/type-traits.md).  
  
##  <a name="operator_add"></a>  operator+  
 Suma los objetos [duration](../standard-library/duration-class.md) y [time_point](../standard-library/time-point-class.md).  
  
```  
template <class Rep1, class Period1, class Rep2, class Period2>  
constexpr typename common_type<duration<Rep1, Period1>, duration<Rep2, Period2>>::type 
   operator+(
      const duration<Rep1, Period1>& Left,  
      const duration<Rep2, Period2>& Right);

 
template <class Clock, class Duration1, class Rep2, class Period2>  
constexpr time_point<Clock, typename common_type<Duration1, duration<Rep2, Period2>>::type>
   operator+(
      const time_point<Clock, Duration1>& Time,  
      const duration<Rep2, Period2>& Dur);

 
template <class Rep1, class Period1, class Clock, class Duration2>  
time_point<Clock, constexpr typename common_type<duration<Rep1, Period1>, Duration2>::type>
   operator+(
      const duration<Rep1, Period1>& Dur,  
      const time_point<Clock, Duration2>& Time);
```  
  
### <a name="parameters"></a>Parámetros  
 `Left`  
 Objeto `duration` o `time_point` izquierdo.  
  
 `Right`  
 Objeto `duration` o `time_point` derecho.  
  
 `Time`  
 Objeto `time_point`.  
  
 `Dur`  
 Objeto `duration`.  
  
### <a name="return-value"></a>Valor devuelto  
 La primera función devuelve un objeto `duration` cuyo intervalo de tiempo es igual a la suma de los intervalos de `Left` y `Right`.  
  
 Las funciones segunda y tercera devuelven un objeto `time_point` que representa un punto en el tiempo que está desplazado, según el intervalo `Dur`, con respecto al punto en el tiempo `Time`.  
  
##  <a name="operator_lt_"></a>  operator&lt;  
 Determina si un objeto [duration](../standard-library/duration-class.md) o [time_point](../standard-library/time-point-class.md) es menor que otro objeto `duration` o `time_point`.  
  
```  
template <class Rep1, class Period1, class Rep2, class Period2>  
constexpr bool operator<(
    const duration<Rep1, Period1>& Left,  
    const duration<Rep2, Period2>& Right);

 
template <class Clock, class Duration1, class Duration2>  
constexpr bool operator<(
    const time_point<Clock, Duration1>& Left,  
    const time_point<Clock, Duration2>& Right);
```  
  
### <a name="parameters"></a>Parámetros  
 `Left`  
 Objeto `duration` o `time_point` izquierdo.  
  
 `Right`  
 Objeto `duration` o `time_point` derecho.  
  
### <a name="return-value"></a>Valor devuelto  
 La primera función devuelve `true` si la longitud del intervalo de `Left` es menor que la longitud del intervalo de `Right`. De lo contrario, la función devuelve `false`.  
  
 La segunda función devuelve `true` si `Left` precede a `Right`. De lo contrario, la función devuelve `false`.  
  
##  <a name="operator_lt__eq"></a>  operator&lt;=  
 Determina si un objeto [duration](../standard-library/duration-class.md) o [time_point](../standard-library/time-point-class.md) es menor o igual que otro objeto `duration` o `time_point`.  
  
```  
template <class Rep1, class Period1, class Rep2, class Period2>  
constexpr bool operator<=(
    const duration<Rep1, Period1>& Left,  
    const duration<Rep2, Period2>& Right);
 
template <class Clock, class Duration1, class Duration2>  
constexpr bool operator<=(
    const time_point<Clock, Duration1>& Left,  
    const time_point<Clock, Duration2>& Right);
```  
  
### <a name="parameters"></a>Parámetros  
 `Left`  
 Objeto `duration` o `time_point` izquierdo.  
  
 `Right`  
 Objeto `duration` o `time_point` derecho.  
  
### <a name="return-value"></a>Valor devuelto  
 Cada función devuelve `!(Right < Left)`.  
  
##  <a name="operator_eq_eq"></a>  operator==  
 Determina si dos objetos `duration` representan intervalos de tiempo de la misma longitud o si dos objetos `time_point` representan el mismo punto en el tiempo.  
  
```  
template <class Rep1, class Period1, class Rep2, class Period2>  
constexpr bool operator==(
    const duration<Rep1, Period1>& Left,  
    const duration<Rep2, Period2>& Right);
 
template <class Clock, class Duration1, class Duration2>  
constexpr bool operator==(
    const time_point<Clock, Duration1>& Left,  
    const time_point<Clock, Duration2>& Right);
```  
  
### <a name="parameters"></a>Parámetros  
 `Left`  
 Objeto `duration` o `time_point` izquierdo.  
  
 `Right`  
 Objeto `duration` o `time_point` derecho.  
  
### <a name="return-value"></a>Valor devuelto  
 La primera función devuelve `true` si `Left` y `Right` representan intervalos de tiempo que tienen la misma longitud. De lo contrario, la función devuelve `false`.  
  
 La segunda función devuelve `true` si `Left` y `Right` representan el mismo punto en el tiempo. De lo contrario, la función devuelve `false`.  
  
##  <a name="operator_gt_"></a>  operator&gt;  
 Determina si un objeto [duration](../standard-library/duration-class.md) o [time_point](../standard-library/time-point-class.md) es mayor que otro objeto `duration` o `time_point`.  
  
```  
template <class Rep1, class Period1, class Rep2, class Period2>  
constexpr bool operator>(
    const duration<Rep1, Period1>& Left,  
    const duration<Rep2, Period2>& Right);
 
template <class Clock, class Duration1, class Duration2>  
constexpr bool operator>(
    const time_point<Clock, Duration1>& Left,  
    const time_point<Clock, Duration2>& Right);
```  
  
### <a name="parameters"></a>Parámetros  
 `Left`  
 Objeto `duration` o `time_point` izquierdo.  
  
 `Right`  
 Objeto `duration` o `time_point` derecho.  
  
### <a name="return-value"></a>Valor devuelto  
 Cada función devuelve `Right < Left`.  
  
##  <a name="operator_gt__eq"></a>  operator&gt;=  
 Determina si un objeto [duration](../standard-library/duration-class.md) o [time_point](../standard-library/time-point-class.md) es mayor o igual que otro objeto `duration` o `time_point`.  
  
```  
template <class Rep1, class Period1, class Rep2, class Period2>  
constexpr bool operator>=(
    const duration<Rep1, Period1>& Left,  
    const duration<Rep2, Period2>& Right);
 
template <class Clock, class Duration1, class Duration2>  
constexpr bool operator>=(
    const time_point<Clock, Duration1>& Left,  
    const time_point<Clock, Duration2>& Right);
```  
  
### <a name="parameters"></a>Parámetros  
 `Left`  
 Objeto `duration` o `time_point` izquierdo.  
  
 `Right`  
 Objeto `duration` o `time_point` derecho.  
  
### <a name="return-value"></a>Valor devuelto  
 Cada función devuelve `!(Left < Right)`.  
  
##  <a name="operator_modulo"></a>  operator modulo  
 Operador para operaciones de módulo en objetos [duration](../standard-library/duration-class.md).  
  
```  
template <class Rep1, class Period1, class Rep2>  
constexpr duration<Rep1, Period1, Rep2>::type 
   operator%(
      const duration<Rep1, Period1>& Dur,  
      const Rep2& Div);

template <class Rep1, class Period1, class Rep2, class Period2>  
constexpr typename common_type<duration<Rep1, _Period1>, duration<Rep2, Period2>>::type
   operator%(
     const duration<Rep1, Period1>& Left,  
     const duration<Rep2, Period2>& Right);
```  
  
### <a name="parameters"></a>Parámetros  
 `Dur`  
 Objeto `duration`.  
  
 `Div`  
 Valor entero.  
  
 `Left`  
 Objeto `duration` izquierdo.  
  
 `Right`  
 Objeto `duration` derecho.  
  
### <a name="return-value"></a>Valor devuelto  
 La primera función devuelve un objeto `duration` cuya longitud del intervalo es el módulo `Div` de `Dur`.  
  
 La segunda función devuelve un valor que representa el módulo `Right` de `Left`.  
  
## <a name="see-also"></a>Vea también  
 [\<chrono>](../standard-library/chrono.md)


