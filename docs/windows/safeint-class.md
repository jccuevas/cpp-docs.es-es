---
title: "SafeInt (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "SafeInt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeInt (clase)"
ms.assetid: 27a8f087-2511-46f9-8d76-2aeb66ca272f
caps.latest.revision: 16
caps.handback.revision: 16
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# SafeInt (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Extender los primitivos fundamentales para ayudar a evitar el desbordamiento de enteros y permiten comparar diferentes tipos de enteros.  
  
## Sintaxis  
  
```  
template<typename T, typename E = _SAFEINT_DEFAULT_ERROR_POLICY>  
class SafeInt;  
```  
  
#### Parámetros  
  
|Plantilla|Descripción|  
|---------------|-----------------|  
|T|El tipo de parámetro entero o boolean que `SafeInt` reemplaza.|  
|E|Un tipo de datos enumerado que define la directiva de control de errores.|  
|U|El tipo de parámetro entero o boolean para el operando secundario.|  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|\[in\] lado derecho|Un parámetro de entrada que representa el valor de la derecha del operador en varias funciones independientes.|  
|\[in\] i|Un parámetro de entrada que representa el valor de la derecha del operador en varias funciones independientes.|  
|\[in\] bits|Un parámetro de entrada que representa el valor de la derecha del operador en varias funciones independientes.|  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SafeInt::SafeInt](../windows/safeint-safeint.md)|Constructor predeterminado.|  
  
### Operadores de asignación  
  
|Name|Sintaxis|  
|----------|--------------|  
|\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator= (const U& rhs)`|  
|\=|`SafeInt<T,E>& operator= (const T& rhs) throw()`|  
|\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator= (const SafeInt<U, E>& rhs)`|  
|\=|`SafeInt<T,E>& operator= (const SafeInt<T,E>& rhs) throw()`|  
  
### Operadores de conversión  
  
|Name|Sintaxis|  
|----------|--------------|  
|bool|`operator bool() throw()`|  
|char|`operator char() const`|  
|signed char|`operator signed char() const`|  
|unsigned char|`operator unsigned char() const`|  
|\_\_int16|`operator __int16() const`|  
|unsigned \_\_int16|`operator unsigned __int16() const`|  
|\_\_int32|`operator __int32() const`|  
|unsigned \_\_int32|`operator unsigned __int32() const`|  
|long|`operator long() const`|  
|unsigned long|`operator unsigned long() const`|  
|\_\_int64|`operator __int64() const`|  
|unsigned \_\_int64|`operator unsigned __int64() const`|  
|wchar\_t|`operator wchar_t() const`|  
  
### Operadores de comparación  
  
|Name|Sintaxis|  
|----------|--------------|  
|\<|`template<typename U>`<br /><br /> `bool operator< (U rhs) const throw()`|  
|\<|`bool operator< (SafeInt<T,E> rhs) const throw()`|  
|\>\=|`template<typename U>`<br /><br /> `bool operator>= (U rhs) const throw()`|  
|\>\=|`Bool operator>= (SafeInt<T,E> rhs) const throw()`|  
|\>|`template<typename U>`<br /><br /> `bool operator> (U rhs) const throw()`|  
|\>|`Bool operator> (SafeInt<T,E> rhs) const throw()`|  
|\<\=|`template<typename U>`<br /><br /> `bool operator<= (U rhs) const throw()`|  
|\<\=|`bool operator<= (SafeInt<T,E> rhs) const throw()`|  
|\=\=|`template<typename U>`<br /><br /> `bool operator== (U rhs) const throw()`|  
|\=\=|`bool operator== (bool rhs) const throw()`|  
|\=\=|`bool operator== (SafeInt<T,E> rhs) const throw()`|  
|\!\=|`template<typename U>`<br /><br /> `bool operator!= (U rhs) const throw()`|  
|\!\=|`bool operator!= (bool b) const throw()`|  
|\!\=|`bool operator!= (SafeInt<T,E> rhs) const throw()`|  
  
### Operadores aritméticos  
  
