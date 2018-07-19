---
title: complex&lt;double&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- complex/std::complex<double>
dev_langs:
- C++
helpviewer_keywords:
- complex<double> function
ms.assetid: 0d0b9d2a-9b9b-410b-82a0-86b6df127e47
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72f7b6e352240498f921c9aa5c3d1a990da34813
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955434"
---
# <a name="complexltdoublegt"></a>complex&lt;double&gt;

Describe un objeto que almacena un par ordenado de objetos de tipo **doble***,* el primero representa la parte real de un número complejo y el segundo representa la parte imaginaria.

## <a name="syntax"></a>Sintaxis

```cpp
template <>
class complex<double> {
public:
    constexpr complex(
    double RealVal = 0,
    double ImagVal = 0);

constexpr complex(const complex<double>& complexNum);

constexpr explicit complex(const complex<long double>& complexNum);
// rest same as template class complex
};
```

### <a name="parameters"></a>Parámetros

*RealVal* el valor de tipo **doble** de la parte real del número complejo que se está construyendo.

*ImagVal* el valor de tipo **doble** de la parte imaginaria del número complejo que se está construyendo.

*complexNum* número complejo de tipo **float** o de tipo **long double** cuyas partes reales e imaginarias se usan para inicializar un número complejo de tipo **doble**que se está construyendo.

## <a name="return-value"></a>Valor devuelto

Número complejo de tipo **double**.

## <a name="remarks"></a>Comentarios

La especialización explícita de la clase de plantilla compleja en una clase compleja de tipo **double** solo se distingue de la clase de plantilla en los constructores que define. La conversión de **float** a **doble** puede ser implícita, pero la conversión de **long double** a **doble** debe ser **explícita**. El uso de la conversión **explícita** descarta el inicio con la conversión de tipos mediante sintaxis de asignación.

Para obtener más información sobre la clase de plantilla `complex`, vea [complex (Clase)](../standard-library/complex-class.md). Para obtener una lista de los miembros de la clase de plantilla `complex`, vea .

## <a name="example"></a>Ejemplo

```cpp
// complex_comp_dbl.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // The first constructor specifies real & imaginary parts
   complex <double> c1 ( 4.0 , 5.0 );
   cout << "Specifying initial real & imaginary parts,\n"
        << " as type double gives c1 = " << c1 << endl;

   // The second constructor initializes values of the real &
   // imaginary parts using those of complex number of type float
   complex <float> c2float ( 4.0 , 5.0 );
   complex <double> c2double ( c2float );
   cout << "Implicit conversion from type float to type double,"
        << "\n gives c2double = " << c2double << endl;

   // The third constructor initializes values of the real &
   // imaginary parts using those of a complex number
   // of type long double
   complex <long double> c3longdouble ( 4.0 , 5.0 );
   complex <double> c3double ( c3longdouble );
   cout << "Explicit conversion from type float to type double,"
        << "\n gives c3longdouble = " << c3longdouble << endl;

   // The modulus and argument of a complex number can be recovered
   double absc3 = abs ( c3longdouble );
   double argc3 = arg ( c3longdouble );
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "
        << absc3 << endl;
   cout << "Argument of c3 is recovered from c3 using:\n arg ( c3 ) = "
        << argc3 << " radians, which is " << argc3 * 180 / pi
        << " degrees." << endl;
}
\* Output:
Specifying initial real & imaginary parts,
 as type double gives c1 = (4,5)
Implicit conversion from type float to type double,
 gives c2double = (4,5)
Explicit conversion from type float to type double,
 gives c3longdouble = (4,5)
The modulus of c3 is recovered from c3 using: abs ( c3 ) = 6.40312
Argument of c3 is recovered from c3 using:
 arg ( c3 ) = 0.896055 radians, which is 51.3402 degrees.
*\
```

## <a name="requirements"></a>Requisitos

**Encabezado**: \<complex>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[complex (Clase)](../standard-library/complex-class.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
