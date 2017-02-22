---
title: "Operadores de direccionamiento indirecto y address-of | Microsoft Docs"
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
  - "& (operador), address-of (operador)"
  - "* (operador)"
  - "* (operador), address-of (operador)"
  - "* (operador), operador de direccionamiento indirecto"
  - "direcciones [C++]"
  - "direcciones [C++], direccionamiento indirecto"
  - "address-of (operador) (&)"
  - "operador y comercial (&)"
  - "operador de direccionamiento indirecto"
  - "punteros null [C++]"
  - "operadores [C++], address-of"
  - "operadores [C++], direccionamiento indirecto"
ms.assetid: 10d62b00-12ba-4ea9-a2d5-09ac29ca2232
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Operadores de direccionamiento indirecto y address-of
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El operador de direccionamiento indirecto \(**\***\) tiene acceso a un valor indirectamente, mediante un puntero.  El operando debe ser un valor de puntero.  El resultado de la operación es el valor al que hace referencia el operando; es decir, el valor de la dirección a la que señala el operando.  El tipo del resultado es el tipo al que apunta el operando.  
  
 Si el operando señala a una función, el resultado es un designador de función.  Si señala a una ubicación de almacenamiento, el resultado es un valor L que designa la ubicación de almacenamiento.  
  
 Si el valor de puntero no es válido, el resultado es indefinido.  La lista siguiente incluye algunas de las condiciones más comunes que invalidan un valor de puntero.  
  
-   El puntero es un puntero null.  
  
-   El puntero especifica la dirección de un elemento local que no está visible en el momento de la referencia.  
  
-   El puntero especifica una dirección que está alineada de una forma no adecuada para el tipo de objeto al que se señala.  
  
-   El puntero especifica una dirección no utilizada por el programa que se ejecuta.  
  
 El operador address\-of \(**&**\) proporciona la dirección de su operando.  El operando del operador address\-of puede ser un designador de función o un valor L que designe un objeto que no es un campo de bits y no se declara con el especificador de clase de almacenamiento **register**.  
  
 El resultado de la operación de dirección es un puntero al operando.  El tipo al que señala el puntero es el tipo del operando.  
  
 El operador address\-of solo se puede aplicar a variables con tipos fundamentales, de estructura o de unión que se declaren en el nivel de ámbito de archivo o para referencias de matriz de subíndice.  En estas expresiones, se puede agregar o quitar de la expresión de dirección una expresión constante que no incluya el operador address\-of.  
  
## Ejemplos  
 En los ejemplos siguientes se usan estas declaraciones:  
  
```  
int *pa, x;  
int a[20];  
double d;  
```  
  
 Esta instrucción utiliza el operador address\-of:  
  
```  
pa = &a[5];  
```  
  
 El operador address\-of \(**&**\) toma la dirección del sexto elemento de la matriz `a`.  El resultado se almacena en la variable de puntero `pa`.  
  
```  
x = *pa;  
```  
  
 En este ejemplo se utiliza el operador de direccionamiento indirecto \(**\***\) para tener acceso al valor `int` en la dirección almacenada en `pa`.  El valor se asigna a la variable de entero `x`.  
  
```  
if( x == *&x )  
    printf( "True\n" );  
```  
  
 Este ejemplo imprime la palabra `True`, que demuestra que el resultado de aplicar el operador de direccionamiento indirecto a la dirección de `x` es igual que `x`.  
  
```  
int roundup( void );     /* Function declaration */  
  
int  *proundup  = roundup;  
int  *pround  = &roundup;  
```  
  
 Una vez declarada la función `roundup`, se declaran y se inicializan dos punteros a `roundup`.  El primer puntero, `proundup`, se inicializa solo con el nombre de la función, mientras que el segundo, `pround`, utiliza el operador address\-of en la inicialización.  Las inicializaciones son equivalentes.  
  
## Vea también  
 [Operador de direccionamiento indirecto: \*](../cpp/indirection-operator-star.md)   
 [Operador address\-of: &](../cpp/address-of-operator-amp.md)