---
title: numeric_limits (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- numeric_limits
- limits/std::numeric_limits
- limits/std::numeric_limits::denorm_min
- limits/std::numeric_limits::digits
- limits/std::numeric_limits::digits10
- limits/std::numeric_limits::epsilon
- limits/std::numeric_limits::has_denorm
- limits/std::numeric_limits::has_denorm_loss
- limits/std::numeric_limits::has_infinity
- limits/std::numeric_limits::has_quiet_NaN
- limits/std::numeric_limits::has_signaling_NaN
- limits/std::numeric_limits::infinity
- limits/std::numeric_limits::is_bounded
- limits/std::numeric_limits::is_exact
- limits/std::numeric_limits::is_iec559
- limits/std::numeric_limits::is_integer
- limits/std::numeric_limits::is_modulo
- limits/std::numeric_limits::is_signed
- limits/std::numeric_limits::is_specialized
- limits/std::numeric_limits::lowest
- limits/std::numeric_limits::max
- limits/std::numeric_limits::max_digits10
- limits/std::numeric_limits::max_exponent
- limits/std::numeric_limits::max_exponent10
- limits/std::numeric_limits::min
- limits/std::numeric_limits::min_exponent
- limits/std::numeric_limits::min_exponent10
- limits/std::numeric_limits::quiet_NaN
- limits/std::numeric_limits::radix
- limits/std::numeric_limits::round_error
- limits/std::numeric_limits::round_style
- limits/std::numeric_limits::signaling_NaN
- limits/std::numeric_limits::tinyness_before
- limits/std::numeric_limits::traps
dev_langs:
- C++
helpviewer_keywords:
- numeric_limits class
ms.assetid: 9e817177-0e91-48e6-b680-0531c4b26625
caps.latest.revision: 26
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 87b1be7f31a8f28425dc80f16ed60528f811ad32
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="numericlimits-class"></a>numeric_limits (Clase)
La clase de plantilla describe propiedades aritméticas de tipos numéricos integrados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Type>  
class numeric_limits  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Type`  
 Tipo de datos del elemento fundamental cuyas propiedades se están probando, consultando o estableciendo.  
  
## <a name="remarks"></a>Comentarios  
 El encabezado define especializaciones explícitas para los tipos `wchar_t`, `bool`, `char`, `signed char`, `unsigned char`, `short`, `unsigned short`, `int`, `unsigned int`, `long`, `unsigned long`, `float`, `double`, `long double`**,** `long long`, `unsigned long long`, `char16_t`y `char32_t`. Para estas especializaciones explícitas, el miembro [numeric_limits::is_specialized](#is_specialized) es `true` y todos los miembros pertinentes tienen valores significativos. El programa puede proporcionar especializaciones explícitas adicionales. La mayoría de las funciones miembro de la clase describen o prueban implementaciones posibles de `float`.  
  
 Para una especialización arbitraria, ningún miembro tiene valores significativos. Un objeto de miembro que no tiene un valor significativo almacena cero (o `false`) y una función miembro que no devuelve un valor significativo devuelve `Type(0)`.  
  
### <a name="static-functions-and-constants"></a>Constantes y funciones estáticas  
  
|||  
|-|-|  
|[denorm_min](#denorm_min)|Devuelve el valor más pequeño distinto de cero desnormalizado.|  
|[digits](#digits)|Devuelve el número de dígitos de base que el tipo puede representar sin pérdida de precisión.|  
|[digits10](#digits10)|Devuelve el número de dígitos decimales que el tipo puede representar sin pérdida de precisión.|  
|[epsilon](#epsilon)|Devuelve la diferencia entre 1 y el valor más pequeño mayor que 1, que el tipo de datos puede representar.|  
|[has_denorm](#has_denorm)|Comprueba si un tipo permite valores no normalizados.|  
|[has_denorm_loss](#has_denorm_loss)|Comprueba si se detecta la pérdida de precisión como una pérdida de desnormalización en lugar de como un resultado inexacto.|  
|[has_infinity](#has_infinity)|Comprueba si un tipo tiene una representación de infinito positivo.|  
|[has_quiet_NaN](#has_quiet_nan)|Comprueba si un tipo tiene una representación para un NaN (no es un número) silencioso, que no sea de señalización.|  
|[has_signaling_NaN](#has_signaling_nan)|Comprueba si un tipo tiene una representación para un NaN (no es un número) de señalización.|  
|[infinity](#infinity)|Representación de infinito positivo de un tipo, si está disponible.|  
|[is_bounded](#is_bounded)|Comprueba si el conjunto de valores que un tipo puede representar es finito.|  
|[is_exact](#is_exact)|Comprueba si los cálculos realizados en un tipo están libres de errores de redondeo.|  
|[is_iec559](#is_iec559)|Comprueba si un tipo se ajusta a los estándares IEC 559.|  
|[is_integer](#is_integer)|Comprueba si un tipo tiene una representación de entero.|  
|[is_modulo](#is_modulo)|Comprueba si un tipo tiene una representación de módulo.|  
|[is_signed](#is_signed)|Comprueba si un tipo tiene una representación con signo.|  
|[is_specialized](#is_specialized)|Comprueba si un tipo tiene una especialización explícita definida en la clase de plantilla `numeric_limits`.|  
|[lowest](#lowest)|Devuelve el mayor valor finito negativo.|  
|[max](#max)|Devuelve el valor finito máximo para un tipo.|  
|[max_digits10](#max_digits10)|Devuelve el número de dígitos decimales necesarios para asegurarse de que dos valores distintos del tipo tengan distintas representaciones decimales.|  
|[max_exponent](#max_exponent)|Devuelve el exponente integral positivo máximo que el tipo de punto flotante puede representar como valor finito cuando se eleva una base de base a esa potencia.|  
|[max_exponent10](#max_exponent10)|Devuelve el exponente integral positivo máximo que puede representar el tipo de punto flotante como valor finito cuando se eleva una base de diez a esa potencia.|  
|[min](#min)|Devuelve el valor normalizado mínimo para un tipo.|  
|[min_exponent](#min_exponent)|Devuelve el exponente integral negativo máximo que puede representar el tipo de punto flotante como valor finito cuando se eleva una base de base a esa potencia.|  
|[min_exponent10](#min_exponent10)|Devuelve el exponente integral negativo máximo que puede representar el tipo de punto flotante como valor finito cuando se eleva una base de diez a esa potencia.|  
|[quiet_NaN](#quiet_nan)|Devuelve la representación de un NaN (no es un número) silencioso para el tipo.|  
|[radix](#radix)|Devuelve la base integral, llamada base, usada para la representación de un tipo.|  
|[round_error](#round_error)|Devuelve el error de redondeo máximo para el tipo.|  
|[round_style](#round_style)|Devuelve un valor que describe los diversos métodos que una implementación puede elegir para redondear un valor de punto flotante a un valor entero.|  
|[signaling_NaN](#signaling_nan)|Devuelve la representación de un NaN (no es un número) de señalización para el tipo.|  
|[tinyness_before](#tinyness_before)|Comprueba si un tipo puede determinar que un valor es demasiado pequeño para representarse como un valor normalizado antes de redondearlo.|  
|[traps](#traps)|Comprueba si la captura que informa sobre excepciones aritméticas está implementada para un tipo.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<limits>  
  
 **Espacio de nombres:** std  
  
##  <a name="denorm_min"></a> numeric_limits::denorm_min  
 Devuelve el valor más pequeño distinto de cero desnormalizado.  
  
```  
static Type denorm_min() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor más pequeño distinto de cero desnormalizado.  
  
### <a name="remarks"></a>Comentarios  
 `long double` es igual que **double** para el compilador de C++.  
  
 La función devuelve el valor mínimo para el tipo, que es el mismo que [min](#min) si [has_denorm](#has_denorm) no es igual a **denorm_present**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_denorm_min.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "The smallest nonzero denormalized value\n for float "  
        << "objects is: " << numeric_limits<float>::denorm_min( )   
        << endl;  
   cout << "The smallest nonzero denormalized value\n for double "  
        << "objects is: " << numeric_limits<double>::denorm_min( )   
        << endl;  
   cout << "The smallest nonzero denormalized value\n for long double "  
        << "objects is: " << numeric_limits<long double>::denorm_min( )   
        << endl;  
  
   // A smaller value will round to zero  
   cout << numeric_limits<float>::denorm_min( )/2 <<endl;  
   cout << numeric_limits<double>::denorm_min( )/2 <<endl;  
   cout << numeric_limits<long double>::denorm_min( )/2 <<endl;  
}  
```  
  
```Output  
The smallest nonzero denormalized value  
 for float objects is: 1.4013e-045  
The smallest nonzero denormalized value  
 for double objects is: 4.94066e-324  
The smallest nonzero denormalized value  
 for long double objects is: 4.94066e-324  
0  
0  
0  
```  
  
##  <a name="digits"></a> numeric_limits::digits  
 Devuelve el número de dígitos de base que el tipo puede representar sin pérdida de precisión.  
  
```  
static const int digits = 0;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de dígitos de base que el tipo puede representar sin pérdida de precisión.  
  
### <a name="remarks"></a>Comentarios  
 El miembro almacena el número de dígitos de base que el tipo puede representar sin cambiar, que es el número de bits además de cualquier bit de signo para un tipo entero predefinido, o el número de dígitos de mantisa para un tipo de punto flotante predefinido.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_digits_min.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << numeric_limits<float>::digits <<endl;  
   cout << numeric_limits<double>::digits <<endl;  
   cout << numeric_limits<long double>::digits <<endl;  
   cout << numeric_limits<int>::digits <<endl;  
   cout << numeric_limits<__int64>::digits <<endl;  
}  
```  
  
```Output  
24  
53  
53  
31  
63  
```  
  
##  <a name="digits10"></a> numeric_limits::digits10  
 Devuelve el número de dígitos decimales que el tipo puede representar sin pérdida de precisión.  
  
```  
static const int digits10 = 0;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de dígitos decimales que el tipo puede representar sin pérdida de precisión.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_digits10.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << numeric_limits<float>::digits10 <<endl;  
   cout << numeric_limits<double>::digits10 <<endl;  
   cout << numeric_limits<long double>::digits10 <<endl;  
   cout << numeric_limits<int>::digits10 <<endl;  
   cout << numeric_limits<__int64>::digits10 <<endl;  
   float f = (float)99999999;  
   cout.precision ( 10 );  
   cout << "The float is; " << f << endl;  
}  
```  
  
```Output  
6  
15  
15  
9  
18  
The float is; 100000000  
```  
  
##  <a name="epsilon"></a> numeric_limits::epsilon  
 La función devuelve la diferencia entre 1 y el valor más pequeño mayor que 1, que el tipo de datos puede representar.  
  
```  
static Type epsilon() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La diferencia entre 1 y el valor más pequeño mayor que 1, que el tipo de datos puede representar.  
  
