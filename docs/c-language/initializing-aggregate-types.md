---
title: Inicializar tipos de agregado | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- aggregate types [C++]
- union keyword [C], declarations
- types [C], initializing
- union keyword [C]
- aggregates [C++], initializing
ms.assetid: a8f8ed75-39db-4592-93b9-d3920d915810
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8656d1c9f5f08e8736ee83705ea2daf9031c2446
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="initializing-aggregate-types"></a>Inicializar tipos de agregado
Un tipo “agregado” es una estructura, una unión o un tipo de matriz. Si un tipo agregado contiene miembros de tipos agregados, las reglas de inicialización se aplican de forma recursiva.  
  
## <a name="syntax"></a>Sintaxis  
 *initializer*:  
 **{**  *initializer-list*  **}** /* Para la inicialización de agregados \*/  
  
 **{**  *initializer-list*  **, }**  
  
 *initializer-list*:  
 *initializer*  
  
 *initializer-list*  **,**  *initializer*  
  
 El elemento *initializer-list* es una lista de inicializadores separados por comas. Cada inicializador de la lista es una expresión constante o una lista de inicializadores. Por consiguiente, las listas de inicializadores pueden anidarse. Este formulario es útil para inicializar miembros agregados de un tipo agregado, como se muestra en los ejemplos de esta sección. Sin embargo, si el inicializador de un identificador automático es una expresión única, no es necesario que sea una expresión constante; solo necesita tener el tipo apropiado para la asignación al identificador.  
  
 Para cada lista de inicializadores, los valores de las expresiones constantes se asignan, en orden, a los miembros correspondientes de la variable agregada.  
  
 Si *initializer-list* tiene menos valores que un tipo agregado, los miembros o los elementos restantes del tipo agregado se inicializan en 0. El valor inicial de un identificador automático no inicializado explícitamente es indefinido. Si *initializer-list* tiene más valores que un tipo agregado, se produce un error. Estas reglas se aplican a cada lista de inicializadores incrustada, así como al agregado en conjunto.  
  
 El inicializador de una estructura es una expresión del mismo tipo o una lista de inicializadores para sus miembros delimitada por llaves (**{ }**). Los miembros de campo de bits sin nombre no se inicializan.  
  
 Cuando se inicializa una unión, *initializer-list* debe ser una expresión constante. El valor de la expresión constante se asigna al primer miembro de la unión.  
  
 Si una matriz tiene un tamaño desconocido, el número de inicializadores determina el tamaño de la matriz y su tipo se completa. No hay ninguna forma de especificar la repetición de un inicializador en C o de inicializar un elemento en medio de una matriz sin proporcionar también todos los valores anteriores. Si necesita esta operación en el programa, escriba la rutina en lenguaje de ensamblado.  
  
 Observe que el número de inicializadores puede establecer el tamaño de la matriz:  
  
```  
int x[ ] = { 0, 1, 2 }  
```  
  
 Si se especifica el tamaño y proporciona un número incorrecto de inicializadores, sin embargo, el compilador genera un error.  
  
 **Específicos de Microsoft**  
  
 El tamaño máximo para una matriz se define mediante **size_t**. Definido en el archivo de encabezado STDDEF.H, **size_t** es un `unsigned int` con el intervalo de 0x00000000 a 0x7CFFFFFF.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="examples"></a>Ejemplos  
 Este ejemplo muestra inicializadores para una matriz.  
  
```  
int P[4][3] =   
{  
    { 1, 1, 1 },  
    { 2, 2, 2 },  
    { 3, 3, 3,},  
    { 4, 4, 4,},  
};  
```  
  
 Esta instrucción declara `P` como una matriz de cuatro por tres e inicializa los elementos de la primera fila en 1, los elementos de la segunda fila en 2, etc. hasta la cuarta fila. Observe que la lista de inicializadores para la tercera y la cuarta filas contiene comas después de la última expresión constante. La última lista de inicializadores (`{4, 4, 4,},`) también va seguida por una coma. Estas comas adicionales se permiten pero no se requieren; solo se requieren las comas que separan expresiones constantes entre sí y las que separan una lista de inicializadores de otra.  
  
 Si un miembro agregado no tiene ninguna lista de inicializadores incrustada, los valores simplemente se asignan, en orden, a cada miembro del subagregado. Por consiguiente, la inicialización del ejemplo anterior es equivalente a la siguiente:  
  
