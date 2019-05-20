---
title: SafeInt (Clase)
ms.date: 10/22/2018
ms.topic: reference
f1_keywords:
- SafeInt
- SafeInt::SafeInt
- SafeInt.SafeInt
helpviewer_keywords:
- SafeInt class
- SafeInt class, constructor
ms.assetid: 27a8f087-2511-46f9-8d76-2aeb66ca272f
ms.openlocfilehash: 1fc7ec438d83be1a92d8fa9d699f4172aba842e4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515560"
---
# <a name="safeint-class"></a>SafeInt (Clase)

Amplía las primitivas de enteros para ayudar a evitar el desbordamiento de enteros y permite comparar diferentes tipos de enteros.

> [!NOTE] 
> La versión más reciente de esta biblioteca se encuentra en [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt).

## <a name="syntax"></a>Sintaxis

```cpp
template<typename T, typename E = _SAFEINT_DEFAULT_ERROR_POLICY>
class SafeInt;
```

### <a name="parameters"></a>Parámetros

| Plantilla  |  Descripción |
|--------|------------|
| T         |  El tipo de parámetro entero o booleano que reemplaza `SafeInt`. |
| E         |  Un tipo de datos enumerados que define la directiva de control de errores. |
| U         |  El tipo de parámetro entero o booleano para el operando secundario. |

| Parámetro  |  Descripción |
|---------|-----------------|
| *rhs*      |  [in] Un parámetro de entrada que representa el valor en el lado derecho del operador en varias funciones independientes. |
| *i*        |  [in] Un parámetro de entrada que representa el valor en el lado derecho del operador en varias funciones independientes. |
| *bits*     |  [in] Un parámetro de entrada que representa el valor en el lado derecho del operador en varias funciones independientes. |

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