### <a name="remarks"></a>Comentarios  
 El valor es FLT_EPSILON para el tipo **float**. `epsilon` para un tipo es el número *N* de punto flotante positivo más pequeño de manera que *N* + `epsilon` + *N* se pueda representar.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_epsilon.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "The difference between 1 and the smallest "  
        << "value greater than 1\n for float objects is: "   
        << numeric_limits<float>::epsilon( )   
        << endl;  
   cout << "The difference between 1 and the smallest "  
        << "value greater than 1\n for double objects is: "   
        << numeric_limits<double>::epsilon( )   
        << endl;  
   cout << "The difference between 1 and the smallest "  
        << "value greater than 1\n for long double objects is: "   
        << numeric_limits<long double>::epsilon( )   
        << endl;  
}  
```  
  
```Output  
The difference between 1 and the smallest value greater than 1  
 for float objects is: 1.19209e-007  
The difference between 1 and the smallest value greater than 1  
 for double objects is: 2.22045e-016  
The difference between 1 and the smallest value greater than 1  
 for long double objects is: 2.22045e-016  
```  
  
##  <a name="has_denorm"></a> numeric_limits::has_denorm  
 Comprueba si un tipo permite valores no normalizados.  
  
```  
static const float_denorm_style has_denorm = denorm_absent;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de enumeración de tipo **const**`float_denorm_style`, que indica si el tipo permite valores desnormalizados.  
  
