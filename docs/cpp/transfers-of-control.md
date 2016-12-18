---
title: "Transferencias del control | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "flujo de control, bifurcación"
  - "flujo de control, transferir control"
ms.assetid: aa51e7f2-060f-4106-b0fe-331f04357423
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Transferencias del control
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede utilizar la instrucción `goto` o una etiqueta **case** en una instrucción `switch` para especificar un programa que se bifurque más allá de un inicializador.  Este código no es válido a menos que la declaración que contenga el inicializador esté en un bloque dentro del bloque en el que aparezca la instrucción de salto.  
  
 En el ejemplo siguiente se muestra un bucle que declara e inicializa los objetos `total`, `ch` y `i`.  Hay también una instrucción `goto` errónea que transfiere el control más allá de un inicializador.  
  
```  
// transfers_of_control.cpp  
// compile with: /W1  
// Read input until a nonnumeric character is entered.  
int main()  
{  
   char MyArray[5] = {'2','2','a','c'};  
   int i = 0;  
   while( 1 )  
   {  
      int total = 0;  
  
      char ch = MyArray[i++];  
  
      if ( ch >= '0' && ch <= '9' )  
      {  
         goto Label1;  
  
         int i = ch - '0';  
      Label1:  
         total += i;   // C4700: transfers past initialization of i.  
      } // i would be destroyed here if  goto error were not present  
   else  
      // Break statement transfers control out of loop,  
      //  destroying total and ch.  
      break;  
   }  
}  
```  
  
 En el ejemplo anterior, la instrucción `goto` intenta transferir el control más allá de la inicialización de `i`.  Sin embargo, si se declarara `i` pero no se inicializara, la transferencia sería válida.  
  
 Los objetos `total` y `ch`, declarados en el bloque que sirve como *statement* de la instrucción `while`, se destruyen cuando se usa la instrucción `break` para salir del bloque.  
  
## Vea también  
 [\(NOTINBUILD\) Declaration of Automatic Objects](http://msdn.microsoft.com/es-es/81f941e9-c1b1-4d1c-a28d-70b6ee9765db)