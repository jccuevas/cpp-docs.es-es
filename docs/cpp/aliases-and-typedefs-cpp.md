---
title: Alias y definiciones de tipos (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- typedef_cpp
dev_langs:
- C++
ms.assetid: af1c24d2-4bfd-408a-acfc-482e264232f5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cff0103a9debe63def6dbbcf7e3730a8e09dcbc2
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37944456"
---
# <a name="aliases-and-typedefs-c"></a>Alias y definiciones de tipos (C++)
Puede usar un *la declaración de alias* para declarar un nombre que se usará como sinónimo para un tipo declarado previamente. (Este mecanismo también se conoce informalmente como un *alias de tipo*). También puede usar este mecanismo para crear un *plantilla de alias*, que puede ser especialmente útil para los asignadores personalizados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
using identifier = type;  
```  
  
## <a name="remarks"></a>Comentarios  
 `identifier`  
 Nombre del alias.  
  
 `type`  
 Identificador de tipo para el que se va a crear un alias.  
  
 Un alias no presenta un tipo nuevo y no puede cambiar el significado de un nombre de tipo existente.  
  
 La forma más sencilla de un alias es equivalente a la **typedef** mecanismo de C ++ 03:  
  
```cpp  
// C++11  
using counter = long;  
  
// C++03 equivalent:  
// typedef long counter;  
```  
  
 Ambos permiten la creación de variables de tipo "contador". Algo más útil sería un alias de tipo como este para `std::ios_base::fmtflags`:  
  
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
  
 Los alias también funcionan con punteros de función, pero son mucho más legibles la definición de tipo equivalente:  
  
```cpp  
// C++11  
using func = void(*)(int);  
  
// C++03 equivalent:  
// typedef void (*func)(int);  
  
// func can be assigned to a function pointer value  
void actual_function(int arg) { /* some code */ }  
func fptr = &actual_function;  
  
```  
  
 Una limitación de la **typedef** mecanismo es que no funciona con plantillas. Sin embargo, la sintaxis de alias de tipo de C++11 permite la creación de plantillas de alias:  
  
```cpp  
template<typename T> using ptr = T*;   
  
// the name 'ptr<T>' is now an alias for pointer to T  
ptr<int> ptr_int;  
  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar una plantilla de alias con un asignador personalizado; en este caso, un tipo de vector entero. Puede sustituir cualquier tipo por **int** crear un alias adecuado para ocultar el parámetro complejo, se enumera en el código funcional principal. El uso del asignador personalizado en todo el código puede mejorar la legibilidad y reducir el riesgo de introducir errores debidos a errores ortográficos.  
  
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
  
```Output  
1701 1764 1664  
```  
  
## <a name="typedefs"></a>Typedefs  
 Un **typedef** declaración introduce un nombre que, dentro de su ámbito, se convierte en un sinónimo del tipo especificado por el *declaración de tipo* parte de la declaración.  
  
 Puede utilizar declaraciones typedef para construir nombres más cortos o más significativos para tipos ya definidos por el lenguaje o para tipos que ha declarado. Los nombres de typedef permiten encapsular detalles de la implementación que pueden cambiar.  
  
 Por el contrario el **clase**, **struct**, **unión**, y **enum** declaraciones, **typedef** las declaraciones no introducen nuevos tipos, introducen nuevos nombres para tipos existentes.  
  
 Los nombres declarados con **typedef** ocupan el mismo espacio de nombres que otros identificadores (excepto las etiquetas de instrucciones). Por consiguiente, no pueden utilizar el mismo identificador que un nombre declarado previamente, excepto en una declaración de tipo de clase. Considere el ejemplo siguiente:  
  
```cpp 
// typedef_names1.cpp  
// C2377 expected  
typedef unsigned long UL;   // Declare a typedef name, UL.  
int UL;                     // C2377: redefined.  
```  
  
 Las reglas de ocultación de nombres que pertenecen a otros identificadores también controlan la visibilidad de los nombres declarados con **typedef**. Por consiguiente, el ejemplo siguiente es válido en C++:  
  
```cpp 
// typedef_names2.cpp  
typedef unsigned long UL;   // Declare a typedef name, UL  
int main()  
{  
   unsigned int UL;   // Redeclaration hides typedef name  
}  
  
// typedef UL back in scope  
```  
 
  
```cpp 
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
  
 Al declarar un identificador de ámbito local con el mismo nombre que un typedef, o al declarar un miembro de una estructura o una unión en el mismo ámbito o en un ámbito interno, se debe indicar el especificador de tipo. Por ejemplo:  
  
```cpp 
typedef char FlagType;  
const FlagType x;  
```  
  
 Para reutilizar el nombre `FlagType` para un identificador, un miembro de una estructura o un miembro de una unión, se debe proporcionar el tipo:  
  
```cpp 
const int FlagType;  // Type specifier required  
```  
  
 No basta con decir  
  
```cpp 
const FlagType;      // Incomplete specification  
```  
  
 porque se considera que `FlagType` forma parte del tipo, no un identificador que se va a volver a declarar. Esta declaración se considera no válida como  
  
```cpp 
int;  // Illegal declaration   
```  
  
 Es posible declarar cualquier tipo con typedef, incluidos los tipos de puntero, función y matriz. Se puede declarar un nombre de typedef para un puntero a un tipo de estructura o de unión antes de definir el tipo de estructura o de unión, siempre y cuando la definición tenga la misma visibilidad que la declaración.  
  
### <a name="examples"></a>Ejemplos  
 Un uso de **typedef** declaraciones es hacer que las declaraciones más uniformes y compactas. Por ejemplo:  
  
```cpp  
typedef char CHAR;          // Character type.  
typedef CHAR * PSTR;        // Pointer to a string (char *).  
PSTR strchr( PSTR source, CHAR target );  
typedef unsigned long ulong;  
ulong ul;     // Equivalent to "unsigned long ul;"  
```  
  
 Para usar **typedef** para especificar tipos fundamentales y derivados en la misma declaración, puede separar los declaradores mediante comas. Por ejemplo:  
  
```cpp 
typedef char CHAR, *PSTR;  
```  
  
 El ejemplo siguiente proporciona el tipo `DRAWF` para una función que no devuelve ningún valor y que toma dos argumentos int:  
  
```cpp 
typedef void DRAWF( int, int );  
```  
  
 Después de la anterior **typedef** instrucción, la declaración  
  
```cpp 
DRAWF box;   
```  
  
 sería equivalente a la declaración  
  
```cpp 
void box( int, int );  
```  
  
 **TypeDef** a menudo se combina con **struct** declarar y dar nombre a tipos definidos por el usuario:  
  
```cpp  
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
  
```Output  
10   0.990000  
``` 
  
### <a name="re-declaration-of-typedefs"></a>Nueva declaración de definiciones de tipos  
 El **typedef** declaración se puede usar para volver a declarar el mismo nombre para hacer referencia al mismo tipo. Por ejemplo:  
  
```cpp  
// FILE1.H  
typedef char CHAR;  
  
// FILE2.H  
typedef char CHAR;  
  
// PROG.CPP  
#include "file1.h"  
#include "file2.h"   // OK  
``` 
  
 El programa *PROG. CPP* incluye dos archivos de encabezado, ambos de los cuales contienen **typedef** declaraciones para el nombre `CHAR`. Mientras las declaraciones hagan referencia al mismo tipo, se puede volver a declarar el nombre.  
  
 Un **typedef** no se puede redefinir un nombre que se declaró previamente como un tipo diferente. Por lo tanto, si *FILE2. H* contiene  
  
```cpp  
// FILE2.H  
typedef int CHAR;     // Error  
``` 
  
 el compilador genera un error debido al intento de volver a declarar el nombre `CHAR` para hacer referencia a un tipo diferente. Esto se aplica también a las construcciones como:  
  
```cpp  
typedef char CHAR;  
typedef CHAR CHAR;      // OK: redeclared as same type  
  
typedef union REGS      // OK: name REGS redeclared  
{                       //  by typedef name with the  
    struct wordregs x;  //  same meaning.  
    struct byteregs h;  
} REGS;  
``` 
  
### <a name="typedefs-in-c-vs-c"></a>Definiciones de tipos de C++ frente a C  
 El uso de la **typedef** especificador de tipos de clase se admite en gran medida debido a la práctica de ANSI C de declarar estructuras sin nombre en **typedef** declaraciones. Por ejemplo, muchos programadores de C usan lo siguiente:  
  
```cpp  
// typedef_with_class_types1.cpp  
// compile with: /c  
typedef struct {   // Declare an unnamed structure and give it the  
                   // typedef name POINT.  
   unsigned x;  
   unsigned y;  
} POINT;  
``` 
  
 La ventaja de esta declaración es que hace posibles declaraciones como:  
  
```cpp  
POINT ptOrigin;  
``` 
  
 en lugar de:  
  
```cpp 
struct point_t ptOrigin;  
```  
  
 En C++, la diferencia entre **typedef** nombres y los tipos reales (declarados con el **clase**, **struct**, **unión**y **enum** palabras clave) es mayor. Aunque la práctica de C de declarar una estructura anónima en un **typedef** instrucción sigue funcionando, no proporciona ningún beneficio notacional como lo hace en C.  
  
```cpp  
// typedef_with_class_types2.cpp  
// compile with: /c /W1  
typedef struct {  
   int POINT();  
   unsigned x;  
   unsigned y;  
} POINT;  
```  
  
 El ejemplo anterior declara una clase denominada `POINT` mediante la clase sin nombre **typedef** sintaxis. `POINT` se trata como un nombre de clase; sin embargo, a los nombres así especificados se aplican las siguientes restricciones:  
  
-   El nombre (el sinónimo) no puede aparecer después de un **clase**, **struct**, o **unión** prefijo.  
  
-   El nombre no se puede utilizar como nombre de constructor o destructor dentro de una declaración de clase.  
  
 En resumen, esta sintaxis no proporciona ningún mecanismo para la herencia, la construcción o la destrucción.  
