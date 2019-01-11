---
title: Tipos de valor (C++ moderno)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f63bb62c-60da-40d5-ac14-4366608fe260
ms.openlocfilehash: 32cdb29ec1c59081ad7e0493888f290f21561d2b
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220353"
---
# <a name="value-types-modern-c"></a>Tipos de valor (C++ moderno)

Las clases de C++ son tipos de valor predeterminado. En este tema se proporciona una introducción de tipos de valor y los problemas relacionados con su uso.

## <a name="value-vs-reference-types"></a>Valor frente a tipos de referencia

Como se mencionó anteriormente, las clases de C++ son tipos de valor predeterminado. Se pueden especificar como tipos de referencia, lo que permite un comportamiento polimórfico admitir la programación orientada a objetos. Tipos de valor a veces se ven desde la perspectiva de control de memoria y el diseño, mientras que son tipos de referencia acerca de las clases base y funciones virtuales fines polimórfico. De forma predeterminada, los tipos de valor son copiar, lo que significa que siempre hay un constructor de copias y un operador de asignación de copia. Tipos de referencia, hace que la clase no se puede copiar (deshabilitar el constructor de copias y un operador de asignación de copia) y usar un destructor virtual, que es compatible con su polimorfismo previsto. Tipos de valor están también relacionados con el contenido que, cuando se copian, siempre le ofrece dos valores independientes que se pueden modificar por separado. ¿Son tipos de referencia acerca de la identidad - el tipo de objeto es? Por este motivo, "tipos de referencia" también se conocen como "tipos polimórficos".

Si desea realmente un tipo de referencia similar (clase base, las funciones virtuales), deberá deshabilitar explícitamente la copia, como se muestra en el `MyRefType` clase en el código siguiente.

```cpp
// cl /EHsc /nologo /W4

class MyRefType {
private:
    MyRefType & operator=(const MyRefType &);
    MyRefType(const MyRefType &);
public:
    MyRefType () {}
};

int main()
{
    MyRefType Data1, Data2;
    // ...
    Data1 = Data2;
}
```

Compilar el código anterior dará como resultado el siguiente error:

```Output
test.cpp(15) : error C2248: 'MyRefType::operator =' : cannot access private member declared in class 'MyRefType'
        meow.cpp(5) : see declaration of 'MyRefType::operator ='
        meow.cpp(3) : see declaration of 'MyRefType'
```

## <a name="value-types-and-move-efficiency"></a>Tipos de valor y mover la eficacia

Se evita la sobrecarga de asignación de copia debido a optimizaciones de copia de nuevo. Por ejemplo, cuando se inserta una cadena en el medio de un vector de cadenas, no habrá ninguna sobrecarga de reasignación de copia, sólo un movimiento - incluso si da como resultado un aumento del vector propio. Esto se aplica también a otras operaciones, por ejemplo realizar una operación de agregar en dos objetos muy grandes. ¿Cómo habilitar estas optimizaciones de operación valor? En algunos compiladores de C++, el compilador habilitará esto por usted implícitamente, al igual que el compilador pueden generarse automáticamente constructores de copia. Sin embargo, en Visual C++, su clase necesitará "participar en" para mover la asignación y constructores declarándolo en la definición de clase. Esto se logra mediante el uso de la y comercial doble (& &) referencia rvalue del miembro adecuado de declaraciones y definición de constructor de movimiento de funciones y los métodos de asignación de desplazamiento.  También deberá insertar el código correcto para "robar las interioridades" fuera el objeto de origen.

¿Cómo se decide si necesita mover habilitado? Si ya sabe que necesita copiar construcción habilitado, probablemente desee mover habilitado si puede ser más barato que una copia en profundidad. Sin embargo, si sabe que necesita mover soporte técnico, no significa necesariamente que desea copia habilitado. Este último caso, se llama un "Mover tipo solo". Es un ejemplo ya está en la biblioteca estándar de `unique_ptr`. Como una nota al margen, la antigua `auto_ptr` está en desuso y se ha sustituido por `unique_ptr` debido precisamente a la falta de compatibilidad de la semántica de movimiento en la versión anterior de C++.

Mediante el uso de la semántica de movimiento puede valor devuelto o insertar en medio. Movimiento es una optimización de copia. No hay necesidad de asignación del montón como solución alternativa. Considere el siguiente seudocódigo:

```cpp
#include <set>
#include <vector>
#include <string>
using namespace std;

//...
set<widget> LoadHugeData() {
    set<widget> ret;
    // ... load data from disk and populate ret
    return ret;
}
//...
widgets = LoadHugeData();   // efficient, no deep copy

vector<string> v = IfIHadAMillionStrings();
v.insert( begin(v)+v.size()/2, "scott" );   // efficient, no deep copy-shuffle
v.insert( begin(v)+v.size()/2, "Andrei" );  // (just 1M ptr/len assignments)
//...
HugeMatrix operator+(const HugeMatrix& , const HugeMatrix& );
HugeMatrix operator+(const HugeMatrix& ,       HugeMatrix&&);
HugeMatrix operator+(      HugeMatrix&&, const HugeMatrix& );
HugeMatrix operator+(      HugeMatrix&&,       HugeMatrix&&);
//...
hm5 = hm1+hm2+hm3+hm4+hm5;   // efficient, no extra copies
```

### <a name="enabling-move-for-appropriate-value-types"></a>Habilitación de movimiento para los tipos de valor adecuado

Para una clase de valor similar a donde mover puede ser más barato que una copia en profundidad, permiten la construcción de movimiento y mover la asignación para mejorar la eficacia. Considere el siguiente seudocódigo:

```cpp
#include <memory>
#include <stdexcept>
using namespace std;
// ...
class my_class {
    unique_ptr<BigHugeData> data;
public:
    my_class( my_class&& other )   // move construction
        : data( move( other.data ) ) { }
    my_class& operator=( my_class&& other )   // move assignment
    { data = move( other.data ); return *this; }
    // ...
    void method() {   // check (if appropriate)
        if( !data )
            throw std::runtime_error("RUNTIME ERROR: Insufficient resources!");
    }
};
```

Si habilita la construcción/asignación de copia, también habilitar construcción/asignación de movimiento si puede ser más barato que una copia en profundidad.

Algunos *sin valor* tipos son de solo movimiento, por ejemplo, cuando no se puede clonar un recurso, sólo transferir la propiedad. Ejemplo: `unique_ptr`.

## <a name="section"></a>Sección

Contenido

## <a name="see-also"></a>Vea también

[Sistema de tipos de C++ (C++ moderno)](../cpp/cpp-type-system-modern-cpp.md)<br/>
[Aquí está otra vez C++ (C++ moderno)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
