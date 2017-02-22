---
title: "Programa de ejemplo | Microsoft Docs"
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
ms.assetid: fc22ef82-9caa-425f-b201-2891bc123d1f
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Programa de ejemplo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El siguiente programa de origen de C se compone de dos archivos de código fuente.  Proporciona información general sobre las distintas declaraciones y definiciones posibles en un programa de C.  En las secciones posteriores de este libro se describe cómo escribir estas declaraciones, definiciones e inicializaciones, y cómo utilizar las palabras clave de C **static** y `extern`.  La función `printf` se declara en el archivo de encabezado de C STDIO.H.  
  
 Se supone que las funciones `main` y `max` están en archivos independientes y la ejecución del programa comienza con la función `main`.  No se ejecuta ninguna función de usuario explícita antes de `main`.  
  
```  
/*****************************************************************  
                    FILE1.C - main function  
*****************************************************************/  
  
#define ONE     1  
#define TWO     2  
#define THREE   3  
#include <stdio.h>  
  
int a = 1;                       // Defining declarations      
int b = 2;                       //  of external variables      
  
extern int max( int a, int b );  // Function prototype          
  
int main()                       // Function definition         
{                                //  for main function          
    int c;                       // Definitions for      
    int d;                       //  two uninitialized  
                                 //  local variables  
  
    extern int u;                // Referencing declaration     
                                 //  of external variable       
                                 //  defined elsewhere          
    static int v;                // Definition of variable      
                                 //  with continuous lifetime   
  
    int w = ONE, x = TWO, y = THREE;  
    int z = 0;  
  
    z = max( x, y );             // Executable statements      
    w = max( z, w );  
    printf_s( "%d %d\n", z, w );  
    return 0;  
}  
  
/****************************************************************  
            FILE2.C - definition of max function  
****************************************************************/  
  
int max( int a, int b )          // Note formal parameters are     
                                 //  included in function header   
{  
    if( a > b )  
        return( a );  
    else  
        return( b );  
}  
```  
  
 FILE1.C contiene el prototipo de la función `max`.  Este tipo de declaración se denomina a veces "declaración adelantada" porque la función se declara antes de que se utilice.  La definición de la función `main` incluye llamadas a `max`.  
  
 Las líneas a partir de `#define` son directivas de preprocesador.  Estas directivas indican al preprocesador que reemplace los identificadores `ONE`, `TWO` y `THREE` por los números `1`, `2` y `3`, respectivamente, en FILE1.C.  Sin embargo, las directivas no se aplican a FILE2.C, que se compila por separado y se vincula con FILE1.C.  La línea a partir de `#include` indica al compilador que incluya el archivo STDIO.H, que contiene el prototipo de la función `printf`.  Las [directivas de preprocesador](../preprocessor/preprocessor-directives.md) se explican en la *Referencia del preprocesador*.  
  
 FILE1.C utiliza la definición de declaraciones para inicializar las variables globales `a` y `b`.  Las variables locales `c` y `d` se declaran pero no se inicializan.  El almacenamiento se asigna para todas estas variables.  Las variables estáticas y externas, `u` y `v`, se inicializan automáticamente en 0.  Por consiguiente solo `a`, `b`, `u` y `v` contienen valores significativos cuando se declaran porque se inicializan, ya sea de forma implícita o explícita.  FILE2.C contiene la definición de función para `max`.  Esta definición satisface las llamadas a `max` en FILE1.C.  
  
 La duración y la visibilidad de identificadores se tratan en [Duración, ámbito, visibilidad y vinculación](../c-language/lifetime-scope-visibility-and-linkage.md).  Para obtener más información sobre las funciones, vea [Funciones](../c-language/functions-c.md).  
  
## Vea también  
 [Archivos de código fuente y programas de origen](../c-language/source-files-and-source-programs.md)