### <a name="remarks"></a>Comentarios  
 El miembro almacena **denorm_present** para un tipo de punto flotante que tiene valores desnormalizados, de manera eficaz, un número variable de bits de exponente.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_has_denorm.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "Whether float objects allow denormalized values: "  
        << numeric_limits<float>::has_denorm   
        << endl;  
   cout << "Whether double objects allow denormalized values: "  
        << numeric_limits<double>::has_denorm   
        << endl;  
   cout << "Whether long int objects allow denormalized values: "   
        << numeric_limits<long int>::has_denorm   
        << endl;  
}  
```  
  
```Output  
Whether float objects allow denormalized values: 1  
Whether double objects allow denormalized values: 1  
Whether long int objects allow denormalized values: 0  
```  
  
##  <a name="has_denorm_loss"></a> numeric_limits::has_denorm_loss  
 Comprueba si se detecta la pérdida de precisión como una pérdida de desnormalización en lugar de como un resultado inexacto.  
  
```  
static const bool has_denorm_loss = false;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si se detecta la pérdida de precisión como una pérdida de desnormalización; **False** si no es así.  
  
### <a name="remarks"></a>Comentarios  
 El miembro almacena True para un tipo que determina si un valor ha perdido precisión porque se entrega como un resultado desnormalizado (demasiado pequeño para representarse como un valor normalizado) o porque no es exacto (no es igual que un resultado no sujeto a las limitaciones de intervalo de exponente y precisión), una opción con representaciones de punto flotante IEC 559 que puede afectar a algunos resultados.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_has_denorm_loss.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "Whether float objects can detect denormalized loss: "  
        << numeric_limits<float>::has_denorm_loss  
        << endl;  
   cout << "Whether double objects can detect denormalized loss: "  
        << numeric_limits<double>::has_denorm_loss  
        << endl;  
   cout << "Whether long int objects can detect denormalized loss: "   
        << numeric_limits<long int>::has_denorm_loss  
        << endl;  
}  
```  
  
```Output  
Whether float objects can detect denormalized loss: 1  
Whether double objects can detect denormalized loss: 1  
Whether long int objects can detect denormalized loss: 0  
```  
  
##  <a name="has_infinity"></a> numeric_limits::has_infinity  
 Comprueba si un tipo tiene una representación de infinito positivo.  
  
```  
static const bool has_infinity = false;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si el tipo tiene una representación de infinito positivo; **False** si no es así.  
  
### <a name="remarks"></a>Comentarios  
 El miembro devuelve **True** si [is_iec559](#is_iec559) es **True**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_has_infinity.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "Whether float objects have infinity: "  
        << numeric_limits<float>::has_infinity  
        << endl;  
   cout << "Whether double objects have infinity: "  
        << numeric_limits<double>::has_infinity  
        << endl;  
   cout << "Whether long int objects have infinity: "   
        << numeric_limits<long int>::has_infinity  
        << endl;  
}  
```  
  
```Output  
Whether float objects have infinity: 1  
Whether double objects have infinity: 1  
Whether long int objects have infinity: 0  
```  
  
##  <a name="has_quiet_nan"></a> numeric_limits::has_quiet_NaN  
 Comprueba si un tipo tiene una representación para un NaN (no es un número) silencioso, que no sea de señalización.  
  
```  
static const bool has_quiet_NaN = false;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si el **tipo** tiene una representación para un NaN silencioso; **False** si no es así.  
  
