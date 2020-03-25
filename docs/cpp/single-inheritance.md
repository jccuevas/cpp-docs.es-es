---
title: Herencia única
ms.date: 11/19/2018
helpviewer_keywords:
- single inheritance
- base classes [C++], indirect
- scope, scope resolution operator
- operators [C++], scope resolution
- scope resolution operator
- derived classes [C++], single base class
- inheritance, single
ms.assetid: 1cb946ed-8b1b-4cf1-bde0-d9cecbfdc622
ms.openlocfilehash: 5f8f08bcea1a44199d15da82b3ddbd37b676b347
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178800"
---
# <a name="single-inheritance"></a>Herencia única

En la "herencia única", una forma de herencia común, las clases solo tienen una clase base. Considere la relación que se muestra en la siguiente ilustración.

![Gráfico de&#45;herencia única básica](../cpp/media/vc38xj1.gif "Gráfico de&#45;herencia única básica") <br/>
Gráfico sencillo de herencia única

Observe la progresión de general a específico en la ilustración. Otro atributo común que se encuentra en el diseño de la mayoría de jerarquías de clases es que la clase derivada tiene una "especie" de relación con la clase base. En la ilustración, `Book` es una clase de `PrintedDocument` y `PaperbackBook` es una clase de `book`.

Otro elemento de interés en la ilustración: `Book` es una clase derivada (de `PrintedDocument`) y una clase base (`PaperbackBook` se deriva de `Book`). En el ejemplo siguiente se muestra una declaración estructural de esta jerarquía de clases:

```cpp
// deriv_SingleInheritance.cpp
// compile with: /LD
class PrintedDocument {};

// Book is derived from PrintedDocument.
class Book : public PrintedDocument {};

// PaperbackBook is derived from Book.
class PaperbackBook : public Book {};
```

`PrintedDocument` se considera una clase "base directa" de `Book`; es una clase "base indirecta" de `PaperbackBook`. La diferencia es que una clase base directa aparece en la lista base de una declaración de clase y una clase base indirecta no.

La clase base de la que se deriva cada clase se declara antes de la declaración de la clase derivada. No es suficiente proporcionar una declaración de referencia adelantada para una clase base; debe ser una declaración completa.

En el ejemplo anterior, se usa el especificador de acceso **Public** . El significado de la herencia pública, protegida y privada se describe en [Access Control de miembro.](../cpp/member-access-control-cpp.md)

Una clase puede actuar como clase base para muchas clases específicas, como se muestra en la ilustración siguiente.

![Gráfico acíclicos dirigido](../cpp/media/vc38xj2.gif "Grafo acíclico dirigido") <br/>
Ejemplo de gráfico acíclico dirigido

En el diagrama anterior, denominado "gráfico acíclico dirigido" (o DAG), algunas de las clases son clases base para más de una clase derivada. Sin embargo, no sucede lo mismo al contrario: solo hay una clase base directa para una clase derivada dada. El gráfico de la ilustración muestra una estructura de "herencia única".

> [!NOTE]
> Los gráficos acíclicos dirigidos no son exclusivos de la herencia única. También se usan para ilustrar gráficos de herencia múltiple.

En la herencia, la clase derivada contiene los miembros de la clase base más cualquier miembro nuevo que se agregue. Como resultado, una clase derivada puede hacer referencia a miembros de la clase base (a menos que esos miembros se redefinan en la clase derivada). Se puede usar el operador de resolución de ámbito (`::`) para hacer referencia a los miembros de clases base directas o indirectas cuando esos miembros se han vuelto a definir en la clase derivada. En este ejemplo:

```cpp
// deriv_SingleInheritance2.cpp
// compile with: /EHsc /c
#include <iostream>
using namespace std;
class Document {
public:
   char *Name;   // Document name.
   void PrintNameOf();   // Print name.
};

// Implementation of PrintNameOf function from class Document.
void Document::PrintNameOf() {
   cout << Name << endl;
}

class Book : public Document {
public:
   Book( char *name, long pagecount );
private:
   long  PageCount;
};

// Constructor from class Book.
Book::Book( char *name, long pagecount ) {
   Name = new char[ strlen( name ) + 1 ];
   strcpy_s( Name, strlen(Name), name );
   PageCount = pagecount;
};
```

Observe que el constructor para `Book`, (`Book::Book`), tiene acceso al miembro de datos, `Name`. En un programa, se puede crear un objeto de tipo `Book`, que se usará del siguiente modo:

```cpp
//  Create a new object of type Book. This invokes the
//   constructor Book::Book.
Book LibraryBook( "Programming Windows, 2nd Ed", 944 );

...

//  Use PrintNameOf function inherited from class Document.
LibraryBook.PrintNameOf();
```

Como demuestra el ejemplo anterior, los datos y funciones heredados y miembros de clase se usan de forma idéntica. Si la implementación de la clase `Book` solicita la reimplementation de la función `PrintNameOf`, la función que pertenece a la clase `Document` solo se puede llamar mediante el operador de resolución de ámbito (`::`):

```cpp
// deriv_SingleInheritance3.cpp
// compile with: /EHsc /LD
#include <iostream>
using namespace std;

class Document {
public:
   char *Name;          // Document name.
   void  PrintNameOf() {}  // Print name.
};

class Book : public Document {
   Book( char *name, long pagecount );
   void PrintNameOf();
   long  PageCount;
};

void Book::PrintNameOf() {
   cout << "Name of book: ";
   Document::PrintNameOf();
}
```

Los punteros y las referencias a clases derivadas se pueden convertir implícitamente a punteros y referencias a sus clases base si hay una clase base accesible e inequívoca. En el código siguiente se muestra este concepto mediante el uso de punteros (el mismo principio se aplica a las referencias):

```cpp
// deriv_SingleInheritance4.cpp
// compile with: /W3
struct Document {
   char *Name;
   void PrintNameOf() {}
};

class PaperbackBook : public Document {};

int main() {
   Document * DocLib[10];   // Library of ten documents.
   for (int i = 0 ; i < 5 ; i++)
      DocLib[i] = new Document;
   for (int i = 5 ; i < 10 ; i++)
      DocLib[i] = new PaperbackBook;
}
```

En el ejemplo anterior, se crean tipos diferentes. Sin embargo, dado que todos estos tipos se derivan de la clase `Document`, hay una conversión implícita a `Document *`. Como resultado, `DocLib` es una "lista heterogénea" (una lista en la que no todos los objetos son del mismo tipo) que contiene diferentes tipos de objetos.

Dado que la clase `Document` tiene una función `PrintNameOf`, puede imprimir el nombre de cada libro de la biblioteca, aunque puede omitir algo de información específica del tipo de documento (recuento de páginas de `Book`, número de bytes para `HelpFile`, etc.).

> [!NOTE]
>  Forzar la clase base para implementar una función como `PrintNameOf` no suele ser el mejor diseño. [Funciones virtuales](../cpp/virtual-functions.md) ofrece otras alternativas de diseño.
