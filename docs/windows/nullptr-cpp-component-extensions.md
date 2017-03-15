---
title: "nullptr (Extensiones de componentes de C++) | Microsoft Docs"
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
  - "__nullptr (palabra clave) (C++)"
  - "nullptr (palabra clave) [C++]"
ms.assetid: 594cfbf7-06cb-4366-9ede-c0b703e1d095
caps.latest.revision: 24
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# nullptr (Extensiones de componentes de C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La palabra clave de `nullptr` representa *un valor de puntero null*.  Utilice un valor de puntero null para indicar que un controlador de objeto, un puntero interior, o un tipo de puntero nativo no señala a un objeto.  
  
 Utilice `nullptr` con código administrado o nativo.  El compilador emite instrucciones correspondientes pero diferentes valores administrados y nativos de puntero NULL.  Para obtener información sobre cómo utilizar la versión de C\+\+ del estándar ISO de esta palabra clave, vea [nullptr](../cpp/nullptr.md).  
  
 La palabra clave de `__nullptr` es una palabra clave Microsoft\- específica que tiene el mismo significado que `nullptr`, pero solo se aplica al código nativo.  Si utiliza `nullptr` con código de C\/C\+\+ nativo y se compila con la opción del compilador [\/clr](../build/reference/clr-common-language-runtime-compilation.md) , el compilador no puede determinar si `nullptr` indica un nativo o un valor administrado del puntero NULL.  Para clarificar la intención al compilador, utilice `nullptr` para especificar un valor administrado o `__nullptr` para especificar un valor nativo.  
  
 La palabra clave de `nullptr` es equivalente a `Nothing` en Visual Basic y a `null` en C\#.  
  
## Uso  
 La palabra clave de `nullptr` se puede utilizar en cualquier lugar un identificador, puntero nativo, o el argumento de la función se puede utilizar.  
  
 La palabra clave de `nullptr` no es un tipo y no se admite para su uso con:  
  
-   [sizeof](../cpp/sizeof-operator.md)  
  
-   [typeid](../cpp/typeid-operator.md)  
  
-   `throw nullptr` \(aunque funcionará `throw (Object^)nullptr;` \)  
  
 La palabra clave de `nullptr` se puede utilizar en la inicialización de tipos de puntero siguientes:  
  
-   Puntero nativo  
  
-   Identificador del runtime de Windows  
  
-   Identificador administrado  
  
-   Puntero interior administrado  
  
 La palabra clave de `nullptr` se puede utilizar para probar si una referencia de puntero o ID es null antes de utilizar la referencia.  
  
 Las llamadas de función entre los lenguajes que utilizan valores de puntero NULL para la comprobación de errores se deben interpretar correctamente.  
  
 No puede inicializar un identificador en cero; sólo `nullptr` puede utilizar.  La asignación de la constante 0 a un controlador de objeto genera `Int32` conversión boxing y una conversión a `Object^`.  
  
## Ejemplo  
 El ejemplo de código siguiente se muestra que la palabra clave de `nullptr` se puede utilizar en cualquier parte que un identificador, puntero nativo, o argumento de la función se puede usar.  Y el ejemplo muestra que la palabra clave de `nullptr` se puede utilizar para comprobar una referencia antes de que se utilice.  
  
```  
// mcpp_nullptr.cpp  
// compile with: /clr  
value class V {};  
ref class G {};  
void f(System::Object ^) {}  
  
int main() {  
// Native pointer.  
   int *pN = nullptr;  
// Managed handle.  
   G ^pG = nullptr;  
   V ^pV1 = nullptr;  
// Managed interior pointer.  
   interior_ptr<V> pV2 = nullptr;  
// Reference checking before using a pointer.  
   if (pN == nullptr) {}  
   if (pG == nullptr) {}  
   if (pV1 == nullptr) {}  
   if (pV2 == nullptr) {}  
// nullptr can be used as a function argument.  
   f(nullptr);   // calls f(System::Object ^)  
}  
```  
  
