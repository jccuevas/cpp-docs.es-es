---
title: "deprecated (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "deprecated"
  - "deprecated_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec (palabra clave) [C++], deprecated"
  - "__declspec (palabra clave desusada)"
ms.assetid: beef1129-9434-4cb3-8392-f1eb29e04805
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# deprecated (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\(Específico de Microsoft\) Con las excepciones que se indican a continuación, la declaración **deprecated** proporciona la misma funcionalidad que la directiva pragma [deprecated](../preprocessor/deprecated-c-cpp.md):  
  
-   La declaración **deprecated** permite especificar formas determinadas de sobrecargas de función como desusadas, mientras que la forma pragma se aplica a todas las formas sobrecargadas de un nombre de función.  
  
-   La declaración **deprecated** permite especificar un mensaje que se mostrará en tiempo de compilación.  El texto del mensaje puede proceder de una macro.  
  
-   Las macros solo se pueden marcar como desusadas con la directiva pragma **deprecated**.  
  
 Si el compilador encuentra el uso de un identificador desusado, se produce una advertencia [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo marcar funciones como desusadas y cómo especificar un mensaje que se mostrará, en tiempo de compilación, cuando se use la función desusada.  
  
```  
// deprecated.cpp  
// compile with: /W3  
#define MY_TEXT "function is deprecated"  
void func1(void) {}  
__declspec(deprecated) void func1(int) {}  
__declspec(deprecated("** this is a deprecated function **")) void func2(int) {}  
__declspec(deprecated(MY_TEXT)) void func3(int) {}  
  
int main() {  
   func1();  
   func1(1);   // C4996  
   func2(1);   // C4996  
   func3(1);   // C4996  
}  
```  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo marcar clases como desusadas y cómo especificar un mensaje que se mostrará, en tiempo de compilación, cuando se use la clase desusada.  
  
```  
// deprecate_class.cpp  
// compile with: /W3  
struct __declspec(deprecated) X {  
   void f(){}  
};  
  
struct __declspec(deprecated("** X2 is deprecated **")) X2 {  
   void f(){}  
};  
  
int main() {  
   X x;   // C4996  
   X2 x2;   // C4996  
}  
```  
  
## Vea también  
 [\_\_declspec](../cpp/declspec.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)