### <a name="remarks"></a>Comentarios  
 Un NaN silencioso es una codificación, para no es un número, que no indica su presencia en una expresión. El valor devuelto es **True** si [is_iec559](#is_iec559) es True.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_has_quiet_nan.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "Whether float objects have quiet_NaN: "  
        << numeric_limits<float>::has_quiet_NaN   
        << endl;  
   cout << "Whether double objects have quiet_NaN: "  
        << numeric_limits<double>::has_quiet_NaN   
        << endl;  
   cout << "Whether long int objects have quiet_NaN: "   
        << numeric_limits<long int>::has_quiet_NaN   
        << endl;  
}  
```  
  
```Output  
Whether float objects have quiet_NaN: 1  
Whether double objects have quiet_NaN: 1  
Whether long int objects have quiet_NaN: 0  
```  
  
##  <a name="has_signaling_nan"></a> numeric_limits::has_signaling_NaN  
 Comprueba si un tipo tiene una representación para un NaN (no es un número) de señalización.  
  
```  
static const bool has_signaling_NaN = false;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si el tipo tiene una representación para un NAN de señalización; **False** si no es así.  
  
### <a name="remarks"></a>Comentarios  
 Un NaN de señalización es una codificación, para no es un número, que indica su presencia en una expresión. El valor devuelto es **True**[is_iec559](#is_iec559) es True.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_has_signaling_nan.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "Whether float objects have a signaling_NaN: "  
        << numeric_limits<float>::has_signaling_NaN   
        << endl;  
   cout << "Whether double objects have a signaling_NaN: "  
        << numeric_limits<double>::has_signaling_NaN   
        << endl;  
   cout << "Whether long int objects have a signaling_NaN: "   
        << numeric_limits<long int>::has_signaling_NaN   
        << endl;  
}  
```  
  
```Output  
Whether float objects have a signaling_NaN: 1  
Whether double objects have a signaling_NaN: 1  
Whether long int objects have a signaling_NaN: 0  
```  
  
##  <a name="infinity"></a> numeric_limits::infinity  
 La representación de infinito positivo de un tipo, si está disponible.  
  
```  
static Type infinity() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La representación de infinito positivo de un tipo, si está disponible.  
  
### <a name="remarks"></a>Comentarios  
 El valor devuelto solo es significativo si [has_infinity](#has_infinity) es **True**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_infinity.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << numeric_limits<float>::has_infinity <<endl;  
   cout << numeric_limits<double>::has_infinity<<endl;  
   cout << numeric_limits<long double>::has_infinity <<endl;  
   cout << numeric_limits<int>::has_infinity <<endl;  
   cout << numeric_limits<__int64>::has_infinity <<endl;  
  
   cout << "The representation of infinity for type float is: "  
        << numeric_limits<float>::infinity( ) <<endl;  
   cout << "The representation of infinity for type double is: "  
        << numeric_limits<double>::infinity( ) <<endl;  
   cout << "The representation of infinity for type long double is: "  
        << numeric_limits<long double>::infinity( ) <<endl;  
}  
```  
  
```Output  
1  
1  
1  
0  
0  
The representation of infinity for type float is: 1.#INF  
The representation of infinity for type double is: 1.#INF  
The representation of infinity for type long double is: 1.#INF  
```  
  
##  <a name="is_bounded"></a> numeric_limits::is_bounded  
 Comprueba si el conjunto de valores que un tipo puede representar es finito.  
  
```  
static const bool is_bounded = false;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si el tipo tiene un conjunto limitado de valores representables; **False** si no es así.  
  
### <a name="remarks"></a>Comentarios  
 Todos los tipos predefinidos tienen un conjunto limitado de valores representables y devuelven **True**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_is_bounded.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "Whether float objects have bounded set "  
        << "of representable values: "  
        << numeric_limits<float>::is_bounded  
        << endl;  
   cout << "Whether double objects have bounded set "  
        << "of representable values: "  
        << numeric_limits<double>::is_bounded  
        << endl;  
   cout << "Whether long int objects have bounded set "  
        << "of representable values: "  
        << numeric_limits<long int>::is_bounded  
        << endl;  
   cout << "Whether unsigned char objects have bounded set "  
        << "of representable values: "  
        << numeric_limits<unsigned char>::is_bounded  
        << endl;  
}  
```  
  
```Output  
Whether float objects have bounded set of representable values: 1  
Whether double objects have bounded set of representable values: 1  
Whether long int objects have bounded set of representable values: 1  
Whether unsigned char objects have bounded set of representable values: 1  
```  
  
##  <a name="is_exact"></a> numeric_limits::is_exact  
 Comprueba si los cálculos realizados en un tipo están libres de errores de redondeo.  
  
```  
static const bool is_exact = false;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si los cálculos están libres de errores de redondeo; **False** si no es así.  
  
