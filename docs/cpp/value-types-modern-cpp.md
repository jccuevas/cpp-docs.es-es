---
title: "Tipos de valor (C++ moderno) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: f63bb62c-60da-40d5-ac14-4366608fe260
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tipos de valor (C++ moderno)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las clases de C\+\+ son de forma predeterminada tipos de valor.  Este tema proporciona información general de introducción de tipos de valor y de problemas relacionados con su uso.  
  
## Valor con tipos de referencia  
 Como se indicó anteriormente, las clases de C\+\+ son de forma predeterminada tipos de valor.  Se pueden especificar como tipos de referencia, que permiten a comportamiento polimórfico para admitir la programación orientada a objetos.  Vea los tipos de valor a veces desde la perspectiva del control de memoria y de diseño, mientras que los tipos de referencia se sobre clases base y funciones virtuales para fines polimórficos.  De forma predeterminada, los tipos de valor son se puede copiar, que significa que siempre hay un constructor de copias y operador de asignación de copia.  Para los tipos de referencia, se crea la clase no \- se puede copiar \(deshabilitar el constructor de copias y el operador de asignación de copia\) y utiliza un destructor virtual, que admite el polimorfismo previsto.  Los tipos de valor están también sobre el contenido, que, cuando los copian, siempre se tienen dos valores independientes que se pueden modificar por separado.  ¿Los tipos de referencia se sobre identidad – qué tipo de objeto es?  Por esta razón, “tipos de referencia” también se conocen como “tipos polimórficos”.  
  
 Si desea realmente a referencia\- como tipo \(clase base, funciones virtuales\), debe deshabilitarse la copia, tal y como se muestra en la clase de `MyRefType` en el código siguiente.  
  
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
  
 La compilación del código anterior provocará el siguiente error:  
  
  **test.cpp \(15\): error C2248: “MyRefType::operator \=”: no puede tener acceso al miembro privado declarado en MyRefType de clases”**  
 **meow.cpp \(5\): vea la declaración de “MyRefType::operator \=”**  
 **meow.cpp \(3\): vea la declaración de “MyRefType”**   
## Tipos de valor y eficacia de movimiento  
 La sobrecarga de la asignación de copia es evitar debido a las nuevas optimizaciones de copia.  Por ejemplo, cuando se inserta una cadena en medio de un vector de cadenas, no habrá sobrecarga de reasignación de copia, solo un movimiento aunque produce un crecimiento vectoriales propio.  Esto también se aplica a otras operaciones, como operaciones de agregar en dos objetos muy grandes.  ¿Cómo habilita estas optimizaciones de la operación de valor?  En algunos compiladores de C\+\+, el compilador habilitará esto para se implícitamente, como constructores de copia se puede generar automáticamente por el compilador.  Sin embargo, en Visual C\+\+, la clase necesitará “pertenencia” mover la asignación y constructores mediante declaración en la definición de clase.  Esto se logra mediante la referencia doble rvalue de y comercial \(&&\) en las declaraciones de función adecuadas y la definición de miembros de métodos de constructor de movimiento y asignar move.  También necesita insertar código correcto “roba la tripa” fuera del objeto de origen.  
  
 ¿Cómo se decide si necesita el movimiento habilitado?  Si sabe ya necesita la construcción habilitada, lo copia desea probablemente el movimiento habilitado si puede ser más barato que una copia profunda.  Sin embargo, si sabe necesita compatibilidad de movimiento, no significa necesariamente que desee la copia habilitada.  Este último caso sería denominado “movimiento \- solo tipo”.  Un ejemplo ya en la biblioteca estándar es `unique_ptr`.  Como nota lateral, `auto_ptr` antiguo es desuso, y se ha reemplazado por `unique_ptr` exacto debido a la falta de compatibilidad de la semántica de transferencia de recursos en la versión anterior de C\+\+.  
  
 Mediante la semántica de movimiento puede retorno\-por\- valor o INSERT\-en\- medio.  El movimiento es una optimización de copia.  Hay necesidad de asignación de pila como solución.  Considere el pseudocódigo siguiente:  
  
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
  
### Habilitar el movimiento de los tipos de valor adecuados  
 Para a siguiente valor como la clase donde el movimiento puede ser más barato que una copia profunda, habilitar la construcción de movimiento y la asignación de movimiento para aumentar la eficacia.  Considere el pseudocódigo siguiente:  
  
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
  
 Si habilita la construcción y la asignación de copia, también habilita la construcción y la asignación de movimiento si puede ser más económica que una copia profunda.  
  
 Algunos tipos *de valor no* son movimiento \- solo, por ejemplo cuando no puede clonar un recurso, solo la propiedad de la transferencia.  Ejemplo: `unique_ptr`.  
  
## Sección  
 Content  
  
## Vea también  
 [Sistema de tipos de C\+\+](../cpp/cpp-type-system-modern-cpp.md)   
 [Aquí está otra vez C\+\+](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referencia de lenguaje C\+\+](../cpp/cpp-language-reference.md)   
 [Biblioteca estándar de C\+\+](../standard-library/cpp-standard-library-reference.md)