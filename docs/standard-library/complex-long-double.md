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
ms.openlocfilehash: 5de4fc2305ef2ac6e523dcb02782455245b99429
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302346"
---
# <a name="complexltlong-doublegt"></a>complex&lt;long double&gt;

Esta plantilla de clase especializada explícitamente describe un objeto que almacena un par ordenado de objetos, ambos de tipo **Long Double**, el primero que representa la parte real de un número complejo y el segundo representa la parte imaginaria.

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

// rest same as class template complex
};
```

### <a name="parameters"></a>Parameters

*_RealVal*\
Valor de tipo **long double** de la parte real del número complejo que se está construyendo.

*_ImagVal*\
Valor de tipo **Long Double** para la parte imaginaria del número complejo que se está construyendo.

\ *complexNum*
Número complejo de tipo **Double** o de tipo **float** cuyas partes reales e imaginarias se usan para inicializar un número complejo de tipo **Long Double** que se va a construir.

## <a name="return-value"></a>Valor devuelto

Un número complejo de tipo **Long Double**.

## <a name="remarks"></a>Notas

La especialización explícita de la plantilla de clase `complex` a una clase compleja de tipo **Long Double** difiere de la plantilla de clase solo en los constructores que define. Se permite que la conversión de **Long Double** a **float** sea implícita, pero la conversión de **Double** a **Long Double** debe ser **explícita**. El uso de la conversión **explícita** descarta el inicio con la conversión de tipos mediante sintaxis de asignación.

Para obtener más información sobre la plantilla de clase `complex` y sus miembros, vea [Complex (clase](../standard-library/complex-class.md)).

**Específico de Microsoft**: los tipos **Long Double** y **Double** tienen la misma representación, pero son tipos distintos. Para obtener más información, vea [tipos integrados](../cpp/fundamental-types-cpp.md).

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

## <a name="requirements"></a>Requisitos de

**Encabezado**: \<complex>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[complex (Clase)](../standard-library/complex-class.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