### <a name="remarks"></a>Comentarios  
 Todos los tipos de enteros predefinidos tienen representaciones exactas para sus valores y devuelven **False**. Un punto fijo o una representación racional también se considera exacta, pero una representación de punto flotante no lo es.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_is_exact.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "Whether float objects have calculations "  
        << "free of rounding errors: "  
        << numeric_limits<float>::is_exact  
        << endl;  
   cout << "Whether double objects have calculations "  
        << "free of rounding errors: "  
        << numeric_limits<double>::is_exact  
        << endl;  
   cout << "Whether long int objects have calculations "  
        << "free of rounding errors: "  
        << numeric_limits<long int>::is_exact  
        << endl;  
   cout << "Whether unsigned char objects have calculations "  
        << "free of rounding errors: "  
        << numeric_limits<unsigned char>::is_exact  
        << endl;  
}  
```  
  
```Output  
Whether float objects have calculations free of rounding errors: 0  
Whether double objects have calculations free of rounding errors: 0  
Whether long int objects have calculations free of rounding errors: 1  
Whether unsigned char objects have calculations free of rounding errors: 1  
```  
  
##  <a name="is_iec559"></a> numeric_limits::is_iec559  
 Comprueba si un tipo se ajusta a los estándares IEC 559.  
  
```  
static const bool is_iec559 = false;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si el tipo se ajusta a los estándares IEC 559; **False** si no es así.  
  
### <a name="remarks"></a>Comentarios  
 IEC 559 es un estándar internacional para representar valores de punto flotante y también se conoce como IEEE 754 en EE. UU.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_is_iec559.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "Whether float objects conform to iec559 standards: "  
        << numeric_limits<float>::is_iec559  
        << endl;  
   cout << "Whether double objects conform to iec559 standards: "  
        << numeric_limits<double>::is_iec559  
        << endl;  
   cout << "Whether int objects conform to iec559 standards: "  
        << numeric_limits<int>::is_iec559  
        << endl;  
   cout << "Whether unsigned char objects conform to iec559 standards: "  
        << numeric_limits<unsigned char>::is_iec559  
        << endl;  
}  
```  
  
```Output  
Whether float objects conform to iec559 standards: 1  
Whether double objects conform to iec559 standards: 1  
Whether int objects conform to iec559 standards: 0  
Whether unsigned char objects conform to iec559 standards: 0  
```  
  
##  <a name="is_integer"></a> numeric_limits::is_integer  
 Comprueba si un tipo tiene una representación de entero.  
  
```  
static const bool is_integer = false;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si el tipo tiene una representación de entero; **False** si no es así.  
  
### <a name="remarks"></a>Comentarios  
 Todos los tipos de entero predefinidos tienen una representación de entero.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_is_integer.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "Whether float objects have an integral representation: "  
        << numeric_limits<float>::is_integer  
        << endl;  
   cout << "Whether double objects have an integral representation: "  
        << numeric_limits<double>::is_integer  
        << endl;  
   cout << "Whether int objects have an integral representation: "  
        << numeric_limits<int>::is_integer  
        << endl;  
   cout << "Whether unsigned char objects have an integral representation: "  
        << numeric_limits<unsigned char>::is_integer  
        << endl;  
}  
```  
  
```Output  
Whether float objects have an integral representation: 0  
Whether double objects have an integral representation: 0  
Whether int objects have an integral representation: 1  
Whether unsigned char objects have an integral representation: 1  
```  
  
##  <a name="is_modulo"></a> numeric_limits::is_modulo  
 Comprueba si un **tipo** tiene una representación de módulo.  
  
```  
static const bool is_modulo = false;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si el tipo tiene una representación de módulo; **False** si no es así.  
  
### <a name="remarks"></a>Comentarios  
 Una representación de módulo es una representación donde todos los resultados son valores de módulo reducidos. Todos los tipos de entero sin signo predefinidos tienen una representación de módulo.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_is_modulo.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "Whether float objects have a modulo representation: "  
        << numeric_limits<float>::is_modulo  
        << endl;  
   cout << "Whether double objects have a modulo representation: "  
        << numeric_limits<double>::is_modulo  
        << endl;  
   cout << "Whether signed char objects have a modulo representation: "  
        << numeric_limits<signed char>::is_modulo  
        << endl;  
   cout << "Whether unsigned char objects have a modulo representation: "  
        << numeric_limits<unsigned char>::is_modulo  
        << endl;  
}  
```  
  
```Output  
Whether float objects have a modulo representation: 0  
Whether double objects have a modulo representation: 0  
Whether signed char objects have a modulo representation: 1  
Whether unsigned char objects have a modulo representation: 1  
```  
  
##  <a name="is_signed"></a> numeric_limits::is_signed  
 Comprueba si un tipo tiene una representación con signo.  
  
```  
static const bool is_signed = false;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si el tipo tiene una representación con signo; **False** si no es así.  
  
### <a name="remarks"></a>Comentarios  
 El miembro almacena True para un tipo que tiene una representación con signo, que es el caso de todos los tipos de entero con signo y de punto flotante predefinidos.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_is_signaled.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "Whether float objects have a signed representation: "  
        << numeric_limits<float>::is_signed  
        << endl;  
   cout << "Whether double objects have a signed representation: "  
        << numeric_limits<double>::is_signed  
        << endl;  
   cout << "Whether signed char objects have a signed representation: "  
        << numeric_limits<signed char>::is_signed  
        << endl;  
   cout << "Whether unsigned char objects have a signed representation: "  
        << numeric_limits<unsigned char>::is_signed  
        << endl;  
}  
```  
  
```Output  
Whether float objects have a signed representation: 1  
Whether double objects have a signed representation: 1  
Whether signed char objects have a signed representation: 1  
Whether unsigned char objects have a signed representation: 0  
```  
  
##  <a name="is_specialized"></a> numeric_limits::is_specialized  
 Comprueba si un tipo tiene una especialización explícita definida en la clase de plantilla `numeric_limits`.  
  
```  
static const bool is_specialized = false;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si el tipo tiene una especialización explícita definida en la clase de plantilla; **False** si no es así.  
  
