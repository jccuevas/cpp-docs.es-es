---
title: "Error del compilador C2440 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2440"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2440"
ms.assetid: 36e6676c-f04f-4715-8ba1-f096c4bf3b44
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# Error del compilador C2440
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'conversión' : no se puede realizar la conversión de 'tipo1' a 'tipo2'  
  
 El compilador no puede realizar la conversión de '`type1`' a '`type2`'.  
  
## Ejemplo  
 C2440 puede producirse al intentar inicializar un `char*` no const \(o `wchar_t*`\) mediante un literal de cadena en el código de C\+\+, cuando se establece la opción [\/Zc: strictStrings](../../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md) de conformidad del compilador.  En C, el tipo de un literal de cadena es matriz de `char`, pero en C\+\+, es matriz de `const` `char`.  Este ejemplo genera el error C2440:  
  
```cpp  
// C2440s.cpp  
// Build: cl /Zc:strictStrings /W3 C2440s.cpp  
// When built, the compiler emits:  
// error C2440: 'initializing' : cannot convert from 'const char [5]'   
// to 'char *'  
//        Conversion from string literal loses const qualifier (see  
// /Zc:strictStrings)  
  
int main() {  
   char* s1 = "test"; // C2440  
   const char* s2 = "tests"; // OK  
}  
```  
  
## Ejemplo  
 El error C2440 también puede producirse al intentar convertir un puntero a miembro a void\*.  El código siguiente genera el error C2440:  
  
```cpp  
// C2440.cpp  
class B {  
public:  
   void  f(){;}  
  
   typedef void (B::*pf)();  
  
   void f2(pf pf) {  
       (this->*pf)();  
       void* pp = (void*)pf;   // C2440  
   }  
  
   void f3() {  
      f2(f);  
   }  
};  
```  
  
## Ejemplo  
 El error C2440 también puede producirse si se intenta convertir de un tipo que solo se haya declarado hacia delante pero no se haya definido.  Este ejemplo genera el error C2440:  
  
```cpp  
// c2440a.cpp   
struct Base { }; // Defined  
  
struct Derived; // Forward declaration, not defined  
  
Base * func(Derived * d) {  
    return static_cast<Base *>(d); // error C2440: 'static_cast' : cannot convert from 'Derived *' to 'Base *'  
}  
  
```  
  
## Ejemplo  
 Los errores C2440 en las líneas 15 y 16 del ejemplo siguiente se califican con el mensaje `Incompatible calling conventions for UDT return value`. Los tipos definidos por el usuario \(UDT\) son por ejemplo class, struct, o union. Estos tipos de errores de incompatibilidad se producen cuando la convención de llamada de un tipo definido por el usuario y especificado en el tipo de valor devuelto de una declaración adelantada entra en conflicto con la convención de llamada real del tipo definido por el usuario, y cuando hay implicado un puntero a función.  
  
 En el ejemplo, primero tenemos declaraciones adelantadas para struct y para una función que devuelve struct; el compilador supone que struct utiliza la convención de llamada de C\+\+.  A continuación tenemos la definición de struct, la cual, de forma predeterminada, utiliza la convención de llamada de C.  Dado que el compilador no conoce la convención de llamada de struct hasta que termina de leerla por completo, también se supone que la convención de llamada de struct en el tipo de valor devuelto de `get_c2` es C\+\+.  
  
 Struct tiene detrás otra declaración de función que devuelve struct, pero en este momento el compilador sabe que su convención de llamada es C\+\+.  De igual forma, el puntero de función, que devuelve struct, se define a continuación de la definición de struct para que el compilador sepa que struct usa la convención de llamada de C\+\+.  
  
 Para resolver este error C2440 producido a consecuencia de convenciones de llamada incompatibles, declare funciones que devuelvan un tipo definido por el usuario después de la definición del tipo.  
  
