---
title: "switch (Instrucci&#243;n) (C++) | Microsoft Docs"
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
  - "default"
  - "default_cpp"
  - "switch"
  - "switch_cpp"
  - "case"
  - "case_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "case (palabra clave) [C++], en instrucciones switch"
  - "default (palabra clave) [C++]"
  - "switch (palabra clave) [C++]"
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# switch (Instrucci&#243;n) (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Permite la selección entre varias secciones de código, dependiendo del valor de una expresión entera.  
  
## Sintaxis  
  
```  
  
      switch ( expression )  
   case constant-expression : statement  
   [default  : statement]  
```  
  
## Comentarios  
 El elemento *expression* debe ser de un tipo entero o de un tipo de clase para el que haya una conversión no ambigua a un tipo entero.  La promoción de entero se realiza como se describe en [Promociones de entero](../misc/integral-promotions.md).  
  
 El cuerpo de la instrucción `switch` consta de una serie de etiquetas **case** y una etiqueta opcional **default**.  Ninguna de la dos expresiones constantes en las instrucciones **case** se puede evaluar en el mismo valor.  La etiqueta **default** solo puede aparecer una vez.  Las instrucciones con etiquetas no son requisitos sintácticos, pero la instrucción `switch` no tiene sentido sin ellas.   La instrucción predeterminada no necesita estar al final; puede aparecer en cualquier parte del cuerpo de la instrucción switch.  Una etiqueta case o default solo puede aparecer en una instrucción switch.  
  
 El elemento *constant\-expression* de cada etiqueta **case** se convierte al tipo de *expression* y se compara con *expression* para determinar si son iguales.  El control pasa a la instrucción que tenga el mismo valor en **case** *constant\-expression* que en *expression*.  El comportamiento resultante se muestra en la siguiente tabla.  
  
### Comportamiento de la instrucción switch  
  
|Condition|Acción|  
|---------------|------------|  
|El valor convertido coincide con el de la expresión de control promovida.|El control se transfiere a la instrucción que sigue a esa etiqueta.|  
|Ninguna de las constantes coincide con las constantes de las etiquetas **case**; hay una etiqueta **default**.|El control se transfiere a la etiqueta **default**.|  
|Ninguna de las constantes coincide con las constantes en las etiquetas **case**; no hay una etiqueta **default**.|El control se transfiere a la instrucción situada detrás de la instrucción `switch`.|  
  
 Si se encuentra una expresión coincidente, las etiquetas **case** o **default** siguientes no impiden que se transfiera el control.  La instrucción [break](../cpp/break-statement-cpp.md) se utiliza para detener la ejecución y transferir el control a la instrucción situada detrás de la instrucción `switch`.  Sin una instrucción **break**, se ejecuta cada instrucción de la etiqueta **case** coincidente hasta el final de la instrucción `switch`, incluida **default**.  Por ejemplo:  
  
```  
// switch_statement1.cpp  
#include <stdio.h>  
  
int main() {  
   char *buffer = "Any character stream";  
   int capa, lettera, nota;  
   char c;  
   capa = lettera = nota = 0;  
  
   while ( c = *buffer++ )   // Walks buffer until NULL  
   {  
      switch ( c )  
      {  
         case 'A':  
            capa++;  
            break;  
         case 'a':  
            lettera++;  
            break;  
         default:  
            nota++;  
      }  
   }  
   printf_s( "\nUppercase a: %d\nLowercase a: %d\nTotal: %d\n",  
      capa, lettera, (capa + lettera + nota) );  
}  
```  
  
 En el ejemplo anterior, se incrementa `capa` si `c` es una `A` mayúscula.  La instrucción `break` detrás de `capa++` finaliza la ejecución del cuerpo de la instrucción `switch` y el control pasa al bucle `while`.  Sin la instrucción `break`, `lettera` y `nota` también se incrementarían.  La instrucción `break` para `case 'a'` tiene un propósito similar.  Si `c` es una `a` minúscula, `lettera` se incrementa y la instrucción `break` finaliza el cuerpo de la instrucción `switch`.  Si `c` no es `a` ni `A`, se ejecuta la instrucción `default`.  
  
 Un bloque interno de una instrucción `switch` puede contener definiciones con inicializaciones siempre que se pueda tener acceso a ellas, es decir, siempre que las rutas de ejecución posibles no las omitan.  Los nombres proporcionados mediante estas declaraciones tienen ámbito local.  Por ejemplo:  
  
```  
// switch_statement2.cpp  
// C2360 expected  
#include <iostream>  
using namespace std;  
int main(int argc, char *argv[])  
{  
   switch( tolower( *argv[1] ) )  
   {  
       // Error. Unreachable declaration.  
       char szChEntered[] = "Character entered was: ";  
  
   case 'a' :  
       {  
       // Declaration of szChEntered OK. Local scope.  
       char szChEntered[] = "Character entered was: ";  
       cout << szChEntered << "a\n";  
       }  
       break;  
  
   case 'b' :  
       // Value of szChEntered undefined.  
       cout << szChEntered << "b\n";  
       break;  
  
   default:  
       // Value of szChEntered undefined.  
       cout << szChEntered << "neither a nor b\n";  
       break;  
   }  
}  
```  
  
 Una instrucción `switch` puede estar anidada.  En tal caso, las etiquetas **case** o **default** se asocian con la instrucción `switch` más cercana que las contenga.  
  
## Específicos de Microsoft  
 Microsoft C no limita el número de valores case en una instrucción `switch`.  El número solo está limitado por la memoria disponible.  ANSI C requiere que al menos 257 etiquetas case se permitan en una instrucción `switch`.  
  
 El valor predeterminado para Microsoft C es que las extensiones de Microsoft estén habilitadas.  Utilice la opción de compilador [\/Za](../build/reference/za-ze-disable-language-extensions.md) para deshabilitar estas extensiones.  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Instrucciones de selección](../cpp/selection-statements-cpp.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [\(NOTINBUILD\) Using Labels in the case Statement](http://msdn.microsoft.com/es-es/a6ff057d-1aee-42ed-a28d-ee6a565b3197)