### <a name="remarks"></a>Comentarios  
 Todos los tipos escalares distintos a los punteros tienen una especialización explícita definida para la clase de plantilla `numeric_limits`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_is_specialized.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "Whether float objects have an explicit "  
        << "specialization in the class: "  
        << numeric_limits<float>::is_specialized  
        << endl;  
   cout << "Whether float* objects have an explicit "  
        << "specialization in the class: "  
        << numeric_limits<float*>::is_specialized  
        << endl;  
   cout << "Whether int objects have an explicit "  
        << "specialization in the class: "  
        << numeric_limits<int>::is_specialized  
        << endl;  
   cout << "Whether int* objects have an explicit "  
        << "specialization in the class: "  
        << numeric_limits<int*>::is_specialized  
        << endl;  
}  
```  
  
```Output  
Whether float objects have an explicit specialization in the class: 1  
Whether float* objects have an explicit specialization in the class: 0  
Whether int objects have an explicit specialization in the class: 1  
Whether int* objects have an explicit specialization in the class: 0  
```  
  
##  <a name="lowest"></a> numeric_limits::lowest  
 Devuelve el mayor valor finito negativo.  
  
```  
static Type lowest() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el mayor valor finito negativo.  
  
### <a name="remarks"></a>Comentarios  
 Devuelve el mayor valor finito negativo para el tipo (que suele ser `min` `()` para los tipos enteros y `-``max` `()` para los tipos de punto flotante). El valor devuelto es significativo si `is_bounded` es `true`.  
  
##  <a name="max"></a> numeric_limits::max  
 Devuelve el valor finito máximo para un tipo.  
  
```  
static Type max() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor finito máximo para un tipo.  
  
### <a name="remarks"></a>Comentarios  
 El valor finito máximo es INT_MAX para el tipo `int` y FLT_MAX para el tipo **float**. El valor devuelto es significativo si [is_bounded](#is_bounded) es **True**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_max.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main() {  
   cout << "The maximum value for type float is:  "  
        << numeric_limits<float>::max( )  
        << endl;  
   cout << "The maximum value for type double is:  "  
        << numeric_limits<double>::max( )  
        << endl;  
   cout << "The maximum value for type int is:  "  
        << numeric_limits<int>::max( )  
        << endl;  
   cout << "The maximum value for type short int is:  "  
        << numeric_limits<short int>::max( )  
        << endl;  
}  
```  
  
##  <a name="max_digits10"></a> numeric_limits::max_digits10  
 Devuelve el número de dígitos decimales necesarios para asegurarse de que dos valores distintos del tipo tengan distintas representaciones decimales.  
  
```  
static int max_digits10 = 0;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de dígitos decimales necesarios para asegurarse de que dos valores distintos del tipo tengan distintas representaciones decimales.  
  
### <a name="remarks"></a>Comentarios  
 El miembro almacena el número de dígitos decimales necesarios para asegurarse de que dos valores distintos del tipo tengan distintas representaciones decimales.  
  
##  <a name="max_exponent"></a> numeric_limits::max_exponent  
 Devuelve el exponente integral positivo máximo que el tipo de punto flotante puede representar como valor finito cuando se eleva una base de base a esa potencia.  
  
```  
static const int max_exponent = 0;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El máximo exponente basado en la base integral que se representa mediante el tipo.  
  
### <a name="remarks"></a>Comentarios  
 El valor devuelto de la función miembro es significativo solo para los tipos de punto flotante. El `max_exponent` es el valor FLT_MAX_EXP para el tipo **float**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_max_exponent.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "The maximum radix-based exponent for type float is:  "  
        << numeric_limits<float>::max_exponent  
        << endl;  
   cout << "The maximum radix-based exponent for type double is:  "  
        << numeric_limits<double>::max_exponent  
        << endl;  
   cout << "The maximum radix-based exponent for type long double is:  "  
        << numeric_limits<long double>::max_exponent  
        << endl;  
}  
```  
  
```Output  
The maximum radix-based exponent for type float is:  128  
The maximum radix-based exponent for type double is:  1024  
The maximum radix-based exponent for type long double is:  1024  
```  
  
##  <a name="max_exponent10"></a> numeric_limits::max_exponent10  
 Devuelve el exponente integral positivo máximo que puede representar el tipo de punto flotante como valor finito cuando se eleva una base de diez a esa potencia.  
  
```  
static const int max_exponent10 = 0;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El máximo exponente de base 10 integral que se representa mediante el tipo.  
  
### <a name="remarks"></a>Comentarios  
 El valor devuelto de la función miembro es significativo solo para los tipos de punto flotante. El `max_exponent` es el valor FLT_MAX_10 para el tipo **float**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_max_exponent10.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "The maximum base 10 exponent for type float is:  "  
           << numeric_limits<float>::max_exponent10  
           << endl;  
   cout << "The maximum base 10 exponent for type double is:  "  
           << numeric_limits<double>::max_exponent10  
           << endl;  
   cout << "The maximum base 10 exponent for type long double is:  "  
           << numeric_limits<long double>::max_exponent10  
           << endl;  
}  
```  
  
```Output  
The maximum base 10 exponent for type float is:  38  
The maximum base 10 exponent for type double is:  308  
The maximum base 10 exponent for type long double is:  308  
```  
  
##  <a name="min"></a> numeric_limits::min  
 Devuelve el valor normalizado mínimo para un tipo.  
  
```  
static Type min() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor normalizado mínimo para el tipo.  
  
