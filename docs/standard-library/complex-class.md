---
title: complex (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- complex/std::complex::value_type
- complex/std::complex::imag
- complex/std::complex::real
dev_langs:
- C++
helpviewer_keywords:
- std::complex [C++], value_type
- std::complex [C++], imag
- std::complex [C++], real
ms.assetid: d6492e1c-5eba-4bc5-835b-2a88001a5868
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a76266714a462837ce8c919392abde8293af8d86
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43684726"
---
# <a name="complex-class"></a>complex (Clase)

La clase de plantilla describe un objeto que almacena dos objetos de tipo `Type`, uno que representa la parte real de un número complejo y otro que representa la parte imaginaria.

## <a name="syntax"></a>Sintaxis

```

template <class
Type>
class complex
```

## <a name="remarks"></a>Comentarios

Un objeto de clase `Type`:

- Tiene un constructor público predeterminado, un destructor, un constructor de copias y un operador de asignación, con un comportamiento convencional.

- Se pueden asignar valores de punto flotante o enteros, o convertirse al tipo de esos valores con un comportamiento convencional.

- Define, en la medida que sean necesarios, los operadores aritméticos y las funciones matemáticas que se definen para los tipos de punto flotante con un comportamiento convencional.

En concreto, no pueden existir diferencias sutiles entre la construcción de la copia y la construcción predeterminada seguida por una asignación. Ninguna de las operaciones en objetos de clase `Type` pueden producir excepciones.

Las especializaciones explícitas de la clase de plantilla compleja existen para los tres tipos de punto flotante. En esta implementación, un valor de cualquier otro tipo `Type` está encasillado en **doble** para cálculos reales, con el **doble** asignado al objeto almacenado de tipo de resultado `Type``.`

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[complex](#complex)|Construye un número complejo con partes reales e imaginarias especificados o como una copia de otro número complejo.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[value_type](#value_type)|Tipo que representa el tipo de datos usado para representar las partes reales e imaginarias de un número complejo.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[imag](#imag)|Extrae el componente imaginario de un número complejo.|
|[real](#real)|Extrae el componente real de un número complejo|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator*=](#op_star_eq)|Multiplica un número complejo de destino por un factor, que puede ser complejo o del mismo tipo, como lo son las partes reales e imaginarias del número complejo.|
|[operator+=](#op_add_eq)|Agrega un número a un número complejo de destino, donde el número agregado puede ser complejo o del mismo tipo que las partes reales e imaginarias del número complejo al que se agrega.|
|[operator-=](#operator-_eq)|Resta un número de un número complejo de destino, donde el número restado puede ser complejo o del mismo tipo que las partes reales e imaginarias del número complejo al que se agrega.|
|[operator/=](#op_div_eq)|Divide un número complejo de destino por un divisor, que puede ser complejo o del mismo tipo, como lo son las partes reales e imaginarias del número complejo.|
|[operator=](#op_eq)|Asigna un número a un número complejo de destino, donde el número asignado puede ser complejo o del mismo tipo que las partes reales e imaginarias del número complejo al que se está asignando.|

## <a name="requirements"></a>Requisitos

**Encabezado**: \<complex>

**Espacio de nombres:** std

## <a name="complex"></a>  complex::complex

Construye un número complejo con partes reales e imaginarias especificados o como una copia de otro número complejo.

```cpp
constexpr complex(
    const T&
    _RealVal = 0  ,
    const T&
    _ImagVal = 0);

    template <class Other>
constexpr complex(
    const complex<Other>&
    complexNum);
```

### <a name="parameters"></a>Parámetros

*_RealVal* el valor de la parte real que se usa para inicializar el número complejo que se está construyendo.

*_ImagVal* el valor de la parte imaginaria que se usa para inicializar el número complejo que se está construyendo.

*complexNum* el número complejo cuyas partes reales e imaginarias se usan para inicializar el número complejo que se está construyendo.

### <a name="remarks"></a>Comentarios

El primer constructor inicializa la parte real almacenada en _ *RealVal* y la parte imaginaria almacenada en \_ *Imagval*. El segundo constructor inicializa la parte real almacenada en `complexNum`**.real**() y la parte imaginaria almacenada en `complexNum`**.imag**().

En esta implementación, si un En esta implementación, si un traductor no admite las funciones miembro de plantilla, la plantilla:

```cpp
template <class Other>
complex(const complex<Other>& right);
```

se reemplaza por:

```

complex(const complex& right);
```

que es el constructor de copias.

### <a name="example"></a>Ejemplo

```cpp
// complex_complex.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // The first constructor specifies real & imaginary parts
   complex <double> c1 ( 4.0 , 5.0 );
   cout << "Specifying initial real & imaginary parts,"
        << "c1 = " << c1 << endl;

   // The second constructor initializes values of the real &
   // imaginary parts using those of another complex number
   complex <double> c2 ( c1 );
   cout << "Initializing with the real and imaginary parts of c1,"
        << " c2 = " << c2 << endl;

   // Complex numbers can be initialized in polar form
   // but will be stored in Cartesian form
   complex <double> c3 ( polar ( sqrt( (double)8 ) , pi / 4 ) );
   cout << "c3 = polar ( sqrt ( 8 ) , pi / 4 ) = " << c3 << endl;

   // The modulus and argument of a complex number can be recovered
   double absc3 = abs ( c3 );
   double argc3 = arg ( c3 );
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "
        << absc3 << endl;
   cout << "Argument of c3 is recovered from c3 using:\n arg ( c3 ) = "
        << argc3 << " radians, which is " << argc3 * 180 / pi
        << " degrees." << endl;
}
```

## <a name="imag"></a>  complex::imag

Extrae el componente imaginario de un número complejo.

```cpp
T imag() const;


T imag(const T& right);
```

### <a name="parameters"></a>Parámetros

*derecha* un número complejo cuya valor imaginario es se va a extraer.

### <a name="return-value"></a>Valor devuelto

Parte imaginaria del número complejo.

### <a name="remarks"></a>Comentarios

Para un número complejo *a + bi*, el componente o parte imaginaria es *Im(a + bi) = b.*

### <a name="example"></a>Ejemplo

```cpp
// complex_imag.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;

   complex <double> c1 ( 4.0 , 3.0 );
   cout << "The complex number c1 = " << c1 << endl;

   double dr1 = c1.real ( );
   cout << "The real part of c1 is c1.real ( ) = "
        << dr1 << "." << endl;

   double di1 = c1.imag ( );
   cout << "The imaginary part of c1 is c1.imag ( ) = "
        << di1 << "." << endl;
}
```

```Output
The complex number c1 = (4,3)
The real part of c1 is c1.real ( ) = 4.
The imaginary part of c1 is c1.imag ( ) = 3.
```

## <a name="op_star_eq"></a>  complex::operator*=

Multiplica un número complejo de destino por un factor, que puede ser complejo o del mismo tipo, como lo son las partes reales e imaginarias del número complejo.

```cpp
template <class Other>
complex& operator*=(const complex<Other>& right);

complex<Type>& operator*=(const Type& right);

complex<Type>& operator*=(const complex<Type>& right);
```

### <a name="parameters"></a>Parámetros

*derecha* un número complejo o un número que es el mismo tipo que el parámetro del número complejo de destino.

### <a name="return-value"></a>Valor devuelto

Un número complejo que se ha multiplicado por el número especificado como un parámetro.

### <a name="remarks"></a>Comentarios

La operación se sobrecarga para poder ejecutar operaciones aritméticas simples sin necesidad de conversión de datos a un formato determinado.

### <a name="example"></a>Ejemplo

```cpp
// complex_op_me.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main() {
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> multiplied by type complex<double>
   complex <double> cl1 ( polar ( 3.0 , pi / 6 ) );
   complex <double> cr1 ( polar ( 2.0 , pi / 3 ) );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex <double> cs1 = cl1 * cr1;
   cout << "Quotient of two complex numbers is: cs1 = cl1 * cr1 = "
        << cs1 << endl;

   // This is equivalent to the following operation
   cl1 *= cr1;
   cout << "Quotient of two complex numbers is also: cl1 *= cr1 = "
        << cl1 << endl;

   double abscl1 = abs ( cl1 );
   double argcl1 = arg ( cl1 );
   cout << "The modulus of cl1 is: " << abscl1 << endl;
   cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type complex<double> multiplied by type double
   complex <double> cl2 ( polar ( 3.0 , pi / 6 ) );
   double cr2 = 5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex <double> cs2 = cl2 * cr2;
   cout << "Quotient of two complex numbers is: cs2 = cl2 * cr2 = "
        << cs2 << endl;

   // This is equivalent to the following operation
   cl2 *= cr2;
   cout << "Quotient of two complex numbers is also: cl2 *= cr2 = "
        << cl2 << endl;

   double abscl2 = abs ( cl2 );
   double argcl2 = arg ( cl2 );
   cout << "The modulus of cl2 is: " << abscl2 << endl;
   cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl;
}
```

## <a name="op_add_eq"></a>  complex::operator+=

Agrega un número a un número complejo de destino, donde el número agregado puede ser complejo o del mismo tipo que las partes reales e imaginarias del número complejo al que se agrega.

```cpp
template <class Other>
complex<Type>& operator+=(const complex<Other>& right);

complex<Type>& operator+=(const Type& right);

complex<Type>& operator+=(const complex<Type>& right);
```

### <a name="parameters"></a>Parámetros

*derecha* un número complejo o un número que es el mismo tipo que el parámetro del número complejo de destino.

### <a name="return-value"></a>Valor devuelto

Un número complejo que ha tenido el número especificado como un parámetro agregado.

### <a name="remarks"></a>Comentarios

La operación se sobrecarga para poder ejecutar operaciones aritméticas simples sin necesidad de conversión de datos a un formato determinado.

### <a name="example"></a>Ejemplo

```cpp
// complex_op_pe.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> added to type complex<double>
   complex <double> cl1 ( 3.0 , 4.0 );
   complex <double> cr1 ( 2.0 , -1.0 );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex <double> cs1 = cl1 + cr1;
   cout << "The sum of the two complex numbers is: cs1 = cl1 + cr1 = "
        << cs1 << endl;

   // This is equivalent to the following operation
   cl1 += cr1;
   cout << "The complex number cr1 added to the complex number cl1 is:"
        << "\n cl1 += cr1 = " << cl1 << endl;

   double abscl1 = abs ( cl1 );
   double argcl1 = arg ( cl1 );
   cout << "The modulus of cl1 is: " << abscl1 << endl;
   cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type double added to type complex<double>
   complex <double> cl2 ( -2 , 4 );
   double cr2 =5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex <double> cs2 = cl2 + cr2;
   cout << "The sum of the two complex numbers is: cs2 = cl2 + cr2 = "
        << cs2 << endl;

   // This is equivalent to the following operation
   cl2 += cr2;
   cout << "The complex number cr2 added to the complex number cl2 is:"
        << "\n cl2 += cr2 = " << cl2 << endl;

   double abscl2 = abs ( cl2 );
   double argcl2 = arg ( cl2 );
   cout << "The modulus of cl2 is: " << abscl2 << endl;
   cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl << endl;
}
```

```Output
The left-side complex number is cl1 = (3,4)
The right-side complex number is cr1 = (2,-1)
The sum of the two complex numbers is: cs1 = cl1 + cr1 = (5,3)
The complex number cr1 added to the complex number cl1 is:
 cl1 += cr1 = (5,3)
The modulus of cl1 is: 5.83095
The argument of cl1 is: 0.54042 radians, which is 30.9638 degrees.

The left-side complex number is cl2 = (-2,4)
The right-side complex number is cr2 = 5
The sum of the two complex numbers is: cs2 = cl2 + cr2 = (3,4)
The complex number cr2 added to the complex number cl2 is:
 cl2 += cr2 = (3,4)
The modulus of cl2 is: 5
The argument of cl2 is: 0.927295 radians, which is 53.1301 degrees.
```

## <a name="complex__operator-_eq"></a>  complex::operator-=

Resta un número de un número complejo de destino, donde el número restado puede ser complejo o del mismo tipo que las partes reales e imaginarias del número complejo al que se agrega.

```cpp
template <class Other>
complex<Type>& operator-=(const complex<Other>& complexNum);

complex<Type>& operator-=(const Type& _RealPart);

complex<Type>& operator-=(const complex<Type>& complexNum);
```

### <a name="parameters"></a>Parámetros

*complexNum* un número complejo que se restará el número complejo de destino.

*_RealPart* un número real que se restará el número complejo de destino.

### <a name="return-value"></a>Valor devuelto

Un número complejo que ha tenido el número especificado como un parámetro restado de él.

### <a name="remarks"></a>Comentarios

La operación se sobrecarga para poder ejecutar operaciones aritméticas simples sin necesidad de conversión de datos a un formato determinado.

### <a name="example"></a>Ejemplo

```cpp
// complex_op_se.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> subtracted from type complex<double>
   complex <double> cl1 ( 3.0 , 4.0 );
   complex <double> cr1 ( 2.0 , -1.0 );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex <double> cs1 = cl1 - cr1;
   cout << "The difference between the two complex numbers is:"
        << "\n cs1 = cl1 - cr1 = " << cs1 << endl;

   // This is equivalent to the following operation
   cl1 -= cr1;
   cout << "Complex number cr1 subtracted from complex number cl1 is:"
        << "\n cl1 -= cr1 = " << cl1 << endl;

   double abscl1 = abs ( cl1 );
   double argcl1 = arg ( cl1 );
   cout << "The modulus of cl1 is: " << abscl1 << endl;
   cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type double subtracted from type complex<double>
   complex <double> cl2 ( 2.0 , 4.0 );
   double cr2 = 5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex <double> cs2 = cl2 - cr2;
   cout << "The difference between the two complex numbers is:"
        << "\n cs2 = cl2 - cr2 = " << cs2 << endl;

   // This is equivalent to the following operation
   cl2  -= cr2;
   cout << "Complex number cr2 subtracted from complex number cl2 is:"
        << "\n cl2 -= cr2 = " << cl2 << endl;

   double abscl2 = abs ( cl2 );
   double argcl2 = arg ( cl2 );
   cout << "The modulus of cl2 is: " << abscl2 << endl;
   cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl << endl;
}
```

```Output
The left-side complex number is cl1 = (3,4)
The right-side complex number is cr1 = (2,-1)
The difference between the two complex numbers is:
 cs1 = cl1 - cr1 = (1,5)
Complex number cr1 subtracted from complex number cl1 is:
 cl1 -= cr1 = (1,5)
The modulus of cl1 is: 5.09902
The argument of cl1 is: 1.3734 radians, which is 78.6901 degrees.

The left-side complex number is cl2 = (2,4)
The right-side complex number is cr2 = 5
The difference between the two complex numbers is:
 cs2 = cl2 - cr2 = (-3,4)
Complex number cr2 subtracted from complex number cl2 is:
 cl2 -= cr2 = (-3,4)
The modulus of cl2 is: 5
The argument of cl2 is: 2.2143 radians, which is 126.87 degrees.
```

## <a name="op_div_eq"></a>  complex::operator/=

Divide un número complejo de destino por un divisor, que puede ser complejo o del mismo tipo, como lo son las partes reales e imaginarias del número complejo.

```cpp
template <class Other>
complex<Type>& operator/=(const complex<Other>& complexNum);

complex<Type>& operator/=(const Type& _RealPart);

complex<Type>& operator/=(const complex<Type>& complexNum);
```

### <a name="parameters"></a>Parámetros

*complexNum* un número complejo que se restará el número complejo de destino.

*_RealPart* un número real que se restará el número complejo de destino.

### <a name="return-value"></a>Valor devuelto

Un número complejo que se ha dividido por el número especificado como un parámetro.

### <a name="remarks"></a>Comentarios

La operación se sobrecarga para poder ejecutar operaciones aritméticas simples sin necesidad de conversión de datos a un formato determinado.

### <a name="example"></a>Ejemplo

```cpp
// complex_op_de.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> divided by type complex<double>
   complex <double> cl1 ( polar (3.0 , pi / 6 ) );
   complex <double> cr1 ( polar (2.0 , pi / 3 ) );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex <double> cs1 = cl1 / cr1;
   cout << "The quotient of the two complex numbers is: cs1 = cl1 /cr1 = "
        << cs1 << endl;

   // This is equivalent to the following operation
   cl1 /= cr1;
   cout << "Quotient of two complex numbers is also: cl1 /= cr1 = "
        << cl1 << endl;

   double abscl1 = abs ( cl1 );
   double argcl1 = arg ( cl1 );
   cout << "The modulus of cl1 is: " << abscl1 << endl;
   cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type complex<double> divided by type double
   complex <double> cl2 ( polar (3.0 , pi / 6 ) );
   double cr2 =5;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex <double> cs2 = cl2 / cr2;
   cout << "The quotient of the two complex numbers is: cs2 /= cl2 cr2 = "
        << cs2 << endl;

   // This is equivalent to the following operation
   cl2 /= cr2;
   cout << "Quotient of two complex numbers is also: cl2 = /cr2 = "
        << cl2 << endl;

   double abscl2 = abs ( cl2 );
   double argcl2 = arg ( cl2 );
   cout << "The modulus of cl2 is: " << abscl2 << endl;
   cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl << endl;
}
```

```Output
The left-side complex number is cl1 = (2.59808,1.5)
The right-side complex number is cr1 = (1,1.73205)
The quotient of the two complex numbers is: cs1 = cl1 /cr1 = (1.29904,-0.75)
Quotient of two complex numbers is also: cl1 /= cr1 = (1.29904,-0.75)
The modulus of cl1 is: 1.5
The argument of cl1 is: -0.523599 radians, which is -30 degrees.

The left-side complex number is cl2 = (2.59808,1.5)
The right-side complex number is cr2 = 5
The quotient of the two complex numbers is: cs2 /= cl2 cr2 = (0.519615,0.3)
Quotient of two complex numbers is also: cl2 = /cr2 = (0.519615,0.3)
The modulus of cl2 is: 0.6
The argument of cl2 is: 0.523599 radians, which is 30 degrees.
```

## <a name="op_eq"></a>  complex::operator=

Asigna un número a un número complejo de destino, donde el número asignado puede ser complejo o del mismo tipo que las partes reales e imaginarias del número complejo al que se está asignando.

```cpp
template <class Other>
complex<Type>& operator=(const complex<Other>& right);

complex<Type>& operator=(const Type& right);
```

### <a name="parameters"></a>Parámetros

*derecha* un número complejo o un número que es el mismo tipo que el parámetro del número complejo de destino.

### <a name="return-value"></a>Valor devuelto

Un número complejo al que se ha asignado el número especificado como un parámetro.

### <a name="remarks"></a>Comentarios

La operación se sobrecarga para poder ejecutar operaciones aritméticas simples sin necesidad de conversión de datos a un formato determinado.

### <a name="example"></a>Ejemplo

```cpp
// complex_op_as.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> assigned to type complex<double>
   complex <double> cl1 ( 3.0 , 4.0 );
   complex <double> cr1 ( 2.0 , -1.0 );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   cl1  = cr1;
   cout << "The complex number cr1 assigned to the complex number cl1 is:"
        << "\n cl1 = cr1 = " << cl1 << endl;

   // Example of the second member function
   // type double assigned to type complex<double>
   complex <double> cl2 ( -2 , 4 );
   double cr2 =5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   cl2 = cr2;
   cout << "The complex number cr2 assigned to the complex number cl2 is:"
        << "\n cl2 = cr2 = " << cl2 << endl;

   cl2 = complex<double>(3.0, 4.0);
   cout << "The complex number (3, 4) assigned to the complex number cl2 is:"
        << "\n cl2 = " << cl2 << endl;
}
```

```Output
The left-side complex number is cl1 = (3,4)
The right-side complex number is cr1 = (2,-1)
The complex number cr1 assigned to the complex number cl1 is:
 cl1 = cr1 = (2,-1)
The left-side complex number is cl2 = (-2,4)
The right-side complex number is cr2 = 5
The complex number cr2 assigned to the complex number cl2 is:
 cl2 = cr2 = (5,0)
The complex number (3, 4) assigned to the complex number cl2 is:
 cl2 = (3,4)
```

## <a name="real"></a>  complex::real

Obtiene o establece el componente real de un número complejo.

```cpp
constexpr T real() const;


T real(const T& right);
```

### <a name="parameters"></a>Parámetros

*derecha* un número complejo cuyo valor real es se va a extraer.

### <a name="return-value"></a>Valor devuelto

Parte real del número complejo.

### <a name="remarks"></a>Comentarios

Para un número complejo *a + bi*, la parte o componente real es *Re(a + bi) = a.*

### <a name="example"></a>Ejemplo

```cpp
// complex_class_real.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;

   complex <double> c1 ( 4.0 , 3.0 );
   cout << "The complex number c1 = " << c1 << endl;

   double dr1 = c1.real ( );
   cout << "The real part of c1 is c1.real ( ) = "
        << dr1 << "." << endl;

   double di1 = c1.imag ( );
   cout << "The imaginary part of c1 is c1.imag ( ) = "
        << di1 << "." << endl;
}
```

```Output
The complex number c1 = (4,3)
The real part of c1 is c1.real ( ) = 4.
The imaginary part of c1 is c1.imag ( ) = 3.
```

## <a name="value_type"></a>  complex::value_type

Tipo que representa el tipo de datos usado para representar las partes reales e imaginarias de un número complejo.

```

typedef Type value_type;
```

### <a name="remarks"></a>Comentarios

`value_type` es un sinónimo de la clase compleja `Type` parámetro de plantilla.

### <a name="example"></a>Ejemplo

```cpp
// complex_valuetype.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   complex <double>::value_type a = 3, b = 4;

   complex <double> c1 ( a , b );
   cout << "Specifying initial real & imaginary parts"
      << "\nof type value_type: "
      << "c1 = " << c1 << "." << endl;
}
```

```Output
Specifying initial real & imaginary parts
of type value_type: c1 = (3,4).
```

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
