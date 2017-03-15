---
title: "Punteros a miembros | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "miembros de clases, punteros a"
  - "declaraciones, punteros"
  - "miembros, punteros a"
  - "punteros, declaraciones"
  - "punteros, a miembros"
ms.assetid: f42ddb79-9721-4e39-95b1-c56b55591f68
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Punteros a miembros
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las declaraciones de punteros a miembros son casos especiales de declaraciones de puntero.  Se declaran mediante la siguiente secuencia:  
  
```  
[storage-class-specifiers] [cv-qualifiers] type-specifiers [ms-modifier]  
qualified-name ::* [cv-qualifiers] identifier  
[= & qualified-name :: member-name];  
```  
  
1.  El especificador de declaración:  
  
    -   Un especificador de clase de almacenamiento opcional.  
  
    -   Especificadores **const** y\/o `volatile` opcionales.  
  
    -   El especificador de tipo: el nombre de un tipo.  Este es el tipo del miembro al que se señala, no la clase.  
  
2.  El declarador:  
  
    -   Un modificador opcional específico de Microsoft.  Para obtener más información, vea [Modificadores específicos de Microsoft](../cpp/microsoft-specific-modifiers.md).  
  
    -   El nombre completo de la clase que contiene los miembros a los que se señala.  Vea [Nombres y nombres completos](../misc/names-and-qualified-names.md).  
  
    -   El operador ::.  
  
    -   El operador **\***.  
  
    -   Especificadores **const** y\/o `volatile` opcionales.  
  
    -   El identificador que denomina el puntero a miembro.  
  
    -   Un inicializador opcional:  
  
 El operador **\=**.  
  
 El operador **&**.  
  
 Nombre completo de la clase.  
  
 El operador `::`.  
  
 El nombre de un miembro no estático de la clase del tipo adecuado.  
  
 Como siempre, se permiten varios declaradores \(y cualesquiera inicializadores asociados\) en una sola declaración.  
  
 Un puntero a un miembro de una clase se diferencia de un puntero normal porque tiene información del tipo de miembro y de la clase a la que pertenece el miembro.  Un puntero normal identifica \(tiene la dirección de\) un solo objeto en memoria.  Un puntero a un miembro de una clase identifica ese miembro en cualquier instancia de la clase.  En el ejemplo siguiente se declara una clase, `Window`, y algunos punteros a los datos de miembros.  
  
```  
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
  
 En el ejemplo anterior, `pwCaption` es un puntero a cualquier miembro de la clase `Window` que tenga el tipo **char\***.  El tipo de `pwCaption` es `char * Window::*`.  El siguiente fragmento de código declara punteros a las funciones miembro `SetCaption` y `GetCaption`.  
  
```  
const char * (Window::*pfnwGC)() = &Window::GetCaption;  
bool (Window::*pfnwSC)( const char * ) = &Window::SetCaption;  
```  
  
 Los punteros `pfnwGC` y `pfnwSC` señalan, respectivamente, a `GetCaption` y a `SetCaption` de la clase `Window`.  El código copia la información en la leyenda de la ventana directamente mediante el puntero al miembro `pwCaption`:  
  
```  
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
  
 La diferencia entre los operadores **.\*** y **–\>\*** \(los operadores de puntero a miembro\) consiste en que el operador **.\*** selecciona los miembros con un objeto o una referencia de objeto especificados, mientras que el operador **–\>\*** selecciona los miembros a través de un puntero.  \(Para obtener más información sobre estos operadores, vea [Expresiones con operadores de puntero a miembro](../cpp/pointer-to-member-operators-dot-star-and-star.md)\).  
  
 El resultado de los operadores de puntero a miembro es el tipo de miembro \(en este caso, **char \***\).  
  
 El fragmento de código siguiente invoca las funciones miembro `GetCaption` y `SetCaption` mediante punteros a miembros:  
  
```  
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
  
## Restricciones de los punteros a miembros  
 La dirección de un miembro estático no es un puntero a un miembro.  Es un puntero regular a la única instancia del miembro estático.  Puesto que solo existe una instancia de un miembro estático para todos los objetos de una clase determinada, se pueden usar los operadores normales address\-of **\(&\)** y de referencia **\(\*\)**.  
  
## Punteros a funciones virtuales y de miembro  
 La llamada a una función virtual a través de una función de puntero a miembro funciona como si se hubiera llamado directamente a la función; la función correcta se busca en la tabla v y se invoca.  
  
 La clave para trabajar con funciones virtuales es, como siempre, invocarlas a través de un puntero a una clase base.  \(Para obtener más información sobre funciones virtuales, vea [Funciones virtuales](../cpp/virtual-functions.md)\).  
  
 El código siguiente muestra cómo invocar una función virtual a través de una función de puntero a miembro:  
  
```  
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
  
## Vea también  
 [Declaradores abstractos de C\+\+](http://msdn.microsoft.com/es-es/e7e18c18-0cad-4450-942b-d27e1d4dd088)