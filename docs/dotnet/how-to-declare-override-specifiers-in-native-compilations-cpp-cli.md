---
title: "C&#243;mo: Declarar especificadores de invalidaci&#243;n en las compilaciones nativas (C++/CLI) | Microsoft Docs"
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
  - "especificadores de invalidación en compilaciones nativas, invalidar"
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Declarar especificadores de invalidaci&#243;n en las compilaciones nativas (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[sealed](../windows/sealed-cpp-component-extensions.md), [resumen](../windows/abstract-cpp-component-extensions.md), y [override](../windows/override-cpp-component-extensions.md) están disponibles en las compilaciones que no utilizan **\/ZW** o [\/clr](../build/reference/clr-common-language-runtime-compilation.md).  
  
> [!NOTE]
>  El lenguaje estándar ISO C\+\+11 tiene el identificador de [override](../cpp/override-specifier.md) y el identificador de [final](../cpp/final-specifier.md) , y ambos son compatibles con el uso `final` de Visual Studio en lugar de `sealed` en el código que se tienen que compilarse como nativos \- únicamente.  
  
## Ejemplo  
  
### Descripción  
 El ejemplo siguiente se muestra que `sealed` es válido en compila nativas.  
  
### Código  
  
```  
// sealed_native_keyword.cpp  
#include <stdio.h>  
__interface I1 {  
   virtual void f();  
   virtual void g();  
};  
  
class X : public I1 {  
public:  
   virtual void g() sealed {}  
};  
  
class Y : public X {  
public:  
  
   // the following override generates a compiler error  
   virtual void g() {}   // C3248 X::g is sealed!  
};  
```  
  
## Ejemplo  
  
### Descripción  
 El ejemplo siguiente se muestra que `override` es válido en compila nativas.  
  
### Código  
  
```  
// override_native_keyword.cpp  
#include <stdio.h>  
__interface I1 {  
   virtual void f();  
};  
  
class X : public I1 {  
public:  
   virtual void f() override {}   // OK  
   virtual void g() override {}   // C3668 I1::g does not exist  
};  
```  
  
## Ejemplo  
  
### Descripción  
 Este ejemplo muestra que `abstract` es válido en compila nativas.  
  
### Código  
  
```  
// abstract_native_keyword.cpp  
class X abstract {};  
  
int main() {  
   X * MyX = new X;   // C3622 cannot instantiate abstract class  
}  
```  
  
## Vea también  
 [Especificadores de invalidación](../windows/override-specifiers-cpp-component-extensions.md)