|Name|Sintaxis|  
|----------|--------------|  
|\+|`const SafeInt<T,E>& operator+ () const throw()`|  
|\-|`SafeInt<T,E> operator- () const`|  
|\+\+|`SafeInt<T,E>& operator++ ()`|  
|\-\-|`SafeInt<T,E>& operator-- ()`|  
|%|`template<typename U>`<br /><br /> `SafeInt<T,E> operator% (U rhs) const`|  
|%|`SafeInt<T,E> operator% (SafeInt<T,E> rhs) const`|  
|%\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (U rhs)`|  
|%\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (SafeInt<U, E> rhs)`|  
|\*|`template<typename U>`<br /><br /> `SafeInt<T,E> operator* (U rhs) const`|  
|\*|`SafeInt<T,E> operator* (SafeInt<T,E> rhs) const`|  
|\*\=|`SafeInt<T,E>& operator*= (SafeInt<T,E> rhs)`|  
|\*\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (U rhs)`|  
|\*\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (SafeInt<U, E> rhs)`|  
|\/|`template<typename U>`<br /><br /> `SafeInt<T,E> operator/ (U rhs) const`|  
|\/|`SafeInt<T,E> operator/ (SafeInt<T,E> rhs ) const`|  
|\/\=|`SafeInt<T,E>& operator/= (SafeInt<T,E> i)`|  
|\/\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (U i)`|  
|\/\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (SafeInt<U, E> i)`|  
|\+|`SafeInt<T,E> operator+ (SafeInt<T,E> rhs) const`|  
|\+|`template<typename U>`<br /><br /> `SafeInt<T,E> operator+ (U rhs) const`|  
|\+\=|`SafeInt<T,E>& operator+= (SafeInt<T,E> rhs)`|  
|\+\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (U rhs)`|  
|\+\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (SafeInt<U, E> rhs)`|  
|\-|`template<typename U>`<br /><br /> `SafeInt<T,E> operator- (U rhs) const`|  
|\-|`SafeInt<T,E> operator- (SafeInt<T,E> rhs) const`|  
|\-\=|`SafeInt<T,E>& operator-= (SafeInt<T,E> rhs)`|  
|\-\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (U rhs)`|  
|\-\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (SafeInt<U, E> rhs)`|  
  
### Operadores lógicos  
  
|Name|Sintaxis|  
|----------|--------------|  
|\!|`bool operator !() const throw()`|  
|~|`SafeInt<T,E> operator~ () const throw()`|  
|\<\<|`template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (U bits) const throw()`|  
|\<\<|`template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (SafeInt<U, E> bits) const throw()`|  
|\<\<\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (U bits) throw()`|  
|\<\<\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (SafeInt<U, E> bits) throw()`|  
|\>\>|`template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (U bits) const throw()`|  
|\>\>|`template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (SafeInt<U, E> bits) const throw()`|  
|\>\>\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (U bits) throw()`|  
|\>\>\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (SafeInt<U, E> bits) throw()`|  
|&|`SafeInt<T,E> operator& (SafeInt<T,E> rhs) const throw()`|  
|&|`template<typename U>`<br /><br /> `SafeInt<T,E> operator& (U rhs) const throw()`|  
|&\=|`SafeInt<T,E>& operator&= (SafeInt<T,E> rhs) throw()`|  
|&\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (U rhs) throw()`|  
|&\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (SafeInt<U, E> rhs) throw()`|  
|^|`SafeInt<T,E> operator^ (SafeInt<T,E> rhs) const throw()`|  
|^|`template<typename U>`<br /><br /> `SafeInt<T,E> operator^ (U rhs) const throw()`|  
|^\=|`SafeInt<T,E>& operator^= (SafeInt<T,E> rhs) throw()`|  
|^\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (U rhs) throw()`|  
|^\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (SafeInt<U, E> rhs) throw()`|  
|&#124;|`SafeInt<T,E> operator&#124; (SafeInt<T,E> rhs) const throw()`|  
|&#124;|`template<typename U>`<br /><br /> `SafeInt<T,E> operator&#124; (U rhs) const throw()`|  
|&#124;\=|`SafeInt<T,E>& operator&#124;= (SafeInt<T,E> rhs) throw()`|  
|&#124;\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (U rhs) throw()`|  
|&#124;\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (SafeInt<U, E> rhs) throw()`|  
  
## Comentarios  
 La clase de `SafeInt` protege contra el desbordamiento de enteros en operaciones matemáticas.  Por ejemplo, considere agregar dos enteros de 8 bits: uno tiene un valor de 200 y el segundo tiene un valor de 100.  La operación matemática correcta se 200 \+ 100 \= 300.  Sin embargo, debido al límite entero de 8 bits, el bit superior se perderán y el compilador devolverá 44 \(300 \- 2<sup>8</sup>\) como resultado.  Cualquier operación que depende de esta ecuación matemática generará un comportamiento inesperado.  
  
 La clase de `SafeInt` comprueba si un desbordamiento aritmético aparece o si el código intenta dividir por cero.  En ambos casos, la clase llama al controlador de errores para advertir el programa del problema.  
  
 Esta clase también permite comparar dos tipos de enteros mientras son objetos de `SafeInt` .  Normalmente, cuando se realiza una comparación, primero debe convertir números con el mismo tipo.  El inicio de un número a otro tipo requiere a menudo comprobaciones asegurarse de que no haya pérdida de datos.  
  
 La tabla de los operadores de este tema muestra el matemático y operadores de comparación admitidos por el tipo de `SafeInt` .  La mayoría de los operadores matemáticos devuelven un objeto de `SafeInt` de `T`escrito.  
  
 Las operaciones de comparación entre `SafeInt` y un tipo entero se pueden realizar en cualquier dirección.  Por ejemplo, `SafeInt<int>(x) < y` y `y > SafeInt<int>(x)` son válidos y devolverán el mismo resultado.  
  
 Muchos operadores binarios no admiten mediante dos tipos diferentes de `SafeInt` .  Un ejemplo de esto es el operador de `&` .  se admite`SafeInt<T, E> & int` , pero `SafeInt<T, E> & SafeInt<U, E>` no.  En el último ejemplo, el compilador no conoce el tipo de parámetro a devolver.  Una solución a este problema es convertir el segundo parámetro al tipo base.  Utilizando los mismos parámetros, esto se puede hacer con `SafeInt<T, E> & (U)SafeInt<U, E>`.  
  
