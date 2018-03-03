---
title: SafeInt (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SafeInt
dev_langs:
- C++
helpviewer_keywords:
- SafeInt class
ms.assetid: 27a8f087-2511-46f9-8d76-2aeb66ca272f
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ea076ea092257fd5bf6acd6d597f79ef42dd96f2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="safeint-class"></a>SafeInt (Clase)
Extiende las primitivas de entero para ayudar a evitar el desbordamiento de enteros y le permite comparar los diferentes tipos de enteros.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename T, typename E = _SAFEINT_DEFAULT_ERROR_POLICY>  
class SafeInt;  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Plantilla|Descripción|  
|--------------|-----------------|  
|T|El tipo de entero o un parámetro booleano que `SafeInt` reemplaza.|  
|E|Un tipo de datos enumerado que define la directiva de control de errores.|  
|U|El tipo de entero o un parámetro booleano para el operando secundario.|  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] rhs|Un parámetro de entrada que representa el valor en el lado derecho del operador en varias funciones independientes.|  
|[in]|Un parámetro de entrada que representa el valor en el lado derecho del operador en varias funciones independientes.|  
|[in] bits|Un parámetro de entrada que representa el valor en el lado derecho del operador en varias funciones independientes.|  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SafeInt::SafeInt](../windows/safeint-safeint.md)|Constructor predeterminado.|  
  
### <a name="assignment-operators"></a>Operadores de asignación  
  
|nombre|Sintaxis|  
|----------|------------|  
|=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator= (const U& rhs)`|  
|=|`SafeInt<T,E>& operator= (const T& rhs) throw()`|  
|=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator= (const SafeInt<U, E>& rhs)`|  
|=|`SafeInt<T,E>& operator= (const SafeInt<T,E>& rhs) throw()`|  
  
### <a name="casting-operators"></a>Operadores de conversión  
  
|nombre|Sintaxis|  
|----------|------------|  
|bool|`operator bool() throw()`|  
|char|`operator char() const`|  
|signed char|`operator signed char() const`|  
|unsigned char|`operator unsigned char() const`|  
|__int16|`operator __int16() const`|  
|unsigned __int16|`operator unsigned __int16() const`|  
|__int32|`operator __int32() const`|  
|unsigned __int32|`operator unsigned __int32() const`|  
|long|`operator long() const`|  
|unsigned long|`operator unsigned long() const`|  
|__int64|`operator __int64() const`|  
|unsigned __int64|`operator unsigned __int64() const`|  
|wchar_t|`operator wchar_t() const`|  
  
### <a name="comparison-operators"></a>Operadores de comparación  
  
|nombre|Sintaxis|  
|----------|------------|  
|<|`template<typename U>`<br /><br /> `bool operator< (U rhs) const throw()`|  
|<|`bool operator< (SafeInt<T,E> rhs) const throw()`|  
|>=|`template<typename U>`<br /><br /> `bool operator>= (U rhs) const throw()`|  
|>=|`Bool operator>= (SafeInt<T,E> rhs) const throw()`|  
|>|`template<typename U>`<br /><br /> `bool operator> (U rhs) const throw()`|  
|>|`Bool operator> (SafeInt<T,E> rhs) const throw()`|  
|<=|`template<typename U>`<br /><br /> `bool operator<= (U rhs) const throw()`|  
|<=|`bool operator<= (SafeInt<T,E> rhs) const throw()`|  
|==|`template<typename U>`<br /><br /> `bool operator== (U rhs) const throw()`|  
|==|`bool operator== (bool rhs) const throw()`|  
|==|`bool operator== (SafeInt<T,E> rhs) const throw()`|  
|!=|`template<typename U>`<br /><br /> `bool operator!= (U rhs) const throw()`|  
|!=|`bool operator!= (bool b) const throw()`|  
|!=|`bool operator!= (SafeInt<T,E> rhs) const throw()`|  
  
### <a name="arithmetic-operators"></a>Operadores aritméticos  
  