| nombre                          |  Descripción |
|---------------------------|--------------------|
| [SafeInt::SafeInt](#safeint)  |  Constructor predeterminado. |

### <a name="assignment-operators"></a>Operadores de asignación

| nombre  |  Sintaxis |
|----|---------|
| =     |  `template<typename U>`<br />`SafeInt<T,E>& operator= (const U& rhs)` |
| =     |  `SafeInt<T,E>& operator= (const T& rhs) throw()` |
| =     |  `template<typename U>`<br />`SafeInt<T,E>& operator= (const SafeInt<U, E>& rhs)` |
| =     |  `SafeInt<T,E>& operator= (const SafeInt<T,E>& rhs) throw()` |

### <a name="casting-operators"></a>Operadores de conversión

| nombre              |  Sintaxis |
|------|---------------------------------|
| bool              |  `operator bool() throw()` |
| char              |  `operator char() const` |
| signed char       |  `operator signed char() const` |
| unsigned char     |  `operator unsigned char() const` |
| __int16           |  `operator __int16() const` |
| unsigned __int16  |  `operator unsigned __int16() const` |
| __int32           |  `operator __int32() const` |
| unsigned __int32  |  `operator unsigned __int32() const` |
| long              |  `operator long() const` |
| unsigned long     |  `operator unsigned long() const` |
| __int64           |  `operator __int64() const` |
| unsigned __int64  |  `operator unsigned __int64() const` |
| wchar_t           |  `operator wchar_t() const` |

### <a name="comparison-operators"></a>Operadores de comparación

| nombre  |  Sintaxis |
|----|----------------|
| \<     |  `template<typename U>`<br /><br /> `bool operator< (U rhs) const throw()` |
| \<     |  `bool operator< (SafeInt<T,E> rhs) const throw()` |
| \>=    |  `template<typename U>`<br /><br /> `bool operator>= (U rhs) const throw()` |
| \>=    |  `Bool operator>= (SafeInt<T,E> rhs) const throw()` |
| \>     |  `template<typename U>`<br /><br /> `bool operator> (U rhs) const throw()` |
| \>     |  `Bool operator> (SafeInt<T,E> rhs) const throw()` |
| \<=    |  `template<typename U>`<br /><br /> `bool operator<= (U rhs) const throw()` |
| \<=    |  `bool operator<= (SafeInt<T,E> rhs) const throw()` |
| ==    |  `template<typename U>`<br /><br /> `bool operator== (U rhs) const throw()` |
| ==    |  `bool operator== (bool rhs) const throw()` |
| ==    |  `bool operator== (SafeInt<T,E> rhs) const throw()` |
| !=    |  `template<typename U>`<br /><br /> `bool operator!= (U rhs) const throw()` |
| !=    |  `bool operator!= (bool b) const throw()` |
| !=    |  `bool operator!= (SafeInt<T,E> rhs) const throw()` |

### <a name="arithmetic-operators"></a>Operadores aritméticos

| nombre  |  Sintaxis |
|----|--------------|
| +     |  `const SafeInt<T,E>& operator+ () const throw()` |
| -     |  `SafeInt<T,E> operator- () const` |
| ++    |  `SafeInt<T,E>& operator++ ()` |
| --    |  `SafeInt<T,E>& operator-- ()` |
| %     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator% (U rhs) const` |
| %     |  `SafeInt<T,E> operator% (SafeInt<T,E> rhs) const` |
| %=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (U rhs)` |
| %=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (SafeInt<U, E> rhs)` |
| \*     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator* (U rhs) const` |
| \*     |  `SafeInt<T,E> operator* (SafeInt<T,E> rhs) const` |
| \*=    |  `SafeInt<T,E>& operator*= (SafeInt<T,E> rhs)` |
| \*=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (U rhs)` |
| \*=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (SafeInt<U, E> rhs)` |
| /     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator/ (U rhs) const` |
| /     |  `SafeInt<T,E> operator/ (SafeInt<T,E> rhs ) const` |
| /=    |  `SafeInt<T,E>& operator/= (SafeInt<T,E> i)` |
| /=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (U i)` |
| /=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (SafeInt<U, E> i)` |
| +     |  `SafeInt<T,E> operator+ (SafeInt<T,E> rhs) const` |
| +     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator+ (U rhs) const` |
| +=    |  `SafeInt<T,E>& operator+= (SafeInt<T,E> rhs)` |
| +=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (U rhs)` |
| +=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (SafeInt<U, E> rhs)` |
| -     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator- (U rhs) const` |
| -     |  `SafeInt<T,E> operator- (SafeInt<T,E> rhs) const` |
| -=    |  `SafeInt<T,E>& operator-= (SafeInt<T,E> rhs)` |
| -=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (U rhs)` |
| -=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (SafeInt<U, E> rhs)` |

### <a name="logical-operators"></a>Operadores lógicos

| nombre     |  Sintaxis |
|------|--------------|
| !        |  `bool operator !() const throw()` |
| ~        |  `SafeInt<T,E> operator~ () const throw()` |
| \<\<       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (U bits) const throw()` |
| \<\<       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (SafeInt<U, E> bits) const throw()` |
| \<\<=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (U bits) throw()` |
| \<\<=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (SafeInt<U, E> bits) throw()` |
| \>\>       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (U bits) const throw()` |
| \>\>       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (SafeInt<U, E> bits) const throw()` |
| \>\>=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (U bits) throw()` |
| \>\>=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (SafeInt<U, E> bits) throw()` |
| &        |  `SafeInt<T,E> operator& (SafeInt<T,E> rhs) const throw()` |
| &        |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator& (U rhs) const throw()` |
| &=       |  `SafeInt<T,E>& operator&= (SafeInt<T,E> rhs) throw()` |
| &=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (U rhs) throw()` |
| &=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (SafeInt<U, E> rhs) throw()` |
| ^        |  `SafeInt<T,E> operator^ (SafeInt<T,E> rhs) const throw()` |
| ^        |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator^ (U rhs) const throw()` |
| ^=       |  `SafeInt<T,E>& operator^= (SafeInt<T,E> rhs) throw()` |
| ^=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (U rhs) throw()` |
| ^=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (SafeInt<U, E> rhs) throw()` |
| &#124;   |  `SafeInt<T,E> operator&#124; (SafeInt<T,E> rhs) const throw()` |
| &#124;   |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator&#124; (U rhs) const throw()` |
| &#124;=  |  `SafeInt<T,E>& operator&#124;= (SafeInt<T,E> rhs) throw()` |
| &#124;=  |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (U rhs) throw()` |
| &#124;=  |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (SafeInt<U, E> rhs) throw()` |

## <a name="remarks"></a>Comentarios

La clase `SafeInt` protege frente al desbordamiento de enteros en las operaciones matemáticas. Por ejemplo, suponga que se agregan dos enteros de 8 bits: uno tiene un valor de 200 y el segundo de 100. La operación matemática correcta sería 200 + 100 = 300. Sin embargo, debido al límite de enteros de 8 bits, se perderá el bit superior y el compilador devolverá como resultado 44 (300-2<sup>8</sup>). Cualquier operación que dependa de esta ecuación matemática generará un comportamiento inesperado.

La clase `SafeInt` comprueba si se produce un desbordamiento aritmético o si el código intenta dividir por cero. En ambos casos, la clase llama al controlador de errores para advertir al programa del posible problema.

Esta clase también le permite comparar dos tipos diferentes de enteros siempre que sean objetos `SafeInt`. Normalmente, cuando se realiza una comparación, primero se deben convertir los números para que sean del mismo tipo. Para convertir un número en otro tipo con frecuencia se necesitan comprobaciones para asegurarse de que no hay pérdida de datos.

En la tabla de operadores de este tema se enumeran los operadores matemáticos y de comparación que admite la clase `SafeInt`. La mayoría de operadores matemáticos devuelven un objeto `SafeInt` de tipo `T`.

Las operaciones de comparación entre `SafeInt` y un tipo entero se pueden realizar en cualquier dirección. Por ejemplo, tanto `SafeInt<int>(x) < y` como `y> SafeInt<int>(x)` son válidos y devolverán el mismo resultado.

Muchos operadores binarios no admiten el uso de dos tipos de `SafeInt` diferentes. Un operador de este tipo es `&`. Se admite `SafeInt<T, E> & int`, pero no `SafeInt<T, E> & SafeInt<U, E>`. En el último ejemplo, el compilador no sabe qué tipo de parámetro devolver. Una solución a este problema es convertir el segundo parámetro de nuevo al tipo base. Para ello se puede utilizar `SafeInt<T, E> & (U)SafeInt<U, E>` con los mismos parámetros.

> [!NOTE]
> En las operaciones bit a bit, los dos parámetros diferentes deben tener el mismo tamaño. Si los tamaños son diferentes, el compilador producirá una excepción [ASSERT](../mfc/reference/diagnostic-services.md#assert). No se puede garantizar que los resultados de esta operación sean precisos. Para resolver este problema, convierta el parámetro más pequeño hasta que tenga el mismo tamaño que el parámetro más grande.

Con los operadores de desplazamiento, al desplazar más bits de los que existen para el tipo de plantilla se producirá una excepción ASSERT. Esta acción no tendrá ningún efecto en el modo de versión. Los operadores de desplazamiento permiten mezclar dos tipos de parámetros SafeInt, ya que el tipo de valor devuelto es igual que el tipo original. El número en el lado derecho del operador solo indica el número de bits que se van a desplazar.

Cuando se realiza una comparación lógica con un objeto SafeInt, la comparación es estrictamente aritmética. Por ejemplo, vea estas expresiones:

- `SafeInt<uint>((uint)~0) > -1`

- `((uint)~0) > -1`

La primera instrucción se resuelve en **true**, pero la segunda instrucción se resuelve en `false`. La negación bit a bit de 0 es 0xFFFFFFFF. En la segunda instrucción, el operador de comparación predeterminado compara 0xFFFFFFFF con 0xFFFFFFFF y considera que son iguales. El operador de comparación de la clase `SafeInt` se da cuenta de que el segundo parámetro es negativo, mientras que el primer parámetro no tiene signo. Por lo tanto, aunque la representación de bits es idéntica, el operador lógico `SafeInt` se da cuenta de que el entero sin signo es mayor que -1.

Tenga cuidado al usar la clase `SafeInt` en combinación con el operador ternario `?:`. Vea la siguiente línea de código.

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : -1;
```

El compilador la convierte en esto:

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : SafeInt<unsigned int>(-1);
```

Si `flag` es `false`, el compilador produce una excepción en lugar de asignar el valor de -1 a `x`. Por lo tanto, para evitar este comportamiento, el código correcto que se debe usar es la siguiente línea.

```cpp
Int x = flag ? (int) SafeInt<unsigned int>(y) : -1;
```

A `T` y `U` se les puede asignar un tipo booleano, un tipo de carácter o un tipo entero. Los tipos enteros pueden tener o no signo y cualquier tamaño entre 8 y 64 bits.

> [!NOTE]
> Aunque la clase `SafeInt` acepta cualquier tipo de entero, funciona mejor con tipos sin signo.

`E` es el mecanismo de control de errores que usa `SafeInt`. Con la biblioteca de SafeInt se proporcionan dos mecanismos de control de errores. La directiva predeterminada es `SafeIntErrorPolicy_SafeIntException`, que produce una excepción [SafeIntException (Clase)](../safeint/safeintexception-class.md) cuando hay un error. La otra directiva es `SafeIntErrorPolicy_InvalidParameter`, que detiene el programa si se produce un error.

Hay dos opciones para personalizar la directiva de errores. La primera opción es establecer el parámetro `E` al crear un objeto `SafeInt`. Use esta opción si quiere cambiar la directiva de control de errores de un único objeto `SafeInt`. La otra opción es definir _SAFEINT_DEFAULT_ERROR_POLICY como la clase de control de errores personalizada antes de incluir la biblioteca `SafeInt`. Use esta opción si quiere cambiar la directiva de control de errores predeterminada de todas las instancias de la clase `SafeInt` en el código.

> [!NOTE]
> Una clase personalizada que controla los errores de la biblioteca SafeInt no debe devolver el control al código que llamó al controlador de errores. Después de llamar al controlador de errores, no se puede confiar en el resultado de la operación de `SafeInt`.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`SafeInt`

## <a name="requirements"></a>Requisitos

**Encabezado:** safeint.h

**Espacio de nombres:** msl::utilities

## <a name="safeint"></a>SafeInt::SafeInt

Construye un objeto `SafeInt`.

```cpp
SafeInt() throw

SafeInt (
   const T& i
) throw ()

SafeInt (
   bool b
) throw ()

template <typename U>
SafeInt (
   const SafeInt <U, E>& u
)

I template <typename U>
SafeInt (
   const U& i
)
```

### <a name="parameters"></a>Parámetros

*i*<br/>
[in] El valor del nuevo objeto `SafeInt`. Debe ser un parámetro de tipo T o U, según el constructor.

*b*<br/>
[in] El valor booleano del nuevo objeto `SafeInt`.

*u*<br/>
[in] Un objeto `SafeInt` de tipo U. El nuevo objeto `SafeInt` tendrá el mismo valor que *u*, pero será de tipo T.

U: el tipo de datos almacenados en `SafeInt`. Puede ser un tipo entero, de carácter o booleano. Si es un tipo entero, puede tener o no signo y estar formado por entre 8 y 64 bits.

### <a name="remarks"></a>Comentarios

El parámetro de entrada para el constructor, *i* o *u*, debe ser un tipo entero, de carácter o booleano. Si es otro tipo de parámetro, la clase `SafeInt` llama a [static_assert](../cpp/static-assert.md) para indicar un parámetro de entrada no válido.

Los constructores que utilizan el tipo de plantilla `U` convierten automáticamente el parámetro de entrada en el tipo especificado por `T`. La clase `SafeInt` convierte los datos sin pérdida de datos. Informa al controlador de errores `E` si no puede convertir los datos al tipo `T` sin pérdida de datos.

Si crea un objeto `SafeInt` a partir de un parámetro booleano, debe inicializar el valor inmediatamente. No se puede construir un objeto `SafeInt` con el código `SafeInt<bool> sb;`. Se generará un error de compilación.
