---
title: "for (Instrucci&#243;n) (C) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "for (palabra clave) [C]"
ms.assetid: 560a8de4-19db-4868-9f18-dbe51b17900d
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# for (Instrucci&#243;n) (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La instrucción `for` permite repetir una instrucción o una instrucción compuesta un número especificado de veces.  El cuerpo de una instrucción `for` se ejecuta cero o más veces hasta que una condición opcional sea false.  Puede utilizar expresiones opcionales dentro de la instrucción `for` para inicializar y cambiar valores durante la ejecución de la instrucción `for`.  
  
## Sintaxis  
 *iteration\-statement*:  
 `for` \( `init-expression` opt ; `cond-expression`opt ; `loop-expression` opt \)`statement`  
  
 La ejecución de una instrucción `for` continúa como sigue:  
  
1.  `init-expression`, si existe, se evalúa.  Especifica la inicialización del bucle.  No hay ninguna restricción sobre el tipo de `init-expression`.  
  
2.  `cond-expression`, si existe, se evalúa.  Esta expresión debe tener un tipo aritmético o de puntero.  Se evalúa antes de cada iteración.  Se pueden producir tres resultados:  
  
    -   Si `cond-expression` es true \(distinta de cero\), se ejecuta `statement`; a continuación, se evalúa `loop-expression`, si existe.  `loop-expression` se evalúa después de cada iteración.  No hay restricciones sobre su tipo.  Los efectos secundarios se ejecutarán en orden.  Entonces, comienza de nuevo el proceso con la evaluación de `cond-expression`.  
  
    -   Si se omite `cond-expression`, `cond-expression` se considera true, y la ejecución continúa exactamente como se ha descrito en el párrafo anterior.  Una instrucción `for` sin un argumento `cond-expression` solo finaliza cuando se ejecuta una instrucción `break` o `return` dentro del cuerpo de la instrucción o cuando se ejecuta `goto` \(para una instrucción con etiqueta fuera del cuerpo de la instrucción `for`\).  
  
    -   Si `cond-expression` es `false` \(0\), la ejecución de la instrucción `for` termina y se pasa el control a la siguiente instrucción del programa.  
  
 Una instrucción `for` también finaliza cuando se ejecuta una instrucción `break`, `goto` o `return` dentro del cuerpo de la instrucción.  Una instrucción `continue` en un bucle `for` hace que se evalúe `loop-expression`.  Cuando se ejecuta una instrucción `break` dentro de un bucle `for`, `loop-expression` no se evalúa ni se ejecuta.  Esta instrucción  
  
```  
for( ;; )  
```  
  
 es la forma habitual de generar un bucle infinito del que solo se puede salir con una instrucción `break`, `goto` o `return`.  
  
## Código  
 En este ejemplo se ilustra la instrucción `for`:  
  
```  
// c_for.c  
int main()  
{  
   char* line = "H e  \tl\tlo World\0";  
   int space = 0;  
   int tab = 0;  
   int i;  
   int max = strlen(line);  
   for (i = 0; i < max; i++ )   
   {  
      if ( line[i] == ' ' )  
      {  
          space++;  
      }  
      if ( line[i] == '\t' )  
      {  
          tab++;  
      }  
   }  
  
   printf("Number of spaces: %i\n", space);  
   printf("Number of tabs: %i\n", tab);  
   return 0;  
}  
```  
  
## Salida  
  
```  
Number of spaces: 4  
Number of tabs: 2  
```  
  
## Vea también  
 [Instrucciones](../c-language/statements-c.md)