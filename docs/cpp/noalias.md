---
title: "noalias | Microsoft Docs"
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
  - "noalias"
  - "noalias_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec (palabra clave) [C++], noalias"
  - "noalias __declspec (palabra clave)"
ms.assetid: efafa8b0-7f39-4edc-a81e-d287ae882c9b
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# noalias
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 `noalias` significa que una llamada de función no modifica el estado global visible ni hace referencia a él y solo modifica la memoria designada `directly` por los parámetros de puntero \(direccionamientos indirectos de primer nivel\).  
  
 Si una función está marcada como `noalias`, el optimizador puede suponer que, además de los parámetros en sí mismos, dentro de la función solo se modifican los direccionamientos indirectos de primer nivel de los parámetros del puntero o se hace referencia a ellos.  El estado global visible es el conjunto de todos los datos que no están definidos o a los que no se hace referencia fuera del ámbito de la compilación, y su dirección no se toma.  El ámbito de la compilación son todos los archivos de código fuente \(compilaciones de [\/LTCG \(Generación de código en tiempo de enlace\)](../build/reference/ltcg-link-time-code-generation.md)\) o un único archivo de código fuente \(compilaciones que no son de **\/LTCG**\).  
  
## Ejemplo  
 En el siguiente ejemplo de código se demuestra cómo usar `__declspec(restrict)` y `__declspec(noalias)`.  Normalmente, la memoria devuelta de `malloc` es `restrict` y `noalias` porque los encabezados de CRT se decoran correctamente.  
  
 Sin embargo, en este ejemplo, los punteros `mempool` y `memptr` son globales, por lo que el compilador no tiene ninguna garantía de que la memoria no está sujeta a alias.  Al decorar las funciones que devuelven punteros con `__declspec(restrict)`, se indica al compilador que la memoria indicada por el valor devuelto no tiene alias.  
  
 Al decorar la función del ejemplo que tiene acceso a la memoria con `__declspec(noalias)`, se indica al compilador que esta función no interfiere con el estado global, excepto a través de los punteros de su lista de parámetros.  
  
```  
// declspec_noalias.c   
#include <stdio.h>  
#include <stdlib.h>  
  
#define M 800  
#define N 600  
#define P 700  
  
float * mempool, * memptr;  
  
__declspec(restrict) float * ma(int size)  
{  
    float * retval;  
    retval = memptr;  
    memptr += size;  
    return retval;  
}  
  
__declspec(restrict) float * init(int m, int n)  
{  
    float * a;  
    int i, j;  
    int k=1;  
  
    a = ma(m * n);  
    if (!a) exit(1);  
    for (i=0; i<m; i++)  
        for (j=0; j<n; j++)  
            a[i*n+j] = 0.1/k++;  
    return a;  
}  
  
__declspec(noalias) void multiply(float * a, float * b, float * c)  
{  
    int i, j, k;  
  
    for (j=0; j<P; j++)  
        for (i=0; i<M; i++)  
            for (k=0; k<N; k++)  
                c[i * P + j] =   
                          a[i * N + k] *   
                          b[k * P + j];  
}  
  
int main()  
{  
    float * a, * b, * c;  
  
    mempool = (float *) malloc(sizeof(float) * (M*N + N*P + M*P));  
  
    if (!mempool)   
    {  
        puts("ERROR: Malloc returned null");  
        exit(1);  
    }  
  
    memptr = mempool;  
    a = init(M, N);  
    b = init(N, P);  
    c = init(M, P);  
  
    multiply(a, b, c);  
}  
```  
  
## Vea también  
 [\_\_declspec](../cpp/declspec.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)