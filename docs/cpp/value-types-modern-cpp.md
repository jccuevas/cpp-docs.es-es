---
title: Clases C++ como tipos de valor
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: f63bb62c-60da-40d5-ac14-4366608fe260
ms.openlocfilehash: 1aabcad46e848e1a499a142adaba5002a829bbf5
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246021"
---
# <a name="c-classes-as-value-types"></a>Clases C++ como tipos de valor

C++las clases son de forma predeterminada tipos de valor. Se pueden especificar como tipos de referencia, lo que permite que el comportamiento polimórfico admita la programación orientada a objetos. A veces, los tipos de valor se ven desde la perspectiva de la memoria y el control de diseño, mientras que los tipos de referencia son acerca de las clases base y las funciones virtuales para propósitos polimórficos. De forma predeterminada, los tipos de valor se pueden copiar, lo que significa que siempre hay un constructor de copias y un operador de asignación de copia. En el caso de los tipos de referencia, hace que la clase sea no copiable (deshabilite el constructor de copias y el operador de asignación de copia) y use un destructor virtual, que admite el polimorfismo previsto. Los tipos de valor también son sobre el contenido, que, cuando se copian, siempre proporcionan dos valores independientes que se pueden modificar por separado. Tipos de referencia sobre identidad: ¿Qué tipo de objeto es? Por este motivo, los "tipos de referencia" también se conocen como "tipos polimórficos".

Si realmente desea un tipo de referencia (clase base, funciones virtuales), debe deshabilitar explícitamente la copia, como se muestra en la clase `MyRefType` en el código siguiente.

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

Al compilar el código anterior se producirá el siguiente error:

```Output
test.cpp(15) : error C2248: 'MyRefType::operator =' : cannot access private member declared in class 'MyRefType'
        meow.cpp(5) : see declaration of 'MyRefType::operator ='
        meow.cpp(3) : see declaration of 'MyRefType'
```

## <a name="value-types-and-move-efficiency"></a>Tipos de valor y eficiencia de movimiento

La sobrecarga de asignación de copia se evita debido a nuevas optimizaciones de copia. Por ejemplo, al insertar una cadena en medio de un vector de cadenas, no habrá ninguna sobrecarga de reasignación de copia, solo un movimiento, incluso si se produce un aumento del propio vector. Esto también se aplica a otras operaciones, por ejemplo, realizar una operación de agregar en dos objetos de gran tamaño. ¿Cómo se habilitan estas optimizaciones de operaciones de valores? En algunos C++ compiladores, el compilador lo habilitará de forma implícita, al igual que el compilador puede generar automáticamente los constructores de copia. Sin embargo, C++en, la clase deberá "participar" para trasladar la asignación y los constructores declarándolos en la definición de clase. Esto se logra mediante el uso de la referencia rvalue de comillas dobles (& &) en las declaraciones de función miembro apropiadas y la definición de los métodos de asignación y movimiento del constructor de movimiento.  También debe insertar el código correcto para "robar el Trip" del objeto de origen.

¿Cómo se decide si se necesita el traslado habilitado? Si ya sabe que necesita la construcción de copias habilitada, es probable que desee habilitar el movimiento si puede ser más barato que una copia en profundidad. Sin embargo, si sabe que necesita la compatibilidad con Move, no significa necesariamente que desee que la copia esté habilitada. Este último caso se denominaría "tipo de solo movimiento". Un ejemplo que ya está en la biblioteca estándar es `unique_ptr`. Como nota lateral, el `auto_ptr` antiguo está en desuso y se ha reemplazado por `unique_ptr` precisamente debido a la falta de compatibilidad con la semántica de transferencia en la versión C++anterior de.

Mediante el uso de la semántica de movimiento, puede devolver por valor o insertar en el medio. Move es una optimización de la copia. La asignación del montón es necesaria como solución alternativa. Considere el siguiente seudocódigo:

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

### <a name="enabling-move-for-appropriate-value-types"></a>Habilitar Move para tipos de valor adecuados

En el caso de una clase de valor, donde el movimiento puede ser más barato que una copia en profundidad, habilite la construcción de movimiento y la asignación de movimiento para mayor eficacia. Considere el siguiente seudocódigo:

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

Si habilita la construcción/asignación de copia, habilite también la construcción o asignación de movimiento si puede ser más barata que una copia en profundidad.

Algunos tipos *que no son de valor* son de solo movimiento, como cuando no se puede clonar un recurso, solo se transfiere la propiedad. Ejemplo: `unique_ptr`.

## <a name="see-also"></a>Vea también

[C++sistema de tipos](../cpp/cpp-type-system-modern-cpp.md)<br/>
[Bienvenido de nuevo aC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
