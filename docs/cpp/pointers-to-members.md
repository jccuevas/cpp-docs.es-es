---
title: Punteros a miembros
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, pointers
- class members [C++], pointers to
- pointers, to members
- members [C++], pointers to
- pointers, declarations
ms.assetid: f42ddb79-9721-4e39-95b1-c56b55591f68
ms.openlocfilehash: adffacc3ddc08679d7db4e17e027d8a7dbe8a92b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320326"
---
# <a name="pointers-to-members"></a>Punteros a miembros

Las declaraciones de punteros a miembros son casos especiales de declaraciones de puntero.  Se declaran mediante la siguiente secuencia:

> *storage-class-specifiers*<sub>opt</sub> *cv-qualifiers*<sub>opt</sub> *type-specifier* *ms-modifier*<sub>opt</sub> *qualified-name* **`::*`** *cv-qualifiers*<sub>opt</sub> *identifier* *pm-initializer*opt<sub>opt</sub>**`;`**

1. El especificador de declaración:

   - Un especificador de clase de almacenamiento opcional.

   - **Especificadores const** y **volatile opcionales.**

   - El especificador de tipo: el nombre de un tipo. Es el tipo de miembro al que se debe apuntar, no la clase.

1. El declarador:

   - Modificador opcional concreto de Microsoft. Para obtener más información, consulte [Modificadores específicos de Microsoft](../cpp/microsoft-specific-modifiers.md).

   - El nombre completo de la clase que contiene los miembros a los que se señala.

   - El __`::`__ operador.

   - El __`*`__ operador.

   - **Especificadores const** y **volatile opcionales.**

   - El identificador que denomina el puntero a miembro.

1. Un inicializador de puntero a miembro opcional:

   - El **`=`** operador.

   - El **`&`** operador.

   - Nombre completo de la clase.

   - El __`::`__ operador.

   - El nombre de un miembro no estático de la clase del tipo adecuado.

Como siempre, se permiten varios declaradores (y cualesquiera inicializadores asociados) en una sola declaración. Un puntero a miembro no puede apuntar a un miembro estático **`void`** de la clase, un miembro de tipo de referencia o .

Un puntero a un miembro de una clase difiere de un puntero normal: tiene información de tipo para el tipo del miembro y para la clase a la que pertenece el miembro. Un puntero normal identifica (tiene la dirección de) un solo objeto en memoria. Un puntero a un miembro de una clase identifica ese miembro en cualquier instancia de la clase. En el ejemplo siguiente se declara una clase, `Window`, y algunos punteros a los datos de miembros.

```cpp
// pointers_to_members1.cpp
class Window
{
public:
   Window();                               // Default constructor.
   Window( int x1, int y1,                 // Constructor specifying
   int x2, int y2 );                       //  window size.
bool SetCaption( const char *szTitle ); // Set window caption.
   const char *GetCaption();               // Get window caption.
   char *szWinCaption;                     // Window caption.
};

// Declare a pointer to the data member szWinCaption.
char * Window::* pwCaption = &Window::szWinCaption;
int main()
{
}
```

En el ejemplo `pwCaption` anterior, es un puntero `Window` a cualquier `char*`miembro de la clase que sea de tipo . El tipo de `pwCaption` es `char * Window::*`. El siguiente fragmento de código declara punteros a las funciones miembro `SetCaption` y `GetCaption`.

```cpp
const char * (Window::*pfnwGC)() = &Window::GetCaption;
bool (Window::*pfnwSC)( const char * ) = &Window::SetCaption;
```

Los punteros `pfnwGC` y `pfnwSC` señalan, respectivamente, a `GetCaption` y a `SetCaption` de la clase `Window`. El código copia la información en la leyenda de la ventana directamente mediante el puntero al miembro `pwCaption`:

```cpp
Window wMainWindow;
Window *pwChildWindow = new Window;
char   *szUntitled    = "Untitled -  ";
int    cUntitledLen   = strlen( szUntitled );

strcpy_s( wMainWindow.*pwCaption, cUntitledLen, szUntitled );
(wMainWindow.*pwCaption)[cUntitledLen - 1] = '1';     //same as
//wMainWindow.SzWinCaption [cUntitledLen - 1] = '1';
strcpy_s( pwChildWindow->*pwCaption, cUntitledLen, szUntitled );
(pwChildWindow->*pwCaption)[cUntitledLen - 1] = '2'; //same as //pwChildWindow->szWinCaption[cUntitledLen - 1] = '2';
```

La diferencia **`.*`** entre **`->*`** los operadores y (los operadores **`.*`** de puntero a miembro) es que **`->*`** el operador selecciona los miembros dados a una referencia de objeto u objeto, mientras que el operador selecciona miembros a través de un puntero. Para obtener más información acerca de estos operadores, vea [Expresiones con operadores de puntero a miembro](../cpp/pointer-to-member-operators-dot-star-and-star.md).

El resultado de los operadores de puntero a miembro es el tipo del miembro. En este caso, es `char *`.

El fragmento de código siguiente invoca las funciones miembro `GetCaption` y `SetCaption` mediante punteros a miembros:

```cpp
// Allocate a buffer.
enum {
    sizeOfBuffer = 100
};
char szCaptionBase[sizeOfBuffer];

// Copy the main window caption into the buffer
//  and append " [View 1]".
strcpy_s( szCaptionBase, sizeOfBuffer, (wMainWindow.*pfnwGC)() );
strcat_s( szCaptionBase, sizeOfBuffer, " [View 1]" );
// Set the child window's caption.
(pwChildWindow->*pfnwSC)( szCaptionBase );
```

## <a name="restrictions-on-pointers-to-members"></a>Restricciones de los punteros a miembros

La dirección de un miembro estático no es un puntero a un miembro. Es un puntero normal a la única instancia del miembro estático. Solo existe una instancia de un miembro estático para todos los objetos de una clase determinada. Esto significa que puede utilizar los**&** operadores de<strong>\*</strong>dirección normal de ( ) y desreferenciación ( ).

## <a name="pointers-to-members-and-virtual-functions"></a>Punteros a funciones virtuales y de miembro

Invocar una función virtual a través de una función de puntero a miembro funciona como si se hubiera llamado a la función directamente. La función correcta se busca en la tabla v y se invoca.

La clave para trabajar con funciones virtuales es, como siempre, invocarlas a través de un puntero a una clase base. (Para obtener más información acerca de las funciones virtuales, consulte [Funciones virtuales](../cpp/virtual-functions.md).)

El código siguiente muestra cómo invocar una función virtual a través de una función de puntero a miembro:

```cpp
// virtual_functions.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

class Base
{
    public:
    virtual void Print();
};
void (Base ::* bfnPrint)() = &Base :: Print;
void Base :: Print()
{
    cout << "Print function for class Base\n";
}

class Derived : public Base
{
    public:
    void Print();  // Print is still a virtual function.
};

void Derived :: Print()
{
    cout << "Print function for class Derived\n";
}

int main()
{
    Base   *bPtr;
    Base    bObject;
    Derived dObject;
    bPtr = &bObject;    // Set pointer to address of bObject.
    (bPtr->*bfnPrint)();
    bPtr = &dObject;    // Set pointer to address of dObject.
    (bPtr->*bfnPrint)();
}

//Output: Print function for class Base
Print function for class Derived
```
