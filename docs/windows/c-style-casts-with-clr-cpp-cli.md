---
title: "Conversiones de estilo C con /clr (C++/CLI) | Microsoft Docs"
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
  - "conversiones de estilo C y /clr"
ms.assetid: d2a4401a-156a-4da9-8d12-923743e26913
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Conversiones de estilo C con /clr (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El tema siguiente se aplica sólo a Common Language Runtime.  
  
 Cuando se utiliza con los tipos de CLR, el compilador intenta asignar el estilo de C echado a una de las conversiones que se enumeran a continuación, en el orden siguiente:  
  
1.  const\_cast  
  
2.  safe\_cast  
  
3.  safe\_cast más const\_cast  
  
4.  static\_cast  
  
5.  static\_cast más const\_cast  
  
 Si ninguna de las conversiones enumeradas anteriormente son válidas, y si el tipo de la expresión y el tipo de destino son tipos de referencia CLR, se asigna la conversión de estilo C a tiempo de ejecución\- CHECK \(instrucción de MSIL de los castclass\).  Si no, c. la conversión de estilo se considera no válido y el compilador emite un error.  
  
## Comentarios  
 C. la conversión de estilo no se recomienda.  Al compilar con [\/clr \(Compilación de Common Language Runtime\)](../build/reference/clr-common-language-runtime-compilation.md), utilice [safe\_cast](../windows/safe-cast-cpp-component-extensions.md).  
  
 El ejemplo siguiente muestra c. el estilo echado que asigna a `const_cast`.  
  
```  
// cstyle_casts_1.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct R {};  
int main() {  
   const R^ constrefR = gcnew R();  
   R^ nonconstR = (R^)(constrefR);   
}  
```  
  
 El ejemplo siguiente muestra c. el estilo echado que asigna a `safe_cast`.  
  
```  
// cstyle_casts_2.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   Object ^ o = "hello";  
   String ^ s = (String^)o;  
}  
```  
  
 El ejemplo siguiente muestra c. el estilo echado que asigna a `safe_cast` más `const_cast`.  
  
```  
// cstyle_casts_3.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct R {};  
ref struct R2 : public R {};  
  
int main() {  
   const R^ constR2 = gcnew R2();  
   try {  
   R2^ b2DR = (R2^)(constR2);  
   }  
   catch(InvalidCastException^ e) {  
      System::Console::WriteLine("Invalid Exception");  
   }  
}  
```  
  
 El ejemplo siguiente muestra c. el estilo echado que asigna a `static_cast`.  
  
```  
// cstyle_casts_4.cpp  
// compile with: /clr  
using namespace System;  
  
struct N1 {};  
struct N2 {  
   operator N1() {  
      return N1();  
   }  
};  
  
int main() {  
   N2 n2;  
   N1 n1 ;  
   n1 = (N1)n2;  
}  
```  
  
 El ejemplo siguiente muestra c. el estilo echado que asigna a `static_cast` más `const_cast`.  
  
```  
// cstyle_casts_5.cpp  
// compile with: /clr  
using namespace System;  
struct N1 {};  
  
struct N2 {  
   operator const N1*() {  
      static const N1 n1;  
      return &n1;  
   }  
};  
  
int main() {  
   N2 n2;  
   N1* n1 = (N1*)(const N1*)n2;   // const_cast + static_cast  
}  
```  
  
 El ejemplo siguiente muestra c. el estilo echado que asigna a una comprobación en tiempo de ejecución.  
  
```  
// cstyle_casts_6.cpp  
// compile with: /clr  
using namespace System;  
  
ref class R1 {};  
ref class R2 {};  
  
int main() {  
   R1^ r  = gcnew R1();  
   try {  
      R2^ rr = ( R2^)(r);  
   }  
   catch(System::InvalidCastException^ e) {  
      Console::WriteLine("Caught expected exception");  
   }  
}  
```  
  
 El ejemplo siguiente se muestra una conversión no válida de estilo C, que hace que el compilador emita un error.  
  
```  
// cstyle_casts_7.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   String^s = S"hello";  
   int i = (int)s;   // C2440  
}  
```  
  
## Requisitos  
 Opción del compilador: **\/clr**  
  
## Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)