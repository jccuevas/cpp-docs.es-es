---
title: Compilador advertencia (nivel 1) C4503 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4503
dev_langs:
- C++
helpviewer_keywords:
- C4503
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: adafddff679cbe04cf26a39647760bf595af0bd3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4503"></a>Advertencia del compilador (nivel 1) C4503
'identificador': superada, la longitud del nombre representativo nombre se ha truncado  
  
 El nombre representativo es mayor que el límite del compilador (4096) y se ha truncado. Para evitar esta advertencia y el truncamiento, reduzca el número de argumentos o la longitud del nombre de los identificadores usados.  
  
 Una situación en la que se emitirá esta advertencia es cuando el código contiene plantillas especializadas en plantillas repetidamente.  Por ejemplo, un mapa de mapas (de la biblioteca estándar de C++).  En esta situación, puede hacer las definiciones de tipos un tipo (por ejemplo, struct) que contenga la asignación.  
  
 Sin embargo, podría decidir que no reestructurar el código.  Es posible distribuir una aplicación que genera la advertencia C4503, pero si se producen errores en tiempo de vínculo en un símbolo truncado, será más difícil determinar el tipo del símbolo en el error.  Depuración también resultará más difícil; el depurador también tendrá dificultades para asignar un nombre de símbolo para escribir el nombre.  La corrección del programa, sin embargo, se ve afectada por el nombre truncado.  
  
 El ejemplo siguiente genera la advertencia C4503:  
  
```  
// C4503.cpp  
// compile with: /W1 /EHsc /c  
// C4503 expected  
#include <string>  
#include <map>  
  
class Field{};  
  
typedef std::map<std::string, Field> Screen;  
typedef std::map<std::string, Screen> WebApp;  
typedef std::map<std::string, WebApp> WebAppTest;  
typedef std::map<std::string, WebAppTest> Hello;  
Hello MyWAT;  
```  
  
 El ejemplo siguiente muestra una manera de volver a escribir el código para resolver la advertencia C4503:  
  
```  
// C4503b.cpp  
// compile with: /W1 /EHsc /c  
#include <string>  
#include <map>  
  
class Field{};  
struct Screen2 {  
   std::map<std::string, Field> Element;  
};  
  
struct WebApp2 {  
   std::map<std::string, Screen2> Element;  
};  
  
struct WebAppTest2 {  
   std::map<std::string, WebApp2> Element;  
};  
  
struct Hello2 {  
   std::map<std::string, WebAppTest2> Element;  
};  
  
Hello2 MyWAT2;  
```