## Ejemplo  
 **Ejemplo**  
  
 El ejemplo de código siguiente se muestra que `nullptr` y cero se puede utilizar también en punteros nativos.  
  
```  
// mcpp_nullptr_1.cpp  
// compile with: /clr  
class MyClass {  
public:  
   int i;  
};  
  
int main() {  
   MyClass * pMyClass = nullptr;  
   if ( pMyClass == nullptr)  
      System::Console::WriteLine("pMyClass == nullptr");  
  
   if ( pMyClass == 0)  
      System::Console::WriteLine("pMyClass == 0");  
  
   pMyClass = 0;  
   if ( pMyClass == nullptr)  
      System::Console::WriteLine("pMyClass == nullptr");  
  
   if ( pMyClass == 0)  
      System::Console::WriteLine("pMyClass == 0");  
}  
```  
  
 **Resultados**  
  
  **nullptr \=\= de los pMyClass**  
 **\=\= 0 de los pMyClass**  
 **nullptr \=\= de los pMyClass**  
 **\=\= 0 de los pMyClass**   
## Ejemplo  
 **Ejemplo**  
  
 El ejemplo de código siguiente se muestra que `nullptr` se interpreta como un identificador a cualquier tipo o un puntero nativo ningún está escrito.  En caso de función que sobrecarga con identificadores a tipos diferentes, un error de ambigüedad se generará.  `nullptr` tendría que en se echado a un tipo.  
  
```  
// mcpp_nullptr_2.cpp  
// compile with: /clr /LD  
void f(int *){}  
void f(int ^){}  
  
void f_null() {  
   f(nullptr);   // C2668  
   // try one of the following lines instead  
   f((int *) nullptr);  
   f((int ^) nullptr);  
}  
```  
  
## Ejemplo  
 **Ejemplo**  
  
 El ejemplo de código siguiente se muestra que el inicio de `nullptr` está permitido y devuelve un puntero o un identificador a la conversión que contiene el valor de `nullptr` .  
  
```  
// mcpp_nullptr_3.cpp  
// compile with: /clr /LD  
using namespace System;  
template <typename T>   
void f(T) {}   // C2036 cannot deduce template type because nullptr can be any type  
  
int main() {  
   f((Object ^) nullptr);   // T = Object^, call f(Object ^)  
  
   // Delete the following line to resolve.  
   f(nullptr);  
  
   f(0);   // T = int, call f(int)  
}  
```  
  
## Ejemplo  
 **Ejemplo**  
  
 El ejemplo de código siguiente se muestra que `nullptr` se puede utilizar como un parámetro de la función.  
  
```  
// mcpp_nullptr_4.cpp  
// compile with: /clr  
using namespace System;  
void f(Object ^ x) {  
   Console::WriteLine("test");  
}  
  
int main() {  
   f(nullptr);  
}  
```  
  
 **Resultados**  
  
  **prueba**   
## Ejemplo  
 **Ejemplo**  
  
 El ejemplo de código siguiente muestra que cuando se declaran y no explícitamente se inicializan los identificadores, son default inicializados a `nullptr`.  
  
```  
// mcpp_nullptr_5.cpp  
// compile with: /clr  
using namespace System;  
ref class MyClass {  
public:  
   void Test() {  
      MyClass ^pMyClass;   // gc type  
      if (pMyClass == nullptr)  
         Console::WriteLine("NULL");  
   }  
};  
  
int main() {  
   MyClass ^ x = gcnew MyClass();  
   x -> Test();  
}  
```  
  
 **Resultados**  
  
  **NULL**   
## Ejemplo  
 **Ejemplo**  
  
 El ejemplo de código siguiente se muestra que `nullptr` se puede asignar a un puntero nativo cuando se compila con **\/clr**.  
  
```  
// mcpp_nullptr_6.cpp  
// compile with: /clr  
int main() {  
   int * i = 0;  
   int * j = nullptr;  
}  
```  
  
## Requisitos  
 Opción del compilador: \(No necesario; admite todas las opciones de generación de código, incluidos **\/ZW** y **\/clr**\)  
  
## Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)   
 [nullptr](../cpp/nullptr.md)