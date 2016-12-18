---
title: "Advertencia del compilador (nivel 1) C4540 | Microsoft Docs"
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
  - "C4540"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4540"
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4540
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

dynamic\_cast se ha utilizado para realizar la conversión a base inaccesible o ambigua; se producirá un error de prueba en tiempo de ejecución \('tipo1' a 'tipo2'\)  
  
 Se usó `dynamic_cast` para convertir de un tipo a otro.  El compilador determinó que la conversión fallaría en todos los casos \(devolvería **NULL**\) porque una clase base es inaccesible \(`private`, por ejemplo\) o ambigua \(aparece más de una vez en la jerarquía de clases, por ejemplo\).  
  
 El siguiente ejemplo muestra un ejemplo de esta advertencia.  La clase **B** se deriva de la clase **A**.  El programa usa `dynamic_cast` para convertir de la clase **B** \(la clase derivada\) a la clase **A**, que siempre se producirá un error porque la clase **B** es `private` y, por tanto, inaccesible.  Cambiar el tipo de acceso de **A** a **público** resolverá la advertencia.  
  
```  
// C4540.cpp  
// compile with: /W1  
  
struct A {   
   virtual void g() {}  
};  
  
struct B : private A {  
   virtual void g() {}  
};  
  
int main() {  
   B b;  
   A * ap = dynamic_cast<A*>(&b);   // C4540  
}  
```