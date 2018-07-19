---
title: Valor de tipos (C++ moderno) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f63bb62c-60da-40d5-ac14-4366608fe260
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7e49c97bca86b8d2debde2f5b132f7dde16998e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32423423"
---
# <a name="value-types-modern-c"></a>Tipos de valor (C++ moderno)
Las clases de C++ son tipos de valor predeterminado. Este tema proporciona información general introductoria de tipos de valor y problemas relacionados con su uso.  
  
## <a name="value-vs-reference-types"></a>Valor frente a tipos de referencia  
 Como se mencionó anteriormente, las clases de C++ son tipos de valor predeterminado. Se pueden especificar como tipos de referencia, que permiten un comportamiento polimórfico admitir la programación orientada a objetos. Tipos de valor a veces se ven desde la perspectiva del control de memoria y el diseño, mientras que son tipos de referencia acerca de las clases base y las funciones virtuales fines polimórfico. De forma predeterminada, los tipos de valor son se puede copiar, lo que significa que siempre hay un constructor de copias y un operador de asignación de copia. Para los tipos de referencia, haga que la clase no se puede copiar (deshabilitar el constructor de copias y un operador de asignación de copia) y utiliza un destructor virtual, que admite el polimorfismo previsto. Tipos de valor también están relacionados con el contenido, lo que, cuando se copian, siempre proporcionará dos valores independientes que se pueden modificar por separado. ¿Tipos de referencia están relacionados con identidad - qué tipo de objeto es? Por esta razón, "tipos de referencia" también se conocen como "tipos polimórficos".  
  
 Si realmente desea un tipo de referencia similar (clase base, las funciones virtuales), deberá deshabilitar explícitamente copiar, tal y como se muestra en el `MyRefType` clase en el código siguiente.  
  
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
  
 Compilar el código anterior se producirá el error siguiente:  
  
```Output  
test.cpp(15) : error C2248: 'MyRefType::operator =' : cannot access private member declared in class 'MyRefType'  
        meow.cpp(5) : see declaration of 'MyRefType::operator ='  
        meow.cpp(3) : see declaration of 'MyRefType'  
  
```  
  
## <a name="value-types-and-move-efficiency"></a>Los tipos de valor y mover la eficacia  
 Se evita la sobrecarga de asignación de copia debido a optimizaciones de copia de nuevo. Por ejemplo, cuando se inserta una cadena en el medio de un vector de cadenas, no habrá ninguna sobrecarga de reasignación de copia, solo un movimiento - incluso si se produce un aumento del vector propio. Esto se aplica también a otras operaciones, por ejemplo realizar una operación de agregar en dos objetos muy grandes. ¿Cómo se habilita estas optimizaciones de operación de valor? En algunos compiladores de C++, el compilador permitirá esto por usted implícitamente, mucho como constructores de copias se pueden generar automáticamente por el compilador. Sin embargo, en Visual C++, puede que su clase necesitará que "opt" para mover la asignación y constructores declarándolo en la definición de clase. Esto se logra mediante el doble signo de y comercial (& &) referencia de valor r en el miembro correspondiente función declaraciones y el constructor de movimiento definición y los métodos de asignación de desplazamiento.  También debe insertar el código correcto para "robar muestra el" objeto de origen.  
  
 ¿Cómo se decide si necesita mover habilitado? Si ya sabe que necesita copiar construcción habilitado, probablemente desee mover habilitado si puede ser más económico que una copia en profundidad. Sin embargo, si sabe que necesita mover soporte técnico, no significa necesariamente que desea copiar habilitado. Este último caso, se llama un "solo movimiento tipo". Es un ejemplo ya se encuentran en la biblioteca estándar de `unique_ptr`. Como una nota al margen, la antigua `auto_ptr` está en desuso y se sustituyó por `unique_ptr` debido precisamente a la falta de compatibilidad de la semántica de movimiento en la versión anterior de C++.  
  
 Mediante la semántica de movimiento puede valor devuelto o insert en medio. Movimiento es una optimización de copia. No hay necesidad de asignación en el montón para solucionar este problema. Considere el siguiente seudocódigo:  
  
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
  
### <a name="enabling-move-for-appropriate-value-types"></a>Habilitar movimiento para los tipos de valor adecuado  
 Para una clase de tipo de valor en movimiento puede ser más económico que una copia en profundidad, permiten la construcción de movimiento y mover la asignación para mejorar la eficacia. Considere el siguiente seudocódigo:  
  
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
  
 Si habilita la construcción/asignación de copia, habilitar construcción/asignación de movimiento si puede ser más económico que una copia en profundidad.  
  
 Algunos *sin valor* tipos son solo de movimiento, por ejemplo, cuando no se puede clonar un recurso, sólo transferir la propiedad. Ejemplo: `unique_ptr`.  
  
## <a name="section"></a>Sección  
 Contenido  
  
## <a name="see-also"></a>Vea también  
 [Sistema de tipos de C++](../cpp/cpp-type-system-modern-cpp.md)   
 [Aquí está otra vez C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)   
 [Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)