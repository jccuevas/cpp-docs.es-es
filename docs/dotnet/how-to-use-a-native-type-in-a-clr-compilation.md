---
title: "C&#243;mo: Utilizar un tipo nativo en una compilaci&#243;n con /clr | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr (opción del compilador) [C++], utilizar tipos nativos"
  - "compilación, tipos nativos en /clr"
ms.assetid: 3a505c90-4adb-4942-9cf9-7d1fdcbc01e7
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Utilizar un tipo nativo en una compilaci&#243;n con /clr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede definir un tipo nativo en una compilación con **\/clr** y cualquier uso de ese tipo nativo desde dentro del ensamblado será válido.  Sin embargo, los tipos nativos no estarán disponibles para su uso desde los metadatos a los que se hace referencia.  
  
 Cada ensamblado debe contener la definición de cada tipo nativo que utilice.  
  
 Para obtener más información, vea [\/clr \(Compilación de Common Language Runtime\)](../build/reference/clr-common-language-runtime-compilation.md).  
  
## Ejemplo  
 Este ejemplo crea un componente que define y utiliza un tipo nativo.  
  
```  
// use_native_type_in_clr.cpp  
// compile with: /clr /LD  
public struct NativeClass {  
   static int Test() { return 98; }  
};  
  
public ref struct ManagedClass {  
   static int i = NativeClass::Test();  
   void Test() {  
      System::Console::WriteLine(i);  
   }  
};  
```  
  
## Ejemplo  
 Este ejemplo define un cliente que utiliza el componente.  Observe que es un error para tener acceso al tipo nativo, a menos que se defina en el compilando.  
  
```  
// use_native_type_in_clr_2.cpp  
// compile with: /clr  
#using "use_native_type_in_clr.dll"  
// Uncomment the following 3 lines to resolve.  
// public struct NativeClass {  
//    static int Test() { return 98; }  
// };  
  
int main() {  
   ManagedClass x;  
   x.Test();  
  
   System::Console::WriteLine(NativeClass::Test());   // C2653  
}  
```  
  
## Vea también  
 [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)