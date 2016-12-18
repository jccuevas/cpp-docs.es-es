---
title: "Operador de pegado de token (##) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "##"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "## (operador de preprocesador)"
  - "preprocesador, operadores"
ms.assetid: 4f173503-990f-4bff-aef3-ec4d1f1458ef
caps.latest.revision: 10
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Operador de pegado de token (##)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El operador de signo de número doble o “pegado de token” \(**\#\#**\), que a veces se denomina operador de "combinación", se utiliza en las macros de tipo de objeto y de tipo de función.  Permite que se unan tokens distintos en un solo token y, por tanto, no puede ser el primero ni el último token en la definición de macro.  
  
 Si un parámetro formal en una definición de macro va precedido o seguido del operador de pegado de token, el parámetro formal se sustituye inmediatamente por el argumento real sin expandir.  La expansión de la macro no se realiza en el argumento antes de la sustitución.  
  
 A continuación, se quitan todas las apariciones del operador de pegado de token en el elemento *token\-string* y se concatenan los tokens que aparecen delante y detrás.  El token resultante debe ser un token válido.  Si es válido, el token se analiza para una posible sustitución en caso de que represente un nombre de macro.  El identificador representa el nombre por el que se conocerán los tokens concatenados en el programa antes de la sustitución.  Cada token representa un token definido en alguna parte, ya sea dentro del programa o en la línea de comandos del compilador.  El espacio en blanco que precede o que sigue al operador es opcional.  
  
 En este ejemplo se muestra el uso de los operadores de generación de cadenas y de pegado de token al especificar la salida del programa:  
  
```  
#define paster( n ) printf_s( "token" #n " = %d", token##n )  
int token9 = 9;  
```  
  
 Si se llama a una macro con un argumento numérico como  
  
```  
paster( 9 );  
```  
  
 la macro produce  
  
```  
printf_s( "token" "9" " = %d", token9 );  
```  
  
 que se convierte en  
  
```  
printf_s( "token9 = %d", token9 );  
```  
  
## Ejemplo  
  
```  
// preprocessor_token_pasting.cpp  
#include <stdio.h>  
#define paster( n ) printf_s( "token" #n " = %d", token##n )  
int token9 = 9;  
  
int main()  
{  
   paster(9);  
}  
```  
  
  **token9 \= 9**   
## Vea también  
 [Operadores de preprocesador](../preprocessor/preprocessor-operators.md)