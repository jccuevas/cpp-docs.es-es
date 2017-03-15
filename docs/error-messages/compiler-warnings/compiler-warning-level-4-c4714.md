---
title: "Advertencia del compilador (nivel 4) C4714 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4714"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4714"
ms.assetid: 22c7fd0c-899d-4e9b-95f3-725b2c49fb46
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (nivel 4) C4714
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la función 'función' marcada como \_\_forceinline no está entre líneas  
  
 La función dada fue seleccionada para la expansión en línea, pero el compilador no realizó la expansión.  
  
 Si bien `__forceinline` es una indicación de mayor prioridad para el compilador que `__inline`, la inclusión en línea continúa realizándose a discreción del compilador, pero no se utiliza heurística para determinar los beneficios de aplicar la inclusión a esta función.  
  
 En algunos casos, el compilador no incluye en línea una determinada función por motivos mecánicos.  Por ejemplo, el compilador no incluirá en línea:  
  
-   Una función si como resultado de ello se mezcla SEH y C\+\+ EH.  
  
-   Algunas funciones con objetos construidos mediante copia y pasados por valor con la opción GX\/EHs\/EHa activada.  
  
-   Algunas funciones que devuelven un objeto no desenredable por valor con la opción GX\/EHs\/EHa activada.  
  
-   Las funciones que contienen ensamblado en línea al compilar sin \-Og\/Ox\/O1\/O2.  
  
-   Las funciones con una lista de argumentos de variable.  
  
-   Una función con una instrucción **try** \(control de excepciones de C\+\+\).  
  
 El código siguiente genera el error C4714:  
  
```  
// C4714.cpp  
// compile with: /Ob1 /GX /W4  
__forceinline void func1()  
{  
   try  
   {  
   }  
   catch (...)  
   {  
   }  
}  
  
void func2()  
{  
   func1();   // C4714  
}  
  
int main()  
{  
}  
```