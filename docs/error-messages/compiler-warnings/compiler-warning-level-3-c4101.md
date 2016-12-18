---
title: "Advertencia del compilador (nivel 3) C4101 | Microsoft Docs"
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
  - "C4101"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4101"
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 3) C4101
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : variable local sin referencia  
  
 La variable local nunca se utiliza.  Esta advertencia se produce en la siguiente situación:  
  
```  
// C4101a.cpp  
// compile with: /W3  
int main() {  
int i;   // C4101  
}  
```  
  
 Sin embargo, esta advertencia también se produce al llamar a una función miembro **static** a través de una instancia de la clase:  
  
```  
// C4101b.cpp  
// compile with:  /W3  
struct S {  
   static int func()  
   {  
      return 1;  
   }  
};  
  
int main() {  
   S si;   // C4101, si is never used  
   int y = si.func();  
   return y;  
}  
```  
  
 En esta situación, el compilador utiliza información acerca de `si` para obtener acceso a la función **static**, pero no es necesaria la instancia de la clase para llamar a la función **static**, de ahí la advertencia.  Para resolver este advertencia:  
  
-   Agregue un constructor, donde el compilador utilizará la instancia de `si` en la llamada a `func`.  
  
-   Quite la palabra clave **static** de la definición de `func`.  
  
-   Llame explícitamente a la función **static**: `int y = S::func();`.