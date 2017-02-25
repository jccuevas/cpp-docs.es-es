---
title: "Error del compilador C2146 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2146"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2146"
ms.assetid: 6bfb7de6-6723-4486-9350-c66ef88d7a64
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# Error del compilador C2146
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

error de sintaxis: falta 'símbolo \(token\)' delante del identificador 'identificador'  
  
 El compilador esperaba `token` y encontró `identifier` en su lugar.  Causas posibles:  
  
1.  Error de escritura o de uso de mayúsculas.  
  
2.  Falta el especificador de tipo en la declaración del identificador.  
  
 Este error podría deberse a un error tipográfico.  El error [C2065](../../error-messages/compiler-errors-1/compiler-error-c2065.md) suele preceder a este error.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C2146.  
  
```  
// C2146.cpp  
class CDeclaredClass {};  
  
class CMyClass {  
   CUndeclared m_myClass;   // C2146  
   CDeclaredClass m_myClass2;   // OK  
};  
  
int main() {  
   int x;  
   int t x;   // C2146 : missing semicolon before 'x'  
}  
```  
  
## Ejemplo  
 Este error también puede producirse como resultado del trabajo de compatibilidad del compilador realizado para Visual Studio .NET 2003: falta la palabra clave `typename`.  
  
 El siguiente ejemplo compila en Visual Studio .NET 2002, pero genera errores en Visual Studio .NET 2003:  
  
```  
// C2146b.cpp  
// compile with: /c  
template <typename T>  
struct X {  
   struct Y {  
      int i;  
   };  
   Y memFunc();  
};  
  
template <typename T>  
X<T>::Y func() { }   // C2146  
  
// OK  
template <typename T>  
typename X<T>::Y func() { }  
```  
  
## Ejemplo  
 También podrá ver este error como resultado de un trabajo de compatibilidad del compilador realizado para Visual Studio .NET 2003: las especializaciones explícitas ya no buscan parámetros de plantilla desde plantillas principales.  
  
 En la especialización explícita no se permite el uso de `T` desde la plantilla principal.  Para que el código sea válido en las versiones Visual Studio .NET 2003 y Visual Studio .NET de Visual C\+\+, reemplace todas las instancias del parámetro de plantilla en la especialización por el tipo especializado explícitamente.  
  
 El código de ejemplo siguiente se compila en Visual Studio .NET, pero genera errores en Visual Studio .NET 2003:  
  
```  
// C2146_c.cpp  
// compile with: /c  
template <class T>   
struct S;  
  
template <>   
struct S<int> {  
   T m_t;   // C2146  
   int m_t2;   // OK  
};  
```