```  
int P[4][3] =   
{  
   1, 1, 1, 2, 2, 2, 3, 3, 3, 4, 4, 4  
};  
```  
  
 También pueden aparecer llaves alrededor de inicializadores individuales de la lista, que ayudarían a clarificar el ejemplo anterior.  
  
 Cuando se inicializa una variable global, debe tener cuidado de utilizar correctamente las llaves y las listas de inicializadores. El ejemplo siguiente muestra con más detalle la interpretación de las llaves por el compilador:  
  
```  
typedef struct   
{  
    int n1, n2, n3;  
} triplet;  
  
triplet nlist[2][3] =   
{  
    { {  1, 2, 3 }, {  4, 5, 6 }, {  7, 8, 9 } },  /* Row 1 */  
    { { 10,11,12 }, { 13,14,15 }, { 16,17,18 } }   /* Row 2 */  
};  
```  
  
 En este ejemplo, se declara `nlist` como una matriz de 2 por 3 estructuras, cada una de las cuales tiene tres miembros. La fila 1 de la inicialización asigna valores a la primera fila de `nlist`, de la manera siguiente:  
  
1.  La primera llave de apertura de la fila 1 indica al compilador que está comenzando la inicialización del primer miembro agregado de `nlist` (es decir, `nlist[0]`).  
  
2.  La segunda llave de apertura indica que está comenzando la inicialización del primer miembro agregado de `nlist[0]` (es decir, la estructura de `nlist[0][0]`).  
  
3.  La primera llave de cierre finaliza la inicialización de la estructura `nlist[0][0]`; la llave de apertura siguiente comienza la inicialización de `nlist[0][1]`.  
  
4.  El proceso continúa hasta el final de la línea, donde la llave de cierre de la derecha finaliza la inicialización de `nlist[0]`.  
  
 La fila 2 asigna valores a la segunda fila de `nlist` de una manera similar. Observe que se requieren conjuntos externos de llaves que delimiten los inicializadores de las filas 1 y 2. La construcción siguiente, que omite las llaves externas, provocaría un error:  
  
```  
triplet nlist[2][3] =  /* THIS CAUSES AN ERROR */  
{  
     {  1, 2, 3 },{  4, 5, 6 },{  7, 8, 9 },   /* Line 1 */  
     { 10,11,12 },{ 13,14,15 },{ 16,17,18 }    /* Line 2 */  
};  
```  
  
 En esta construcción, la primera llave de apertura de la línea 1 comienza la inicialización de `nlist[0]`, que es una matriz de tres estructuras. Los valores 1, 2 y 3 se asignan a los tres miembros de la primera estructura. Cuando se encuentra la siguiente llave de cierre (después del valor 3), la inicialización de `nlist[0]` se completa y las dos estructuras restantes de la matriz de tres estructuras se inicializan automáticamente en 0. De igual forma, `{ 4,5,6 }` inicializa la primera estructura de la segunda fila de `nlist`. Las dos estructuras restantes de `nlist[1]` se establecen en 0. Cuando el compilador encuentra la siguiente lista de inicializadores ( `{ 7,8,9 }` ), intenta inicializar `nlist[2]`. Puesto que `nlist` solo tiene dos filas, este intento provoca un error.  
  
 En este ejemplo siguiente, los tres miembros `int` de `x` se inicializan en 1, 2 y 3, respectivamente.  
  
```  
struct list   
{  
    int i, j, k;  
    float m[2][3];  
} x = {  
        1,  
        2,  
        3,  
       {4.0, 4.0, 4.0}  
      };  
```  
  
 En la estructura `list` anterior, los tres elementos de la primera fila de `m` se inicializan en 4,0; los elementos de la fila restante de `m` se inicializan en 0,0 de forma predeterminada.  
  
```  
union  
{  
    char x[2][3];  
    int i, j, k;  
} y = { {  
            {'1'},  
            {'4'}   
        }  
      };  
```  
  
 La variable de unión `y`, en este ejemplo, se inicializa. El primer elemento de la unión es una matriz, por lo que el inicializador es un inicializador agregado. La lista de inicializadores `{'1'}` asigna valores a la primera fila de la matriz. Dado que solo aparece un valor en la lista, el elemento de la primera columna se inicializa en el carácter `1` y los restantes dos elementos de la fila se inicializan en el valor 0 de forma predeterminada. De igual forma, el primer elemento de la segunda fila de `x` se inicializa en el carácter `4` y los dos elementos restantes de la fila se inicializan en el valor 0.  
  
## <a name="see-also"></a>Vea también  
 [Inicialización](../c-language/initialization.md)