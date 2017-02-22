---
title: "Error del compilador C2660 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2660"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2660"
ms.assetid: 2e01a1db-4f00-4df6-a04d-cb6f70a6922b
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# Error del compilador C2660
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : la función no acepta número parámetros  
  
 Se llama a la función con un número incorrecto de parámetros.  
  
 Puede producirse el error C2660 si se llama accidentalmente a una función de la API de Windows en lugar de llamar a una función miembro MFC del mismo nombre.  Para solucionar este problema:  
  
-   Ajuste la llamada de función para que siga el formato de la llamada a función miembro.  
  
-   Utilice el operador de resolución de ámbito \(`::`\) para indicar al compilador que realice una búsqueda del nombre de función en el espacio de nombres global.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C2660.  
  
```  
// C2660.cpp  
void func( int, int ) {}  
  
int main() {  
   func( 1 );   // C2660 func( int ) not declared  
   func( 1, 0 );   // OK  
}  
```  
  
## Ejemplo  
 Este error también puede producirse si se intenta llamar directamente al método Dispose de un tipo administrado.  Para obtener más información, vea [Destructores y finalizadores](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).  El ejemplo siguiente genera el error C2660.  
  
```  
// C2660_a.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Threading;  
  
void CheckStatus( Object^ stateInfo ) {}  
  
int main() {  
   ManualResetEvent^ event = gcnew ManualResetEvent( false );     
   TimerCallback^ timerDelegate = gcnew TimerCallback( &CheckStatus );  
   Timer^ stateTimer = gcnew Timer( timerDelegate, event, 1000, 250 );  
  
   stateTimer->Dispose();   // C2660  
   stateTimer->~Timer();   // OK  
}  
```  
  
## Ejemplo  
 Se producirá el error C2660 si una clase derivada oculta una función.  
  
```  
// C2660b.cpp  
// C2660 expected  
#include <stdio.h>  
  
class f {  
public:  
   void bar() {  
      printf_s("in f::bar\n");  
    }  
};  
  
class f2 : public f {  
public:  
   void bar(int i){printf("in f2::bar\n");}  
   // Uncomment the following line to resolve.  
   // using f::bar;   // - using declaration added  
   // or  
   // void bar(){__super::bar();}  
};  
  
int main() {  
   f2 fObject;  
   fObject.bar();  
}  
```  
  
## Ejemplo  
 Puede producirse el error C2660 si se invoca una propiedad indizada de forma incorrecta.  
  
```  
// C2660c.cpp  
// compile with: /clr  
ref class X {  
   double d;  
public:  
   X() : d(1.9) {}  
   property double MyProp[] {  
      double get(int i) {  
         return d;  
      }  
   }   // end MyProp definition  
};  
  
int main() {  
   X ^ MyX = gcnew X();  
   System::Console::WriteLine(MyX->MyProp(1));   // C2660  
   System::Console::WriteLine(MyX->MyProp[1]);   // OK  
}  
```  
  
## Ejemplo  
 Puede producirse el error C2660 si se invoca una propiedad indizada de forma incorrecta.  
  
```  
// C2660d.cpp  
// compile with: /clr  
ref class A{  
public:  
   property int default[int,int] {  
      int get(int a, int b) {  
         return a + b;  
      }  
   }  
};  
  
int main() {  
   A^ a = gcnew A;  
   int x = a[3][5];   // C2660  
   int x2 = a[3,5];   // OK  
}  
```  
  
## Ejemplo  
 Puede producirse el error C2660 si se define un nuevo operador en una clase de plantilla, pero el nuevo operador crea en dicha clase un objeto cuyo tipo es distinto al del tipo envolvente.  
  
```  
// C2660e.cpp  
// compile with: /c  
#include <malloc.h>  
  
template <class T> class CA {  
private:  
    static T** line;  
   void* operator new (size_t, int i) {   
      return 0;  
   }  
   void operator delete(void* pMem, int i) {  
      free(pMem);  
   }  
  
public:  
   CA () { new (1) T(); }   // C2660  
   // try the following line instead  
   // CA () { new (1) CA<int>(); }  
};  
  
typedef CA <int> int_CA;  
  
void AAA() {  
   int_CA  list;  
}  
```