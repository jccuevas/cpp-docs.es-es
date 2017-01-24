---
title: "Advertencia del compilador (nivel 1) C4503 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4503"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4503"
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4503
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : se ha superado la longitud del nombre representativo, el nombre aparece truncado  
  
 La longitud del nombre representativo es mayor que el límite del compilador \(4096\), por lo que ha sido truncado.  Para evitar esta advertencia y el truncamiento, reduzca el número de argumentos o la longitud del nombre de los identificadores.  
  
 Una situación en la que se emitirá esta advertencia es cuando el código contiene plantillas especializadas en plantillas repetidamente.  Por ejemplo, un mapa de mapas \(de la Biblioteca estándar de C\+\+\).  En esta situación, puede hacer de las definiciones de tipos un tipo \(por ejemplo, struct\) que contenga el mapa.  
  
 No obstante, podría optar por no reestructurar el código.  Es posible distribuir una aplicación que genere la advertencia C4503, pero si se producen errores en tiempo de vinculación en un símbolo truncado, será más difícil determinar el tipo del símbolo en el error.  La depuración también resultará más difícil; además, el depurador tendrá dificultades para asignar un nombre de símbolo a un nombre de tipo.  Sin embargo, el nombre truncado no afecta a la corrección del programa.  
  
 El código siguiente genera el error C4503:  
  
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
  
 El ejemplo siguiente muestra una manera de volver a escribir un código para resolver la advertencia C4503:  
  
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