|nombre|Sintaxis|  
|----------|------------|  
|+|`const SafeInt<T,E>& operator+ () const throw()`|  
|-|`SafeInt<T,E> operator- () const`|  
|++|`SafeInt<T,E>& operator++ ()`|  
|--|`SafeInt<T,E>& operator-- ()`|  
|%|`template<typename U>`<br /><br /> `SafeInt<T,E> operator% (U rhs) const`|  
|%|`SafeInt<T,E> operator% (SafeInt<T,E> rhs) const`|  
|%=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (U rhs)`|  
|%=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (SafeInt<U, E> rhs)`|  
|*|`template<typename U>`<br /><br /> `SafeInt<T,E> operator* (U rhs) const`|  
|*|`SafeInt<T,E> operator* (SafeInt<T,E> rhs) const`|  
|*=|`SafeInt<T,E>& operator*= (SafeInt<T,E> rhs)`|  
|*=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (U rhs)`|  
|*=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (SafeInt<U, E> rhs)`|  
|/|`template<typename U>`<br /><br /> `SafeInt<T,E> operator/ (U rhs) const`|  
|/|`SafeInt<T,E> operator/ (SafeInt<T,E> rhs ) const`|  
|/=|`SafeInt<T,E>& operator/= (SafeInt<T,E> i)`|  
|/=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (U i)`|  
|/=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (SafeInt<U, E> i)`|  
|+|`SafeInt<T,E> operator+ (SafeInt<T,E> rhs) const`|  
|+|`template<typename U>`<br /><br /> `SafeInt<T,E> operator+ (U rhs) const`|  
|+=|`SafeInt<T,E>& operator+= (SafeInt<T,E> rhs)`|  
|+=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (U rhs)`|  
|+=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (SafeInt<U, E> rhs)`|  
|-|`template<typename U>`<br /><br /> `SafeInt<T,E> operator- (U rhs) const`|  
|-|`SafeInt<T,E> operator- (SafeInt<T,E> rhs) const`|  
|-=|`SafeInt<T,E>& operator-= (SafeInt<T,E> rhs)`|  
|-=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (U rhs)`|  
|-=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (SafeInt<U, E> rhs)`|  
  
### <a name="logical-operators"></a>Operadores lógicos  
  
|nombre|Sintaxis|  
|----------|------------|  
|!|`bool operator !() const throw()`|  
|~|`SafeInt<T,E> operator~ () const throw()`|  
|<<|`template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (U bits) const throw()`|  
|<<|`template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (SafeInt<U, E> bits) const throw()`|  
|<<=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (U bits) throw()`|  
|<<=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (SafeInt<U, E> bits) throw()`|  
|>>|`template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (U bits) const throw()`|  
|>>|`template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (SafeInt<U, E> bits) const throw()`|  
|>>=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (U bits) throw()`|  
|>>=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (SafeInt<U, E> bits) throw()`|  
|&|`SafeInt<T,E> operator& (SafeInt<T,E> rhs) const throw()`|  
|&|`template<typename U>`<br /><br /> `SafeInt<T,E> operator& (U rhs) const throw()`|  
|&=|`SafeInt<T,E>& operator&= (SafeInt<T,E> rhs) throw()`|  
|&=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (U rhs) throw()`|  
|&=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (SafeInt<U, E> rhs) throw()`|  
|^|`SafeInt<T,E> operator^ (SafeInt<T,E> rhs) const throw()`|  
|^|`template<typename U>`<br /><br /> `SafeInt<T,E> operator^ (U rhs) const throw()`|  
|^=|`SafeInt<T,E>& operator^= (SafeInt<T,E> rhs) throw()`|  
|^=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (U rhs) throw()`|  
|^=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (SafeInt<U, E> rhs) throw()`|  
|&#124;|`SafeInt<T,E> operator&#124; (SafeInt<T,E> rhs) const throw()`|  
|&#124;|`template<typename U>`<br /><br /> `SafeInt<T,E> operator&#124; (U rhs) const throw()`|  
|&#124;=|`SafeInt<T,E>& operator&#124;= (SafeInt<T,E> rhs) throw()`|  
|&#124;=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (U rhs) throw()`|  
|&#124;=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (SafeInt<U, E> rhs) throw()`|  
  
## <a name="remarks"></a>Comentarios  
 La `SafeInt` clase protege contra el desbordamiento de enteros en operaciones matemáticas. Por ejemplo, considere la posibilidad de agregar dos enteros de 8 bits: uno tiene un valor de 200 y el segundo tiene un valor de 100. La operación matemática correcta sería 200 + 100 = 300. Sin embargo, debido al límite de entero de 8 bits, se perderá el bit superior y el compilador devolverá 44 (300-2<sup>8</sup>) como resultado. Cualquier operación que depende esta ecuación matemática generará un comportamiento inesperado.  
  
 La `SafeInt` clase comprueba si se produce un desbordamiento aritmético o si el código intenta dividir por cero. En ambos casos, la clase llama al controlador de errores para advertirle del programa sobre el posible problema.  
  
 Esta clase también le permite comparar dos tipos diferentes de enteros como son `SafeInt` objetos. Normalmente, cuando se realiza una comparación, primero debe convertir los números para ser del mismo tipo. Convertir un número a otro tipo a menudo requiere comprobaciones para asegurarse de que no hay ninguna pérdida de datos.  
  
 La tabla de operadores en este tema enumeran los operadores matemáticos y de comparación admitidos por la `SafeInt` clase. Operadores matemáticos más devuelven un `SafeInt` objeto del tipo `T`.  
  
 Las operaciones de comparación entre un `SafeInt` y un tipo entero se puede realizar en cualquier dirección. Por ejemplo, `SafeInt<int>(x) < y` y `y > SafeInt<int>(x)` son válidos y se devolverá el mismo resultado.  
  
 Muchos operadores binarios no admiten el uso de diferentes `SafeInt` tipos. Un ejemplo de esto es el `&` operador. `SafeInt<T, E> & int`se admite, pero `SafeInt<T, E> & SafeInt<U, E>` no es. En el último ejemplo, el compilador no sabe qué tipo de parámetro para devolver. Una solución a este problema consiste en convertir el segundo parámetro al tipo base. Mediante el uso de los mismos parámetros, esto puede hacerse con `SafeInt<T, E> & (U)SafeInt<U, E>`.  
  
