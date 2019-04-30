---
title: complex&lt;long double&gt;
ms.date: 11/04/2016
f1_keywords:
- std::complex<long double>
- complex<long double>
- std.complex<long double>
helpviewer_keywords:
- complex<long double> function
ms.assetid: 37591991-b385-46e9-b727-d534dbc10432
ms.openlocfilehash: 19d4569523879911209bf0c05e762eba2c9852a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389182"
---
# <a name="complexltlong-doublegt"></a>complex&lt;long double&gt;

Esta clase de plantilla especializada de forma explícita describe un objeto que almacena un par ordenado de objetos, ambos de tipo **long double**, el primero representa la parte real de un número complejo y el segundo representa la parte imaginaria.

## <a name="syntax"></a>Sintaxis

```cpp
template <>
class complex<long double> {
public:
    constexpr complex(
    long double _RealVal = 0,
    long double _ImagVal = 0);

complex(
    constexpr complex<long double>& complexNum);

// rest same as template class complex
};
```

### <a name="parameters"></a>Parámetros

*_RealVal*<br/>
Valor de tipo **long double** de la parte real del número complejo que se está construyendo.

*_ImagVal*<br/>
El valor de tipo **long double** de la parte imaginaria del número complejo que se está construyendo.

*complexNum*<br/>
El número complejo de tipo **doble** o de tipo **float** cuyas partes reales e imaginarias se usan para inicializar un número complejo de tipo **long double** que se está construyendo.

## <a name="return-value"></a>Valor devuelto

Un número complejo de tipo **long double**.

## <a name="remarks"></a>Comentarios

La especialización explícita de la clase de plantilla `complex` en una clase compleja de tipo **long double** difiere solo en los constructores que define la clase de plantilla. La conversión de **long double** a **float** puede ser implícita, pero la conversión de **doble** a **long double** es necesario para ser **explícita**. El uso de la conversión **explícita** descarta el inicio con la conversión de tipos mediante sintaxis de asignación.

Para obtener más información sobre la clase de plantilla `complex` y sus miembros, vea [complex (clase)](../standard-library/complex-class.md).

**Específico de Microsoft**: El **long double** y **doble** tipos tienen la misma representación, pero son tipos distintos. Para obtener más información, consulte [tipos fundamentales](../cpp/fundamental-types-cpp.md).

## <a name="example"></a>Ejemplo

```cpp
// complex_comp_ld.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
    using namespace std;
    double pi = 3.14159265359;

    // The first constructor specifies real & imaginary parts
    complex<long double> c1( 4.0 , 5.0 );
    cout << "Specifying initial real & imaginary parts,\n"
        << " as type float gives c1 = " << c1 << endl;

    // The second constructor initializes values of the real &
    // imaginary parts using those of complex number of type float
    complex<float> c2float( 1.0 , 3.0 );
    complex<long double> c2longdouble ( c2float );
    cout << "Implicit conversion from type float to type long double,"
        << "\n gives c2longdouble = " << c2longdouble << endl;

    // The third constructor initializes values of the real &
    // imaginary parts using those of a complex number
    // of type double
    complex<double> c3double( 3.0 , 4.0 );
    complex<long double> c3longdouble( c3double );
    cout << "Implicit conversion from type long double to type float,"
        << "\n gives c3longdouble = " << c3longdouble << endl;

    // The modulus and argument of a complex number can be recovered
    double absc3 = abs( c3longdouble );
    double argc3 = arg( c3longdouble );
    cout << "The modulus of c3 is recovered from c3 using: abs( c3 ) = "
        << absc3 << endl;
    cout << "Argument of c3 is recovered from c3 using:\n arg( c3 ) = "
        << argc3 << " radians, which is " << argc3 * 180 / pi
        << " degrees." << endl;
}
```

```Output
Specifying initial real & imaginary parts,
as type float gives c1 = (4,5)
Implicit conversion from type float to type long double,
gives c2longdouble = (1,3)
Implicit conversion from type long double to type float,
gives c3longdouble = (3,4)
The modulus of c3 is recovered from c3 using: abs( c3 ) = 5
Argument of c3 is recovered from c3 using:
arg( c3 ) = 0.927295 radians, which is 53.1301 degrees.
```

## <a name="requirements"></a>Requisitos

**Encabezado**: \<complex>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[complex (Clase)](../standard-library/complex-class.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
