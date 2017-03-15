---
title: "Destructores (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "~ (operador), especificar destructores"
  - "destruir objetos, destructores"
  - "destructores, acerca de destructores"
  - "destructores, C++"
  - "objetos [C++], destruir"
  - "Visual C++, destructores"
ms.assetid: afa859b0-f3bc-4c4d-b250-c68b335b6004
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Destructores (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las funciones de "destructor" son lo contrario de las funciones de constructor.  Se les llama cuando se destruyen \(desasignan\) objetos.  Para designar una función como el destructor de una clase, se debe preceder el nombre de la clase con una tilde \(`~`\).  Por ejemplo, el destructor de la clase `String` se declara como: `~String()`.  
  
 En una compilación \/clr, el destructor tiene un rol especial en la liberación de recursos administrados y no administrados.  Para obtener más información, vea [Destructores y finalizadores de Visual C\+\+](../misc/destructors-and-finalizers-in-visual-cpp.md).  
  
 El destructor se suele utilizar para "limpiar" cuando un objeto ya no es necesario.  Considere la siguiente declaración de una clase `String`:  
  
```  
// spec1_destructors.cpp  
#include <string.h>  
  
class String {  
public:  
   String( char *ch );  // Declare constructor  
   ~String();           //  and destructor.  
private:  
   char    *_text;  
   size_t  sizeOfText;  
};  
  
// Define the constructor.  
String::String( char *ch ) {  
   sizeOfText = strlen( ch ) + 1;  
  
   // Dynamically allocate the correct amount of memory.  
   _text = new char[ sizeOfText ];  
  
   // If the allocation succeeds, copy the initialization string.  
   if( _text )  
      strcpy_s( _text, sizeOfText, ch );  
}  
  
// Define the destructor.  
String::~String() {  
   // Deallocate the memory that was previously reserved  
   //  for this string.  
   if (_text)  
      delete[] _text;  
}  
  
int main() {  
   String str("The piper in the glen...");  
}  
```  
  
 En el ejemplo anterior, el destructor `String::~String` utiliza el operador `delete` para desasignar el espacio asignado dinámicamente para el almacenamiento de texto.  
  
## Declarar destructores  
 Los destructores son funciones con el mismo nombre que la clase pero precedidos por una tilde \(`~`\).  
  
 La primera forma de sintaxis se usa para los destructores declarados o definidos dentro de una declaración de clase; la segunda forma se utiliza para los destructores definidos fuera de una declaración de clase.  
  
 Varias reglas rigen la declaración de destructores.  Destructores:  
  
-   No aceptan argumentos.  
  
-   No puede especificar ningún tipo de valor devuelto \(incluido `void`\).  
  
-   No se puede devolver un valor mediante la instrucción `return`.  
  
-   No se pueden declarar como **const**, `volatile` o **static**.  Sin embargo, se pueden invocar para la destrucción de objetos declarados como **const**, `volatile` o **static**.  
  
-   Pueden declararse como **virtual**.  Mediante los destructores virtuales, puede eliminar objetos sin conocer su tipo; se invoca el destructor correcto para el objeto mediante el mecanismo de función virtual.  Observe que los destructores también se pueden declarar como funciones virtuales puras para las clases abstractas.  
  
## Usar destructores  
 Se llama a los destructores cuando se produce alguno de los eventos siguientes:  
  
-   Un objeto asignado mediante el operador **new** se desasigna explícitamente con el operador **delete**.  Cuando los objetos se desasignan con el operador **delete**, la memoria se libera para el "objeto más derivado" o para el objeto que es un objeto completo y no un subobjeto que representa una clase base.  La desasignación del "objeto más derivado" solo funciona con seguridad con destructores virtuales.  La desasignación puede producir un error en las situaciones de herencia múltiple donde la información de tipo no se corresponde con el tipo subyacente del objeto real.  
  
-   Un objeto local \(automático\) con ámbito de bloque sale de ámbito.  
  
-   La duración de un objeto temporal termina.  
  
-   Un programa termina y hay objetos globales o estáticos.  
  
-   Se llama explícitamente al destructor mediante el nombre completo de la función de destructor.  \(Para obtener más información, vea [Llamadas explícitas al destructor](../misc/explicit-destructor-calls.md)\).  
  
 Los casos descritos en la lista anterior garantizan que todos los objetos se puedan destruir con métodos definidos por el usuario.  
  
 Si una clase base o miembro de datos tiene un destructor accesible, y si una clase derivada no declara un destructor, el compilador genera uno.  Este destructor generado por el compilador llama al destructor de la clase base y a los destructores de los miembros del tipo derivado.  Los destructores predeterminados son públicos.  \(Para obtener más información sobre la accesibilidad, vea [Especificadores de acceso de clases base](../misc/access-specifiers-for-base-classes.md)\).  
  
 Los destructores pueden llamar libremente a funciones miembro de clase y acceder a datos de miembros de clase.  Cuando se llama a una función virtual desde un destructor, la función llamada es la función de la clase que se está destruyendo actualmente.  \(Para obtener más información, vea [Orden de destrucción](../misc/order-of-destruction.md)\).  
  
 Hay dos restricciones en el uso de destructores.  La primera restricción es que no se puede tomar la dirección del destructor.  La segunda es que las clases derivadas no heredan los destructores de su clase base.  En lugar de ello, como se explicó anteriormente, siempre invalidan los destructores de la clase base.  
  
## Orden de destrucción  
 Cuando un objeto sale del ámbito o se elimina, la secuencia de eventos para su completa destrucción es la siguiente:  
  
1.  Se llama al destructor de clase y se ejecuta el cuerpo de la función destructora.  
  
2.  Los destructores de los objetos miembro no estáticos se llaman en el orden inverso al que aparecen en la declaración de clase.  La lista opcional de inicialización de miembros utilizada en la construcción de estos miembros no afecta al orden de \(construcción o\) destrucción.  \(Para obtener más información sobre la inicialización de miembros, vea [Inicialización de bases y miembros](http://msdn.microsoft.com/es-es/2f71377e-2b6b-49da-9a26-18e9b40226a1).\)  
  
3.  Los destructores para las clases base no virtuales se llaman en el orden inverso al de la declaración.  
  
4.  Los destructores para las clases base virtuales se llaman en el orden inverso al de la declaración.  
  
```  
// order_of_destruction.cpp  
#include <stdio.h>  
  
struct A1      { virtual ~A1() { printf("A1 dtor\n"); } };  
struct A2 : A1 { virtual ~A2() { printf("A2 dtor\n"); } };  
struct A3 : A2 { virtual ~A3() { printf("A3 dtor\n"); } };  
  
struct B1      { ~B1() { printf("B1 dtor\n"); } };  
struct B2 : B1 { ~B2() { printf("B2 dtor\n"); } };  
struct B3 : B2 { ~B3() { printf("B3 dtor\n"); } };  
  
int main() {  
   A1 * a = new A3;  
   delete a;  
   printf("\n");  
  
   B1 * b = new B3;  
   delete b;  
   printf("\n");  
  
   B3 * b2 = new B3;  
   delete b2;  
}  
  
Output: A3 dtor  
A2 dtor  
A1 dtor  
  
B1 dtor  
  
B3 dtor  
B2 dtor  
B1 dtor  
  
```  
  
### Clases base virtuales  
 Los destructores de las clases base virtuales se llaman en orden inverso al de su aparición en un gráfico acíclico dirigido \(recorrido con prioridad de profundidad, de izquierda a derecha y en postorden\).  La ilustración siguiente representa un gráfico de herencia.  
  
 ![Gráfico de herencia que muestra clases base virtuales](../cpp/media/vc392j1.png "vc392J1")  
Gráfico de herencia que muestra clases base virtuales  
  
 A continuación se enumeran los encabezados de las clases que se muestran en la ilustración.  
  
```  
class A  
class B  
class C : virtual public A, virtual public B  
class D : virtual public A, virtual public B  
class E : public C, public D, virtual public B  
```  
  
 Para determinar el orden de destrucción de las clases base virtuales de un objeto de tipo `E`, el compilador compila una lista aplicando el algoritmo siguiente:  
  
1.  Recorrer el gráfico izquierdo, desde el punto más profundo del gráfico \(en este caso, `E`\).  
  
2.  Realizar recorridos hacia la izquierda hasta que se hayan visitado todos los nodos.  Anotar el nombre del nodo actual.  
  
3.  Revisitar el nodo anterior \(abajo y a la derecha\) para averiguar si el nodo recordado es una clase base virtual.  
  
4.  Si el nodo recordado es una clase base virtual, examinar la lista para ver si ya se ha especificado.  Si no es una clase base virtual, omitirla.  
  
5.  Si el nodo recordado no está aún en la lista, agregarla al final de la lista.  
  
6.  Recorrer el gráfico hacia arriba y a lo largo de la ruta siguiente a la derecha.  
  
7.  Vaya al paso 2.  
  
8.  Cuando se agote la última ruta ascendente, anotar el nombre del nodo actual.  
  
9. Vaya al paso 3.  
  
10. Continuar este proceso hasta que el nodo inferior sea de nuevo el nodo actual.  
  
 Por consiguiente, para la clase `E`, el orden de destrucción es:  
  
1.  La clase base no virtual `E`.  
  
2.  La clase base no virtual `D`.  
  
3.  La clase base no virtual `C`.  
  
4.  La clase base virtual `B`.  
  
5.  La clase base virtual `A`.  
  
 Este proceso produce una lista ordenada de entradas únicas.  Ningún nombre de clase aparece dos veces.  Una vez construida la lista, se recorre en orden inverso y se llama al destructor para cada una de las clases de la lista, desde la última hasta la primera.  
  
 El orden de construcción o de destrucción es importante sobre todo cuando los constructores o destructores de una clase se basan en que el otro componente se cree primero o persista más tiempo; por ejemplo, si el destructor para `A` \(en la ilustración anterior\) se basa en que `B` continúa estando presente cuando se ejecute el código o viceversa.  
  
 Tales interdependencias entre clases en un gráfico de herencia son inherentemente peligrosas, porque las últimas clases derivadas pueden cambiar cuál es la ruta más a la izquierda y, en consecuencia, pueden cambiar el orden de construcción y destrucción.  
  
### Clases base no virtuales  
 Los destructores para clases base no virtuales se invocan en orden inverso al que se declaran los nombres de clase base.  Considere la siguiente declaración de clase:  
  
```  
class MultInherit : public Base1, public Base2  
...  
```  
  
 En el ejemplo anterior, el destructor para `Base2` se invoca antes que el destructor para `Base1`.  
  
## Llamadas de destructor explícitas  
 Raras veces se necesita llamar explícitamente al destructor.  Sin embargo, puede ser útil realizar la limpieza de los objetos colocados en direcciones absolutas.  Estos objetos se asignan normalmente utilizando un operador **new** definido por el usuario que toma un argumento de ubicación.  El operador **delete** no puede desasignar esta memoria porque no está asignada desde el almacén gratuito \(para obtener más información, vea [Los operadores new y delete](../cpp/new-and-delete-operators.md)\).  Sin embargo, una llamada al destructor puede realizar la limpieza adecuada.  Para llamar explícitamente al destructor para un objeto, `s`, de clase `String`, utilice una de las instrucciones siguientes:  
  
```  
s.String::~String();     // Nonvirtual call  
ps->String::~String();   // Nonvirtual call  
  
s.~String();       // Virtual call  
ps->~String();     // Virtual call  
```  
  
 La notación para las llamadas explícitas a destructores, que se muestra anteriormente, puede utilizarse con independencia de que el tipo defina un destructor.  Esto permite realizar llamadas explícitas sin saber si un destructor está definido para el tipo.  Una llamada explícita a un destructor donde no se ha definido ninguna no tiene ningún efecto.  
  
## Vea también  
 [Funciones miembro especiales](../misc/special-member-functions-cpp.md)