> [!NOTE]
>  Para las operaciones bit a bit, los dos parámetros diferentes deben tener el mismo tamaño. Si los tamaños son diferentes, el compilador producirá un [ASSERT](../mfc/reference/diagnostic-services.md#assert) excepción. No se puede garantizar que los resultados de esta operación sea exacto. Para resolver este problema, convierta el parámetro más pequeño hasta que es el mismo tamaño que el parámetro mayor.  
  
 Para los operadores de desplazamiento desplazar más bits que no existe para el tipo de plantilla producirá una excepción de ASSERT. Esto tendrá ningún efecto en modo de lanzamiento. Si se combinan dos tipos de parámetros de SafeInt es posible que los operadores de desplazamiento porque el tipo de valor devuelto es el mismo que el tipo original. El número en el lado derecho del operador solamente indica el número de bits de desplazamiento.  
  
 Cuando se realiza una comparación lógica con un objeto SafeInt, la comparación es estrictamente aritmética. Por ejemplo, tenga en cuenta estas expresiones:  
  
-   `SafeInt<uint>((uint)~0) > -1`  
  
-   `((uint)~0) > -1`  
  
 La primera instrucción se resuelve como `true`, pero la segunda instrucción se resuelve como `false`. La negación bit a bit 0 es 0xFFFFFFFF. En la segunda instrucción, el operador de comparación predeterminado compara 0xFFFFFFFF a 0xFFFFFFFF y considera que son iguales. El operador de comparación para la `SafeInt` clase se da cuenta de que el segundo parámetro es negativo, mientras que el primer parámetro es sin signo. Por lo tanto, aunque la representación de bits es idéntica, la `SafeInt` operador lógico se da cuenta de que el entero sin signo es mayor que -1.  
  
 Tenga cuidado al usar el `SafeInt` clase junto con el `?:` operador ternario. Tenga en cuenta la siguiente línea de código.  
  
```  
Int x = flag ? SafeInt<unsigned int>(y) : -1;  
```  
  
 El compilador lo convierte a este:  
  
```  
Int x = flag ? SafeInt<unsigned int>(y) : SafeInt<unsigned int>(-1);  
```  
  
 Si `flag` es `false`, el compilador produce una excepción en lugar de asignar el valor de -1 para `x`. Por lo tanto, para evitar este comportamiento, el código correcto para usar es la línea siguiente.  
  
```  
Int x = flag ? (int) SafeInt<unsigned int>(y) : -1;  
```  
  
 `T`y `U` puede asignarse a un tipo booleano, tipo de caracteres o tipo de entero. El entero tipos pueden ser con o sin signo y cualquier tamaño de 8 bits a 64 bits.  
  
> [!NOTE]
>  Aunque la `SafeInt` clase acepta cualquier tipo de entero, lleva a cabo más eficazmente con tipos sin signo.  
  
 `E`es el mecanismo de control de errores que `SafeInt` utiliza. Se proporcionan dos mecanismos de control de errores con la Biblioteca SafeInt. La directiva predeterminada es `SafeIntErrorPolicy_SafeIntException`, que produce una [SafeIntException (clase)](../windows/safeintexception-class.md) excepción cuando se produce un error. La otra directiva es `SafeIntErrorPolicy_InvalidParameter`, que detiene el programa si se produce un error.  
  
 Hay dos opciones para personalizar la directiva de error. La primera opción es establecer el parámetro `E` cuando se crea un `SafeInt`. Use esta opción si desea cambiar el control de errores directiva para una sola `SafeInt`. La otra opción consiste en definir `_SAFEINT_DEFAULT_ERROR_POLICY` como la clase de control de errores personalizada antes de incluir el `SafeInt` biblioteca. Use esta opción si desea cambiar la directiva para todas las instancias de control de errores de forma predeterminada la `SafeInt` clase en el código.  
  
> [!NOTE]
>  Una clase personalizada que controla los errores de la Biblioteca SafeInt no debe devolver el control al código que llama al controlador de errores. Después de que se llama al controlador de errores, el resultado de la `SafeInt` operación no es de confianza.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** safeint.h  
  
 **Namespace:** msl::utilities  
  
## <a name="see-also"></a>Vea también  
 [Biblioteca SafeInt](../windows/safeint-library.md)   
 [SafeIntException (clase)](../windows/safeintexception-class.md)