### <a name="remarks"></a>Comentarios  
 El valor normalizado mínimo es INT_MIN para el tipo `int` y FLT_MIN para el tipo `float`. El valor devuelto es significativo si [is_bounded](#is_bounded) es `true` o si [is_signed](#is_signed) es `false`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_min.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "The minimum value for type float is:  "  
        << numeric_limits<float>::min( )  
        << endl;  
   cout << "The minimum value for type double is:  "  
        << numeric_limits<double>::min( )  
        << endl;  
   cout << "The minimum value for type int is:  "  
        << numeric_limits<int>::min( )  
        << endl;  
   cout << "The minimum value for type short int is:  "  
        << numeric_limits<short int>::min( )  
        << endl;  
}  
```  
  
```Output  
The minimum value for type float is:  1.17549e-038  
The minimum value for type double is:  2.22507e-308  
The minimum value for type int is:  -2147483648  
The minimum value for type short int is:  -32768  
```  
  
##  <a name="min_exponent"></a> numeric_limits::min_exponent  
 Devuelve el exponente integral negativo máximo que puede representar el tipo de punto flotante como valor finito cuando se eleva una base de base a esa potencia.  
  
```  
static const int min_exponent = 0;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El mínimo exponente basado en la base integral que se representa mediante el tipo.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro es significativa solo para los tipos de punto flotante. El `min_exponent` es el valor FLT_MIN_EXP para el tipo **float**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_min_exponent.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "The minimum radix-based exponent for type float is:  "  
        << numeric_limits<float>::min_exponent  
        << endl;  
   cout << "The minimum radix-based exponent for type double is:  "  
        << numeric_limits<double>::min_exponent  
        << endl;  
   cout << "The minimum radix-based exponent for type long double is:  "  
         << numeric_limits<long double>::min_exponent  
        << endl;  
}  
```  
  
```Output  
The minimum radix-based exponent for type float is:  -125  
The minimum radix-based exponent for type double is:  -1021  
The minimum radix-based exponent for type long double is:  -1021  
```  
  
##  <a name="min_exponent10"></a> numeric_limits::min_exponent10  
 Devuelve el exponente integral negativo máximo que puede representar el tipo de punto flotante como valor finito cuando se eleva una base de diez a esa potencia.  
  
```  
static const int min_exponent10 = 0;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El mínimo exponente de base 10 integral que se representa mediante el tipo.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro es significativa solo para los tipos de punto flotante. El `min_exponent10` es el valor FLT_MIN_10_EXP para el tipo **float**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_min_exponent10.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "The minimum base 10 exponent for type float is:  "  
        << numeric_limits<float>::min_exponent10  
        << endl;  
   cout << "The minimum base 10 exponent for type double is:  "  
        << numeric_limits<double>::min_exponent10  
        << endl;  
   cout << "The minimum base 10 exponent for type long double is:  "  
        << numeric_limits<long double>::min_exponent10  
        << endl;  
}  
```  
  
```Output  
The minimum base 10 exponent for type float is:  -37  
The minimum base 10 exponent for type double is:  -307  
The minimum base 10 exponent for type long double is:  -307  
```  
  
##  <a name="quiet_nan"></a> numeric_limits::quiet_NaN  
 Devuelve la representación de un NaN (no es un número) silencioso para el tipo.  
  
```  
static Type quiet_NaN() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La representación de un NaN silencioso para el tipo.  
  
### <a name="remarks"></a>Comentarios  
 El valor devuelto solo es significativo si [has_quiet_NaN](#has_quiet_nan) es **True**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_quiet_nan.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "The quiet NaN for type float is:  "  
        << numeric_limits<float>::quiet_NaN( )  
        << endl;  
   cout << "The quiet NaN for type int is:  "  
        << numeric_limits<int>::quiet_NaN( )  
        << endl;  
   cout << "The quiet NaN for type long double is:  "  
        << numeric_limits<long double>::quiet_NaN( )  
        << endl;  
}  
```  
  
```Output  
The quiet NaN for type float is:  1.#QNAN  
The quiet NaN for type int is:  0  
The quiet NaN for type long double is:  1.#QNAN  
```  
  
##  <a name="radix"></a> numeric_limits::radix  
 Devuelve la base integral, llamada base, usada para la representación de un tipo.  
  
```  
static const int radix = 0;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La base integral para la representación del tipo.  
  
