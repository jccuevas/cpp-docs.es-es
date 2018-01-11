---
title: duration (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- chrono/std::chrono::duration
- chrono/std::chrono::duration::duration
- chrono/std::chrono::duration::count
- chrono/std::chrono::duration::max
- chrono/std::chrono::duration::min
- chrono/std::chrono::duration::zero
dev_langs: C++
ms.assetid: 06b863b3-65be-4ded-a72e-6e1eb1531077
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords: std::chrono [C++], duration
ms.workload: cplusplus
ms.openlocfilehash: e25b632554f56054793f60f3fe058791798894d2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="duration-class"></a>duration (Clase)
Describe un tipo que contiene un *intervalo de tiempo*, que es el tiempo transcurrido entre dos puntos en el tiempo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Rep, class Period = ratio<1>>  
class duration;  
template <class Rep, class Period>  
class duration;  
template <class Rep, class Period1, class Period2>  
class duration <duration<Rep, Period1>, Period2>;  
```  
  
## <a name="remarks"></a>Comentarios  
 El argumento de plantilla `Rep` describe el tipo que se utiliza para almacenar el número de ciclos de reloj del intervalo. El argumento de plantilla `Period` es una creación de instancias de [ratio](../standard-library/ratio.md) que describe el tamaño del intervalo que representa cada ciclo.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|duration::period (Typedef)|Representa un sinónimo para el parámetro de plantilla `Period`.|  
|duration::rep (Typedef)|Representa un sinónimo para el parámetro de plantilla `Rep`.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[duración](#duration)|Construye un objeto `duration`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[count](#count)|Devuelve el número de pasos del reloj del intervalo de tiempo.|  
|[max](#max)|Estático. Devuelve el valor máximo permitido del parámetro de plantilla `Ref`.|  
|[min](#min)|Estático. Devuelve el valor mínimo permitido del parámetro de plantilla `Ref`.|  
|[cero](#zero)|Estático. En efecto, devuelve `Rep`(0).|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[duration::operator-](#operator-)|Devuelve una copia del objeto `duration` junto con un recuento de pasos negado.|  
|[duration::operator--](#operator--)|Disminuye el recuento de pasos almacenado.|  
|[duration::operator=](#op_eq)|Reduce el módulo del recuento de pasos almacenado en un valor especificado.|  
|[duration::operator*=](#op_star_eq)|Multiplica el recuento de pasos almacenado por un valor especificado.|  
|[duration::operator/=](#op_div_eq)|Divide el recuento de pasos almacenado por el recuento de pasos de un objeto `duration` especificado.|  
|[duration::operator+](#op_add)|Devuelve `*this`.|  
|[duration::operator++](#op_add_add)|Incrementa el recuento de pasos almacenado.|  
|[duration::operator+=](#op_add_eq)|Suma el recuento de pasos de un objeto `duration` especificado al recuento de pasos almacenado.|  
|[duration::operator-=](#operator-_eq)|Resta el recuento de pasos de un objeto `duration` especificado del recuento de pasos almacenado.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<chrono >  
  
 **Espacio de nombres:** std::chrono  
  
##  <a name="count"></a>  duration::count  
 Recupera el número de ciclos del reloj del intervalo de tiempo.  
  
```  
constexpr Rep count() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Número de ciclos del reloj del intervalo de tiempo.  
  
##  <a name="duration"></a>  duration::duration (Constructor)  
 Construye un objeto `duration`.  
  
```  
constexpr duration() = default;  
 
template <class Rep2>  
constexpr explicit duration(const Rep2& R);

 
template <class Rep2, class Period2>  
constexpr duration(const duration<Rep2, Period2>& Dur);
```  
  
### <a name="parameters"></a>Parámetros  
 `Rep2`  
 Un tipo aritmético para representar el número de ciclos.  
  
 `Period2`  
 Una especialización de plantilla `std::ratio` para representar el período de ciclo en unidades de segundos.  
  
 `R`  
 El número de ciclos del período predeterminado.  
  
 `Dur`  
 El número de ciclos del período especificado por `Period2`.  
  
### <a name="remarks"></a>Comentarios  
 El constructor predeterminado crea un objeto que no se ha inicializado. La inicialización de un valor mediante llaves vacías inicializa un objeto que representa un intervalo de tiempo de cero ciclos de reloj.  
  
 El segundo constructor de argumento de una plantilla crea un objeto que representa un intervalo de tiempo de `R` ciclos de reloj mediante un período predeterminado de `std::ratio<1>`. Para evitar el redondeo de los ciclos de reloj, es un error construir un objeto de duración a partir de un tipo de representación `Rep2` que se puede tratar como un tipo de punto flotante cuando `duration::rep` no se puede tratar como un tipo de punto flotante.  
  
 El tercer constructor de argumento de dos plantillas crea un objeto que representa un intervalo de tiempo cuya longitud es el intervalo de tiempo especificado por `Dur`. Para evitar el truncamiento de los ciclos de reloj, es un error construir un objeto de duración a partir de otro objeto de duración cuyo tipo es *inconmensurable* con el tipo de destino.  
  
 Un tipo de duración `D1` es *inconmensurable* con otro tipo de duración `D2` si `D2` no se puede tratar como un tipo de punto flotante y [ratio_divide\<D1::period, D2::period>::type::den](../standard-library/ratio.md) no es 1.  
  
 A menos que `Rep2` sea convertible de forma implícita a `rep` y `treat_as_floating_point<rep>`*sea True* o `treat_as_floating_point<Rep2>`*sea False*, el segundo constructor no participa en la resolución de sobrecarga. Para obtener más información, vea [<type_traits>](../standard-library/type-traits.md).  
  
 A menos que no se induzca ningún desbordamiento en la conversión y `treat_as_floating_point<rep>`*sea True* o ambos `ratio_divide<Period2, period>::den` sean iguales a 1 y `treat_as_floating_point<Rep2>`*sea False*, el tercer constructor no participa en la resolución de sobrecarga. Para obtener más información, vea [<type_traits>](../standard-library/type-traits.md).  
  
##  <a name="max"></a>  duration::max  
 Método estático que devuelve el límite superior para los valores de tipo de parámetro de plantilla `Ref`.  
  
```  
static constexpr duration max();
```  
  
### <a name="return-value"></a>Valor devuelto  
 En efecto, devuelve `duration(duration_values<rep>::max())`.  
  
##  <a name="min"></a>  duration::min  
 Método estático que devuelve el límite inferior para los valores de tipo de parámetro de plantilla `Ref`.  
  
```  
static constexpr duration min();
```  
  
### <a name="return-value"></a>Valor devuelto  
 En efecto, devuelve `duration(duration_values<rep>::min())`.  
  
##  <a name="duration__operator-"></a>  duration::operator-  
 Devuelve una copia del objeto `duration` junto con un recuento de pasos negado.  
  
```  
constexpr duration operator-() const;
```  
  
##  <a name="duration__operator--"></a>  duration::operator--  
 Disminuye el recuento de pasos almacenado.  
  
```  
duration& operator--();

duration operator--(int);
```  
  
### <a name="return-value"></a>Valor devuelto  
 El primer método devuelve `*this`.  
  
 El segundo método devuelve una copia de `*this` que se ha creado antes del decremento.  
  
##  <a name="op_eq"></a>  duration::operator=  
 Reduce el módulo del recuento de pasos almacenado en un valor especificado.  
  
```  
duration& operator%=(const rep& Div);

duration& operator%=(const duration& Div);
```  
  
### <a name="parameters"></a>Parámetros  
 `Div`  
 Para el primer método, `Div` representa un recuento de pasos. Para el segundo método, `Div` es un objeto `duration` que contiene un recuento de pasos.  
  
### <a name="return-value"></a>Valor devuelto  
 Objeto `duration` después de realizarse la operación de módulo.  
  
##  <a name="op_star_eq"></a>  duration::operator*=  
 Multiplica el recuento de pasos almacenado por un valor especificado.  
  
```  
duration& operator*=(const rep& Mult);
```  
  
### <a name="parameters"></a>Parámetros  
 `Mult`  
 Valor del tipo especificado por `duration::rep`.  
  
### <a name="return-value"></a>Valor devuelto  
 Objeto `duration` después del cual se realiza la multiplicación.  
  
##  <a name="op_div_eq"></a>  duration::operator/=  
 Divide el recuento de pasos almacenado por un valor especificado.  
  
```  
duration& operator/=(const rep& Div);
```  
  
### <a name="parameters"></a>Parámetros  
 `Div`  
 Valor del tipo especificado por `duration::rep`.  
  
### <a name="return-value"></a>Valor devuelto  
 Objeto `duration` después del cual se realiza la división.  
  
##  <a name="op_add"></a>  duration::operator+  
 Devuelve `*this`.  
  
```  
constexpr duration operator+() const;
```  
  
##  <a name="op_add_add"></a>  duration::operator++  
 Incrementa el recuento de pasos almacenado.  
  
```  
duration& operator++();

duration operator++(int);
```  
  
### <a name="return-value"></a>Valor devuelto  
 El primer método devuelve `*this`.  
  
 El segundo método devuelve una copia de `*this` que se hizo antes del incremento.  
  
##  <a name="op_add_eq"></a>  duration::operator+=  
 Suma el recuento de pasos de un objeto `duration` especificado al recuento de pasos almacenado.  
  
```  
duration& operator+=(const duration& Dur);
```  
  
### <a name="parameters"></a>Parámetros  
 `Dur`  
 Un objeto `duration`.  
  
### <a name="return-value"></a>Valor devuelto  
 Objeto `duration` después del cual se realiza la suma.  
  
##  <a name="duration__operator-_eq"></a>  duration::operator-=  
 Resta el recuento de pasos de un objeto `duration` especificado del recuento de pasos almacenado.  
  
```  
duration& operator-=(const duration& Dur);
```  
  
### <a name="parameters"></a>Parámetros  
 `Dur`  
 Un objeto `duration`.  
  
### <a name="return-value"></a>Valor devuelto  
 Objeto `duration` después del cual se realiza la resta.  
  
##  <a name="zero"></a>  duration::zero  
 Devuelve `duration(duration_values<rep>::zero())`.  
  
```  
static constexpr duration zero();
```  
  
##  <a name="op_mod_eq"></a>  duration::operator mod=  
 Reduce el módulo del recuento de pasos almacenado en Div o Div.count().  
  
```  
duration& operator%=(const rep& Div);duration& operator%=(const duration& Div);
```  
  
### <a name="parameters"></a>Parámetros  
 `Div`  
 El divisor, que es un objeto de duración o un valor que representa los recuentos de pasos.  
  
### <a name="remarks"></a>Comentarios  
 La primera función miembro reduce el módulo del recuento de pasos almacenado Div y devuelve *this. La segunda función miembro reduce el módulo del recuento de pasos almacenado Div.count() y devuelve \*this.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono>](../standard-library/chrono.md)   
 [duration_values (Estructura)](../standard-library/duration-values-structure.md)