> [!NOTE]
>  Para cualquier operación bit a bit, los dos diferentes parámetros deben tener el mismo tamaño.  Si difieren tamaños, el compilador produce una excepción de [ASSERT](../Topic/ASSERT%20\(MFC\).md) .  Los resultados de esta operación no pueden garantizar para ser precisos.  Para resolver este problema, convierta el parámetro menor hasta que el mismo tamaño que el parámetro mayor.  
  
 Para los operadores de cambio, al desplazarse más bits que existe para el tipo de plantilla producirá una excepción ASSERT.  Esto no tendrá ningún efecto en modo de lanzamiento.  Mezclar dos tipos de parámetros SafeInt es posible que los operadores de cambio porque el tipo de valor devuelto es el mismo que el tipo original.  El número a la derecha del operador sólo indica el número de bits al cambio.  
  
 Cuando se realiza una comparación lógica con un objeto SafeInt, la comparación es estrictamente aritmética.  Por ejemplo, considere estas expresiones:  
  
-   `SafeInt<uint>((uint)~0) > -1`  
  
-   `((uint)~0) > -1`  
  
 La primera instrucción cumple a `true`, pero la segunda instrucción se resuelve como `false`.  La negación bit a bit de 0 es 0xFFFFFFFF.  En la segunda instrucción, el operador de comparación predeterminado compara 0xFFFFFFFF a 0xFFFFFFFF y se considera igual.  El operador de comparación de la clase de `SafeInt` detecta que el segundo parámetro es negativo como primer parámetro es sin signo.  Por consiguiente, aunque la representación de bits es idéntica, el operador lógico de `SafeInt` detecta que el entero sin signo es mayor de \-1.  
  
 Tenga cuidado al utilizar la clase de `SafeInt` junto con el operador ternario de `?:` .  Considere la siguiente línea de código.  
  
```  
Int x = flag ? SafeInt<unsigned int>(y) : -1;  
```  
  
 El compilador lo convierte a:  
  
```  
Int x = flag ? SafeInt<unsigned int>(y) : SafeInt<unsigned int>(-1);  
```  
  
 Si `flag` es `false`, el compilador produce una excepción en lugar de asignar el valor de \-1 a `x`.  Por consiguiente, para evitar este comportamiento, código correcto para utilizar es la línea siguiente.  
  
```  
Int x = flag ? (int) SafeInt<unsigned int>(y) : -1;  
```  
  
 `T` y `U` se pueden asignar un tipo booleano, el tipo de caracteres, o el tipo integer.  Los tipos enteros pueden ser firmados o sin signo y cualquier tamaño a partir de 8 bits a 64 bits.  
  
> [!NOTE]
>  Aunque la clase de `SafeInt` acepta cualquier tipo de entero, realiza más eficazmente con tipos sin signo.  
  
 `E` es el mecanismo de control de errores que `SafeInt` utiliza.  Dos mecanismos de control de errores se proporcionan la biblioteca SafeInt.  La directiva predeterminada es `SafeIntErrorPolicy_SafeIntException`, que produce una excepción de [SafeIntException \(Clase\)](../windows/safeintexception-class.md) cuando se produce un error.  Otra directiva es `SafeIntErrorPolicy_InvalidParameter`, que detiene el programa si se produce un error.  
  
 Hay dos opciones para personalizar la directiva del error.  La primera opción es establecer el parámetro `E` cuando se crea `SafeInt`.  Use esta opción si desea cambiar la directiva de control de errores para un solo `SafeInt`.  Otra opción es definir `_SAFEINT_DEFAULT_ERROR_POLICY` para ser la clase de control de errores antes de que incluye la biblioteca de `SafeInt` .  Use esta opción si desea cambiar la directiva predeterminada de control de errores para todas las instancias de la clase de `SafeInt` en el código.  
  
> [!NOTE]
>  Una clase personalizada que controla los errores de la biblioteca SafeInt no debe devolver el control al código que llamó al controlador de errores.  Después de llamar al controlador de errores, el resultado de la operación de `SafeInt` no se puede confirmar.  
  
## Requisitos  
 **Encabezado:** safeint.h  
  
 msl::utilities de**Espacio de nombres:**  
  
## Vea también  
 [Clases admiten distintas de las bibliotecas](http://msdn.microsoft.com/es-es/406fd46e-d53f-4096-ab40-36aa754c7a5c)   
 [SafeInt \(Biblioteca\)](../windows/safeint-library.md)   
 [SafeIntException \(Clase\)](../windows/safeintexception-class.md)