```cpp  
// C2440b.cpp  
struct MyStruct;  
  
MyStruct get_c1();  
  
struct MyStruct {  
   int i;  
   static MyStruct get_C2();  
};  
  
MyStruct get_C3();  
  
typedef MyStruct (*FC)();  
  
FC fc1 = &get_c1;   // C2440, line 15  
FC fc2 = &MyStruct::get_C2;   // C2440, line 16  
FC fc3 = &get_C3;  
  
class CMyClass {  
public:  
   explicit CMyClass( int iBar)  
      throw()   {  
   }  
  
   static CMyClass get_c2();  
};  
  
int main() {  
   CMyClass myclass = 2;   // C2440  
   // try one of the following  
   // CMyClass myclass{2};  
   // CMyClass myclass(2);  
  
   int *i;  
   float j;  
   j = (float)i;   // C2440, cannot cast from pointer to int to float  
}  
```  
  
## Ejemplo  
 El error C2440 también se puede producir si se asigna el valor cero a un puntero interior:  
  
```cpp  
// C2440c.cpp  
// compile with: /clr  
int main() {  
   array<int>^ arr = gcnew array<int>(100);  
   interior_ptr<int> ipi = &arr[0];  
   ipi = 0;   // C2440  
   ipi = nullptr;   // OK  
}  
```  
  
## Ejemplo  
 El error C2440 también se puede deber a un uso incorrecto de una conversión definida por el usuario.  Para obtener más información sobre las conversiones definidas por el usuario, vea [Conversiones definidas por el usuario](../../dotnet/user-defined-conversions-cpp-cli.md).  Este ejemplo genera el error C2440:  
  
```cpp  
// C2440d.cpp  
// compile with: /clr  
value struct MyDouble {  
   double d;  
   // convert MyDouble to Int32  
   static explicit operator System::Int32 ( MyDouble val ) {  
      return (int)val.d;  
   }  
};  
  
int main() {  
   MyDouble d;  
   int i;  
   i = d;   // C2440  
   // Uncomment the following line to resolve.  
   // i = static_cast<int>(d);  
}  
```  
  
## Ejemplo  
 El error C2440 también se puede producir si se intenta crear una instancia de una matriz de Visual C\+\+ cuyo tipo es <xref:System.Array>.  Para obtener más información, vea [Matrices](../../windows/arrays-cpp-component-extensions.md).  El código siguiente genera el error C2440:  
  
```cpp  
// C2440e.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   array<int>^ intArray = Array::CreateInstance(__typeof(int), 1);   // C2440  
   // try the following line instead  
   // array<int>^ intArray = safe_cast<array<int> ^>(Array::CreateInstance(__typeof(int), 1));  
}  
```  
  
## Ejemplo  
 El error C2440 también se puede deber a cambios en la característica de atributos.  El ejemplo siguiente genera el error C2440.  
  
```cpp  
// c2440f.cpp  
// compile with: /LD  
[ module(name="PropDemoLib", version=1.0) ];   // C2440  
// try the following line instead  
// [ module(name="PropDemoLib", version="1.0") ];  
```  
  
## Ejemplo  
 El compilador de Visual C\+\+ ya no permite el uso de [const\_cast \(Operador\)](../../cpp/const-cast-operator.md) para realizar una conversión a un tipo inferior al compilar código fuente que utilice programación **\/clr**.  
  
 Para resolver el error C2440, utilice el operador de conversión correcto.  Para obtener más información, vea [Operadores de conversión](../../cpp/casting-operators.md).  
  
 Este ejemplo genera el error C2440:  
  
```cpp  
// c2440g.cpp  
// compile with: /clr  
ref class Base {};  
ref class Derived : public Base {};  
int main() {  
   Derived ^d = gcnew Derived;  
   Base ^b = d;  
   d = const_cast<Derived^>(b);   // C2440  
   d = dynamic_cast<Derived^>(b);   // OK  
}  
```  
  
## Ejemplo  
 El error C2440 también se puede generar utilizando **\/clr:oldSyntax**:  
  
```cpp  
// c2440h.cpp  
// compile with: /clr:oldSyntax  
__gc class Base {};  
__gc class Derived : public Base {};  
int main() {  
   Derived *d = new Derived;  
   Base *b = d;  
   d = const_cast<Derived*>(b);   // C2440  
   d = dynamic_cast<Derived*>(b);   // OK  
}  
```