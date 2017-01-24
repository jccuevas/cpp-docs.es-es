---
title: "Doble thunk (C++) | Microsoft Docs"
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
helpviewer_keywords: 
  - "/clr (opción del compilador) [C++], doble thunk"
  - "thunks dobles"
  - "interoperabilidad [C++], doble thunk"
  - "interoperabilidad [C++], doble thunk"
  - "ensamblados mixtos [C++], doble thunk"
ms.assetid: a85090b2-dc3c-498a-b40c-340db229dd6f
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Doble thunk (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La aplicación de código thunk doble consiste en la pérdida de rendimiento que se puede sufrir cuando una llamada de función en un contexto administrado llama a una función administrada de Visual C\+\+ y donde la ejecución de un programa llama al punto de entrada nativo de la función para llamar a la función administrada.  Este tema explica dónde se produce doble código thunk y cómo se puede evitar para mejorar el rendimiento.  
  
## Comentarios  
 De forma predeterminada, al compilar con **\/clr** \(no con **\/clr:pure**\), la definición de una función administrada hace que el compilador genere un punto de entrada administrado y otro nativo.  Esto permite llamar a la función administrada desde sitios nativos y administrados.  Sin embargo, si existe un punto de entrada nativo, puede ser el punto de entrada para todas las llamadas a la función.  Si una función de llamada es administrada, el punto de entrada nativo llamará al punto de entrada administrado.  En efecto, se necesitan dos llamadas para invocar la función \(de ahí el doble código thunk\).  Por ejemplo, siempre se llama a las funciones virtuales a través de un punto de entrada nativo.  
  
 Una solución consiste en indicar al compilador que no genere un punto de entrada nativo para una función administrada, que sólo se llame a la función desde un contexto administrado, usando la convención de llamada [\_\_clrcall](../cpp/clrcall.md).  
  
 De forma similar, si exporta \([dllexport, dllimport](../cpp/dllexport-dllimport.md)\) una función administrada, se generará un punto de entrada nativo y cualquier función que importe y llame a dicha función llamará a través del punto de entrada nativo.  Para evitar el doble código thunk en esta situación, no utilice la semántica de importación\/exportación nativa; simplemente haga referencia a los metadatos a través de `#using` \(vea [\#using \(Directiva\)](../preprocessor/hash-using-directive-cpp.md)\).  
  
 El compilador se actualizó para reducir el código thunk doble innecesario.  Por ejemplo, cualquier función con un tipo administrado en la firma \(incluido el tipo de devolución\) se marcará implícitamente como `__clrcall`.  Para obtener más información sobre la eliminación de doble código thunk, vea [http:\/\/msdn.microsoft.com\/msdnmag\/issues\/05\/01\/COptimizations\/default.aspx](http://msdn.microsoft.com/msdnmag/issues/05/01/COptimizations/default.aspx).  
  
## Ejemplo  
  
### Descripción  
 En el ejemplo siguiente se muestra el doble código thunk.  Si se compila de forma nativa \(sin **\/clr**\), la llamada a la función virtual en `main` genera una llamada al constructor de copias de `T` y una llamada al destructor.  Se obtiene un comportamiento similar si la función virtual se declara con **\/clr** y `__clrcall`.  Sin embargo, si sólo se compila con **\/clr**, la llamada a la función genera una llamada al constructor de copias, pero se realiza otra llamada al constructor de copias debido al código thunk de nativo a administrado.  
  
### Código  
  
```  
// double_thunking.cpp  
// compile with: /clr  
#include <stdio.h>  
struct T {  
   T() {  
      puts(__FUNCSIG__);  
   }  
  
   T(const T&) {  
      puts(__FUNCSIG__);  
   }  
  
   ~T() {  
      puts(__FUNCSIG__);  
   }  
  
   T& operator=(const T&) {  
      puts(__FUNCSIG__);  
      return *this;  
   }  
};  
  
struct S {  
   virtual void /* __clrcall */ f(T t) {};  
} s;  
  
int main() {  
   S* pS = &s;  
   T t;  
  
   printf("calling struct S\n");  
   pS->f(t);  
   printf("after calling struct S\n");  
}  
```  
  
### Resultados del ejemplo  
  
```  
__thiscall T::T(void)  
calling struct S  
__thiscall T::T(const struct T &)  
__thiscall T::T(const struct T &)  
__thiscall T::~T(void)  
__thiscall T::~T(void)  
after calling struct S  
__thiscall T::~T(void)  
```  
  
## Ejemplo  
  
### Descripción  
 En el ejemplo anterior se demostraba la existencia de doble código thunk.  Este ejemplo muestra su efecto.  El bucle `for` llama a la función virtual y el programa informa del motor en tiempo de ejecución.  Se obtiene el tiempo más lento cuando el programa se compila con **\/clr**.  Se obtiene el tiempo más rápido al compilar sin **\/clr** o si la función virtual se declara con `__clrcall`.  
  
### Código  
  
```  
// double_thunking_2.cpp  
// compile with: /clr  
#include <time.h>  
#include <stdio.h>   
  
#pragma unmanaged  
struct T {  
   T() {}  
   T(const T&) {}  
   ~T() {}  
   T& operator=(const T&) { return *this; }  
};  
  
struct S {  
   virtual void /* __clrcall */ f(T t) {};  
} s;  
  
int main() {  
   S* pS = &s;  
   T t;  
   clock_t start, finish;  
   double  duration;  
   start = clock();  
  
   for ( int i = 0 ; i < 1000000 ; i++ )  
      pS->f(t);  
  
   finish = clock();  
   duration = (double)(finish - start) / (CLOCKS_PER_SEC);  
   printf( "%2.1f seconds\n", duration );  
   printf("after calling struct S\n");  
}  
```  
  
### Resultados del ejemplo  
  
```  
4.2 seconds  
after calling struct S  
```  
  
## Vea también  
 [Ensamblados mixtos \(nativos y administrados\)](../dotnet/mixed-native-and-managed-assemblies.md)