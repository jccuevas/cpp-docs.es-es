---
title: en desuso (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- deprecated_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], deprecated
- deprecated __declspec keyword
ms.assetid: beef1129-9434-4cb3-8392-f1eb29e04805
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 9ac25648e2d19da82f6c213992699c237e05c01e
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="deprecated-c"></a>en desuso (C++)
Este tema trata sobre la específicos de Microsoft modificador declspec declaración en desuso. Para obtener información sobre C ++ 14 `[[deprecated]]` atributo y orientación sobre cuándo usar ese atributo frente al modificador declspec específicos de Microsoft o la directiva pragma, consulte [atributos estándar de C++](attributes2.md).

 Con las excepciones que se indican a continuación, el **en desuso** declaración ofrece la misma funcionalidad que la [en desuso](../preprocessor/deprecated-c-cpp.md) pragma:  
  
-   El **en desuso** declaración permite especificar formas determinadas de sobrecargas de función como en desuso, mientras que la forma pragma se aplica a todas las formas sobrecargadas de un nombre de función.  
  
-   El **en desuso** declaración le permite especificar un mensaje que se mostrará en tiempo de compilación. El texto del mensaje puede proceder de una macro.  
  
-   Macros solo se pueden marcar como desusadas con la **en desuso** pragma.  
  
 Si el compilador encuentra el uso de un identificador en desuso o la norma [ `[[deprecated]]` ](attributes2.md) atributo, un [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) se produce la advertencia.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo marcar funciones como en desuso y cómo especificar un mensaje que se mostrará, en tiempo de compilación, cuando se use la función en desuso.  
  
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
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo marcar clases como en desuso y cómo especificar un mensaje que se mostrará, en tiempo de compilación, cuando se use la clase en desuso.  
  
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
  
## <a name="see-also"></a>Vea también  
 [__declspec](../cpp/declspec.md)   
 [Palabras clave](../cpp/keywords-cpp.md)
