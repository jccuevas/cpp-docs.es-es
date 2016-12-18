---
title: "Compiler Error C2355 | Microsoft Docs"
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
  - "C2355"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2355"
ms.assetid: 0a947881-d61f-4f98-8409-32140f39500b
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compiler Error C2355
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'this': solo se puede hacer referencia a this en funciones miembro no estáticas o inicializadores de miembro de datos no estáticos  
  
 El puntero `this` solo es válido en funciones miembro no estáticas o en inicializadores de miembro de datos no estáticos.  Este error puede producirse si el ámbito de clase de una definición de función miembro fuera de la declaración de clase no está calificado correctamente.  El error también puede producirse si el puntero `this` se utiliza en una función que no se haya declarado en la clase.  
  
 Para corregir este problema, asegúrese de que la definición de función miembro coincida con una declaración de función miembro de la clase y que no se haya declarado como estática.  En los inicializadores de miembro de datos, asegúrese de que el miembro de datos no se haya declarado como estático.  
  
 El ejemplo siguiente genera el error C2355 y muestra cómo corregirlo:  
  
```  
// C2355.cpp  
// compile with: /c  
class MyClass {};  
MyClass *p = this;   // C2355  
  
// OK  
class MyClass2 {  
public:  
   void Test() {  
      MyClass2 *p = this;  
   }  
};  
```