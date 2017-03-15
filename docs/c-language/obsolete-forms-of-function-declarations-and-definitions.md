---
title: "Formas obsoletas de declaraciones y definiciones de funci&#243;n | Microsoft Docs"
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
  - "declaraciones de función de estilo antiguo"
ms.assetid: 67c5038f-0529-4f29-9d0f-c27580977b50
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Formas obsoletas de declaraciones y definiciones de funci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las declaraciones y definiciones de función de estilo antiguo usan reglas para declarar parámetros ligeramente distintas de la sintaxis recomendada por el estándar ANSI C.  En primer lugar, las declaraciones de estilo antiguo no tienen una lista de parámetros.  En segundo lugar, en la definición de función, se enumeran los parámetros, pero no se declaran sus tipos en la lista de parámetros.  Las declaraciones de tipos preceden a la instrucción compuesta que constituye el cuerpo de la función.  La sintaxis de estilo antiguo está obsoleta y no se debe utilizar en código nuevo.  Sin embargo, se sigue admitiendo el código que utiliza la sintaxis de estilo antiguo.  En este ejemplo se muestran formas obsoletas de declaraciones y definiciones:  
  
```  
double old_style();           /* Obsolete function declaration */  
  
double alt_style( a , real )  /* Obsolete function definition */  
    double *real;   
    int a;   
{  
    return ( *real + a ) ;  
}  
```  
  
 No es necesario que las funciones que devuelven un entero o un puntero con el mismo tamaño que `int` tengan una declaración, aunque sí es recomendable.  
  
 Para cumplir con el estándar ANSI C, las declaraciones de función de estilo antiguo que usan puntos suspensivos ahora generan un error al compilar con la opción \/Za y una advertencia de nivel 4 al compilar con \/Ze.  Por ejemplo:  
  
```  
void funct1( a, ... )  /* Generates a warning under /Ze or */  
int a;                 /* an error when compiling with /Za */  
{  
}  
```  
  
 Debe volver a escribir esta declaración como un prototipo:  
  
```  
void funct1( int a, ... )  
{  
}  
```  
  
 Las declaraciones de función de estilo antiguo también generan advertencias si posteriormente se declara o se define la misma función con puntos suspensivos o un parámetro con un tipo que no es igual que su tipo promovido.  
  
 En la sección siguiente, [Definiciones de funciones de C](../c-language/c-function-definitions.md), se muestra la sintaxis de las definiciones de función, incluida la sintaxis de estilo antiguo.  El elemento no terminal de la lista de parámetros en la sintaxis de estilo antiguo es *identifier\-list*.  
  
## Vea también  
 [Información general de funciones](../c-language/overview-of-functions.md)