### <a name="remarks"></a>Comentarios  
 La base es 2 para los tipos enteros predefinidos, y la base a la que se eleva el exponente, o FLT_RADIX, para los tipos de punto flotante predefinidos.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_radix.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "The base for type float is:  "  
        << numeric_limits<float>::radix  
        << endl;  
   cout << "The base for type int is:  "  
        << numeric_limits<int>::radix  
        << endl;  
   cout << "The base for type long double is:  "  
        << numeric_limits<long double>::radix  
        << endl;  
}  
```  
  
```Output  
The base for type float is:  2  
The base for type int is:  2  
The base for type long double is:  2  
```  
  
##  <a name="round_error"></a> numeric_limits::round_error  
 Devuelve el error de redondeo máximo para el tipo.  
  
```  
static Type round_error() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El error de redondeo máximo para el tipo.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_round_error.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "The maximum rounding error for type float is:  "  
        << numeric_limits<float>::round_error( )  
        << endl;  
   cout << "The maximum rounding error for type int is:  "  
        << numeric_limits<int>::round_error( )  
        << endl;  
   cout << "The maximum rounding error for type long double is:  "  
        << numeric_limits<long double>::round_error( )  
        << endl;  
}  
```  
  
```Output  
The maximum rounding error for type float is:  0.5  
The maximum rounding error for type int is:  0  
The maximum rounding error for type long double is:  0.5  
```  
  
##  <a name="round_style"></a> numeric_limits::round_style  
 Devuelve un valor que describe los diversos métodos que una implementación puede elegir para redondear un valor de punto flotante a un valor entero.  
  
```  
static const float_round_style round_style = round_toward_zero;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de la enumeración `float_round_style` que describe el estilo de redondeo.  
  
### <a name="remarks"></a>Comentarios  
 El miembro almacena un valor que describe los diversos métodos que una implementación puede elegir para redondear un valor de punto flotante a un valor entero.  
  
 El estilo de redondeo está codificado de forma rígida en esta implementación, por lo que aunque el programa se inicie con un modo de redondeo diferente, el valor no cambiará.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_round_style.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <float.h>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "The rounding style for a double type is: "   
        << numeric_limits<double>::round_style << endl;  
   _controlfp_s(NULL,_RC_DOWN,_MCW_RC );  
   cout << "The rounding style for a double type is now: "   
        << numeric_limits<double>::round_style << endl;  
   cout << "The rounding style for an int type is: "   
        << numeric_limits<int>::round_style << endl;  
}  
```  
  
```Output  
The rounding style for a double type is: 1  
The rounding style for a double type is now: 1  
The rounding style for an int type is: 0  
```  
  
##  <a name="signaling_nan"></a> numeric_limits::signaling_NaN  
 Devuelve la representación de un NaN (no es un número) de señalización para el tipo.  
  
```  
static Type signaling_NaN() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La representación de un NaN de señalización para el tipo.  
  
### <a name="remarks"></a>Comentarios  
 El valor devuelto solo es significativo si [has_signaling_NaN](#has_signaling_nan) es **True**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_signaling_nan.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "The signaling NaN for type float is:  "  
        << numeric_limits<float>::signaling_NaN( )  
        << endl;  
   cout << "The signaling NaN for type int is:  "  
        << numeric_limits<int>::signaling_NaN( )  
        << endl;  
   cout << "The signaling NaN for type long double is:  "  
        << numeric_limits<long double>::signaling_NaN( )  
        << endl;  
}  
```  
  
##  <a name="tinyness_before"></a> numeric_limits::tinyness_before  
 Comprueba si un tipo puede determinar que un valor es demasiado pequeño para representarse como un valor normalizado antes de redondearlo.  
  
```  
static const bool tinyness_before = false;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si el tipo puede detectar valores muy pequeños antes del redondeo; `false` si no puede.  
  
### <a name="remarks"></a>Comentarios  
 Los tipos que pueden detectar valores tinyness se han incluido como una opción con las representaciones de punto flotante IEC 559 y su implementación puede afectar a algunos resultados.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_tinyness_before.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "Whether float types can detect tinyness before rounding: "  
        << numeric_limits<float>::tinyness_before  
        << endl;  
   cout << "Whether double types can detect tinyness before rounding: "  
        << numeric_limits<double>::tinyness_before  
        << endl;  
   cout << "Whether long int types can detect tinyness before rounding: "  
        << numeric_limits<long int>::tinyness_before  
        << endl;  
   cout << "Whether unsigned char types can detect tinyness before rounding: "  
        << numeric_limits<unsigned char>::tinyness_before  
        << endl;  
}  
```  
  
```Output  
Whether float types can detect tinyness before rounding: 1  
Whether double types can detect tinyness before rounding: 1  
Whether long int types can detect tinyness before rounding: 0  
Whether unsigned char types can detect tinyness before rounding: 0  
```  
  
##  <a name="traps"></a> numeric_limits::traps  
 Comprueba si la captura que informa sobre excepciones aritméticas está implementada para un tipo.  
  
```  
static const bool traps = false;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si se implementa la captura para el tipo; **False** si no es así.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// numeric_limits_traps.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "Whether float types have implemented trapping: "  
        << numeric_limits<float>::traps  
        << endl;  
   cout << "Whether double types have implemented trapping: "  
        << numeric_limits<double>::traps  
        << endl;  
   cout << "Whether long int types have implemented trapping: "  
        << numeric_limits<long int>::traps  
        << endl;  
   cout << "Whether unsigned char types have implemented trapping: "  
        << numeric_limits<unsigned char>::traps  
        << endl;  
}  
```  
  
```Output  
Whether float types have implemented trapping: 1  
Whether double types have implemented trapping: 1  
Whether long int types have implemented trapping: 0  
Whether unsigned char types have implemented trapping: 0  
```  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)


