---
title: "Alias y definiciones de tipos (C++) | Microsoft Docs"
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
  - "typedef"
dev_langs: 
  - "C++"
ms.assetid: af1c24d2-4bfd-408a-acfc-482e264232f5
caps.latest.revision: 18
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Alias y definiciones de tipos (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se puede utilizar una *declaración de alias* para declarar un nombre que se usará como sinónimo para un tipo declarado previamente.  \(Este mecanismo también se conoce informalmente como *alias de tipo*\).  También se puede utilizar este mecanismo para crear una *plantilla de alias*, que puede resultar especialmente útil para los asignadores personalizados.  
  
## Sintaxis  
  
```  
  
using identifier = type;  
```  
  
## Comentarios  
 `identifier`  
 Nombre del alias.  
  
 `type`  
 Identificador de tipo para el que se va a crear un alias.  
  
 Un alias no presenta un tipo nuevo y no puede cambiar el significado de un nombre de tipo existente.  
  
 El formato más sencillo de alias es equivalente al mecanismo `typedef` de C\+\+03:  
  
```cpp  
  
// C++11  
using counter = long;  
  
// C++03 equivalent:  
// typedef long counter;  
  
```  
  
 Ambos permiten la creación de variables de tipo "contador".  Algo más útil sería un alias de tipo como este para `std::ios_base::fmtflags`:  
  
```cpp  
  
// C++11  
using fmtfl = std::ios_base::fmtflags;  
// C++03 equivalent:  
// typedef std::ios_base::fmtflags fmtfl;  
  
fmtfl fl_orig = std::cout.flags();  
fmtfl fl_hex = (fl_orig & ~std::cout.basefield) | std::cout.showbase | std::cout.hex;  
// ...  
std::cout.flags(fl_hex);  
  
```  
  
 Los alias también funcionan con punteros a función, pero son mucho más legibles que el equivalente de typedef:  
  
```cpp  
  
// C++11  
using func = void(*)(int);  
  
// C++03 equivalent:  
// typedef void (*func)(int);  
  
// func can be assigned to a function pointer value  
void actual_function(int arg) { /* some code */ }  
func fptr = &actual_function;  
  
```  
  
 Una limitación del mecanismo `typedef` es que no funciona con plantillas.  Sin embargo, la sintaxis de alias de tipo de C\+\+11 permite la creación de plantillas de alias:  
  
```cpp  
template<typename T> using ptr = T*;   
  
// the name 'ptr<T>' is now an alias for pointer to T  
ptr<int> ptr_int;  
  
```  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar una plantilla de alias con un asignador personalizado; en este caso, un tipo de vector entero.  Puede sustituir cualquier tipo por `int` para crear un alias adecuado con el fin de ocultar las listas de parámetros complejos en el código funcional principal.  El uso del asignador personalizado en todo el código puede mejorar la legibilidad y reducir el riesgo de introducir errores debidos a errores ortográficos.  
  
```cpp  
  
#include <stdlib.h>  
#include <new>  
  
template <typename T> struct MyAlloc {  
    typedef T value_type;  
  
    MyAlloc() { }  
    template <typename U> MyAlloc(const MyAlloc<U>&) { }  
  
    bool operator==(const MyAlloc&) const { return true; }  
    bool operator!=(const MyAlloc&) const { return false; }  
  
    T * allocate(const size_t n) const {  
        if (n == 0) {  
            return nullptr;  
        }  
  
        if (n > static_cast<size_t>(-1) / sizeof(T)) {  
            throw std::bad_array_new_length();  
        }  
  
        void * const pv = malloc(n * sizeof(T));  
  
        if (!pv) {  
            throw std::bad_alloc();  
        }  
  
        return static_cast<T *>(pv);  
    }  
  
    void deallocate(T * const p, size_t) const {  
        free(p);  
    }  
};  
  
#include <vector>  
using MyIntVector = std::vector<int, MyAlloc<int>>;  
  
#include <iostream>  
  
int main ()   
{  
    MyIntVector foov = { 1701, 1764, 1664 };  
  
    for (auto a: foov) std::cout << a << " ";  
    std::cout << "\n";  
  
    return 0;  
}  
```  
  
## Salida  
  **1701 1764 1664**   
## Definiciones de tipo  
 Una declaración `typedef` introduce un nombre que, dentro de su ámbito, se convierte en un sinónimo del tipo especificado por la parte *type\-declaration* de la declaración.  
  
 Puede utilizar declaraciones typedef para construir nombres más cortos o más significativos para tipos ya definidos por el lenguaje o para tipos que ha declarado.  Los nombres de typedef permiten encapsular detalles de la implementación que pueden cambiar.  
  
 A diferencia de las declaraciones **class**, `struct`, **union** y `enum`, las declaraciones `typedef` no introducen tipos nuevos, sino nombres nuevos para tipos existentes.  
  
 Los nombres declarados con `typedef` ocupan el mismo espacio de nombres que otros identificadores \(excepto las etiquetas de instrucciones\).  Por consiguiente, no pueden utilizar el mismo identificador que un nombre declarado previamente, excepto en una declaración de tipo de clase.  Considere el ejemplo siguiente:  
  
```  
// typedef_names1.cpp  
// C2377 expected  
typedef unsigned long UL;   // Declare a typedef name, UL.  
int UL;                     // C2377: redefined.  
```  
  
 Las reglas de nombres ocultos que pertenecen a otros identificadores también controlan la visibilidad de los nombres declarados con `typedef`.  Por consiguiente, el ejemplo siguiente es válido en C\+\+:  
  
```  
// typedef_names2.cpp  
typedef unsigned long UL;   // Declare a typedef name, UL  
int main()  
{  
   unsigned int UL;   // Redeclaration hides typedef name  
}  
  
// typedef UL back in scope  
```  
  
-   [Nueva declaración de nombres de typedef](../misc/redeclaration-of-typedef-names.md)  
  
-   [Uso de typedef con tipos de clase](../misc/use-of-typedef-with-class-types.md)  
  
-   [Espacio de nombres de los nombres de definiciones de tipo](../misc/name-space-of-typedef-names.md)  
  
```  
// typedef_specifier1.cpp  
typedef char FlagType;  
  
int main()  
{  
}  
  
void myproc( int )  
{  
    int FlagType;  
}  
```  
  
 Al declarar un identificador de ámbito local con el mismo nombre que un typedef, o al declarar un miembro de una estructura o una unión en el mismo ámbito o en un ámbito interno, se debe indicar el especificador de tipo.  Por ejemplo:  
  
```  
typedef char FlagType;  
const FlagType x;  
```  
  
 Para reutilizar el nombre `FlagType` para un identificador, un miembro de una estructura o un miembro de una unión, se debe proporcionar el tipo:  
  
```  
const int FlagType;  // Type specifier required  
```  
  
 No basta con decir  
  
```  
const FlagType;      // Incomplete specification  
```  
  
 porque se considera que `FlagType` forma parte del tipo, no un identificador que se va a volver a declarar.  Esta declaración se considera no válida como  
  
```  
int;  // Illegal declaration   
```  
  
 Es posible declarar cualquier tipo con typedef, incluidos los tipos de puntero, función y matriz.  Se puede declarar un nombre de typedef para un puntero a un tipo de estructura o de unión antes de definir el tipo de estructura o de unión, siempre y cuando la definición tenga la misma visibilidad que la declaración.  
  
### Ejemplos  
 Un uso de las declaraciones `typedef` consiste en hacer que las declaraciones sean más uniformes y compactas.  Por ejemplo:  
  
```  
typedef char CHAR;          // Character type.  
typedef CHAR * PSTR;        // Pointer to a string (char *).  
PSTR strchr( PSTR source, CHAR target );  
typedef unsigned long ulong;  
ulong ul;     // Equivalent to "unsigned long ul;"  
```  
  
 Para utilizar `typedef` con el fin de especificar tipos fundamentales y derivados en la misma declaración, se pueden separar los declaradores mediante comas.  Por ejemplo:  
  
```  
typedef char CHAR, *PSTR;  
```  
  
 El ejemplo siguiente proporciona el tipo `DRAWF` para una función que no devuelve ningún valor y que toma dos argumentos int:  
  
```  
typedef void DRAWF( int, int );  
```  
  
 Después de la instrucción `typedef` anterior, la declaración  
  
```  
DRAWF box;   
```  
  
 sería equivalente a la declaración  
  
```  
void box( int, int );  
```  
  
 `typedef` se suele combinar con `struct` para declarar y asignar nombre a tipos definidos por el usuario:  
  
```  
// typedef_specifier2.cpp  
#include <stdio.h>  
  
typedef struct mystructtag  
{  
    int   i;  
    double f;  
} mystruct;  
  
int main()  
{  
    mystruct ms;  
    ms.i = 10;  
    ms.f = 0.99;  
    printf_s("%d   %f\n", ms.i, ms.f);  
}  
```  
  
  **10   0.990000**   
### Nueva declaración de definiciones de tipos  
 La declaración `typedef` se puede utilizar para volver a declarar el mismo nombre para hacer referencia al mismo tipo.  Por ejemplo:  
  
```  
// FILE1.H  
typedef char CHAR;  
  
// FILE2.H  
typedef char CHAR;  
  
// PROG.CPP  
#include "file1.h"  
#include "file2.h"   // OK  
```  
  
 El programa PROG.CPP incluye dos archivos de encabezado, que contienen las declaraciones `typedef` para el nombre `CHAR`.  Mientras las declaraciones hagan referencia al mismo tipo, se puede volver a declarar el nombre.  
  
 `typedef` no puede volver a definir un nombre que se declaró previamente como un tipo diferente.  Por tanto, si FILE2.H contiene  
  
```  
// FILE2.H  
typedef int CHAR;     // Error  
```  
  
 el compilador genera un error debido al intento de volver a declarar el nombre `CHAR` para hacer referencia a un tipo diferente.  Esto se aplica también a las construcciones como:  
  
```  
typedef char CHAR;  
typedef CHAR CHAR;      // OK: redeclared as same type  
  
typedef union REGS      // OK: name REGS redeclared  
{                       //  by typedef name with the  
    struct wordregs x;  //  same meaning.  
    struct byteregs h;  
} REGS;  
```  
  
### Definiciones de tipos de C\+\+ frente aC  
 El uso del especificador `typedef` con tipos de clase se admite en gran medida debido a la práctica de ANSI C de declarar las estructuras sin nombre en declaraciones `typedef`.  Por ejemplo, muchos programadores de C usan lo siguiente:  
  
```  
// typedef_with_class_types1.cpp  
// compile with: /c  
typedef struct {   // Declare an unnamed structure and give it the  
                   // typedef name POINT.  
   unsigned x;  
   unsigned y;  
} POINT;  
```  
  
 La ventaja de esta declaración es que hace posibles declaraciones como:  
  
```  
POINT ptOrigin;  
```  
  
 en lugar de:  
  
```  
struct point_t ptOrigin;  
```  
  
 En C\+\+, la diferencia entre los nombres de `typedef` y los tipos reales \(declarados con las palabras clave **clase**, `struct`, **union** y `enum`\) es mayor.  Aunque todavía funciona la práctica de C de declarar una estructura anónima en una instrucción `typedef`, no proporciona ningún beneficio notacional como lo hace en C.  
  
```  
// typedef_with_class_types2.cpp  
// compile with: /c /W1  
typedef struct {  
   int POINT();  
   unsigned x;  
   unsigned y;  
} POINT;  
```  
  
 En el ejemplo anterior se declara una clase denominada `POINT` mediante la sintaxis `typedef` de la clase sin nombre.  `POINT` se trata como un nombre de clase; sin embargo, a los nombres así especificados se aplican las siguientes restricciones:  
  
-   El nombre \(el sinónimo\) no puede aparecer después de un prefijo **class**, `struct` o **union**.  
  
-   El nombre no se puede utilizar como nombre de constructor o destructor dentro de una declaración de clase.  
  
 En resumen, esta sintaxis no proporciona ningún mecanismo para la herencia, la construcción o la destrucción.  
  
## Vea también  
 [using \(Palabra clave\)](../misc/using-keyword.md)