---
title: extern (Especificador de clase de almacenamiento) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- extern keyword [C]
- storage class specifiers, extern
- extern keyword [C], storage class specifier
- external linkage, storage-class specifiers
- external linkage, extern modifier
ms.assetid: 6e16d927-291f-49e4-986c-9d91a482a441
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 448a659afaf7a0251d500da3d9878d30550b9180
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="extern-storage-class-specifier"></a>extern (Especificador de clase de almacenamiento)
Una variable declarada con el especificador de clase de almacenamiento `extern` es una referencia a una variable con el mismo nombre definido en el nivel externo en cualquiera de los archivos de código fuente del programa. La declaración interna `extern` se utiliza para hacer que la definición de variable de nivel externo esté visible en el bloque. A menos que se declare de otra manera en el nivel externo, una variable declarada con la palabra clave `extern` solo está visible en el bloque en el que se declara.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestran declaraciones de nivel interno y externo:  
  
```  
// extern_StorageClassSpecified.c  
#include <stdio.h>  
  
void other( void );  
  
int main()  
{  
    // Reference to i, defined below:   
    extern int i;  
  
    // Initial value is zero; a is visible only within main:   
    static int a;  
  
    // b is stored in a register, if possible:   
    register int b = 0;  
  
    // Default storage class is auto:   
    int c = 0;  
  
    // Values printed are 1, 0, 0, 0:   
    printf_s( "%d\n%d\n%d\n%d\n", i, a, b, c );  
    other();  
    return;  
}  
  
int i = 1;  
  
void other( void )  
{  
    // Address of global i assigned to pointer variable:  
    static int *external_i = &i;  
  
    // i is redefined; global i no longer visible:   
    int i = 16;  
  
    // This a is visible only within the other function:   
    static int a = 2;  
  
    a += 2;  
    // Values printed are 16, 4, and 1:  
    printf_s( "%d\n%d\n%d\n", i, a, *external_i );  
}  
```  
  
 En este ejemplo, la variable `i` se define en el nivel externo con el valor inicial 1. Una declaración `extern` en la función `main` se utiliza para declarar una referencia a la variable `i` de nivel externo. La variable **static** `a` se inicializa en 0 de forma predeterminada, ya que se omite el inicializador. La llamada a `printf` imprime los valores 1, 0, 0 y 0.  
  
 En la función `other`, la dirección de la variable global `i` se usa para inicializar la variable de puntero **static** `external_i`. Esto funciona porque la variable global tiene una duración **static**, lo que significa que la dirección no cambia durante la ejecución del programa. A continuación, la variable `i` se vuelve a definir como una variable local con el valor inicial 16. Esta redefinición no afecta al valor de `i` de nivel externo, que está oculto por el uso de su nombre para la variable local. Al valor de la variable `i` ahora solo se puede acceder de forma indirecta dentro de este bloque, a través del puntero `external_i`. El intento de asignar la dirección de la variable **auto** `i` a un puntero no funciona, ya que puede ser diferente cada vez que se accede al bloque. La variable `a` se declara como una variable **static** y se inicializa en 2. Esta variable `a` no entra en conflicto con `a` en `main`, ya que las variables **static** de nivel interno solo son visibles dentro del bloque en el que se declaran.  
  
 La variable `a` se incrementa en 2, lo que da como resultado 4. Si se llamara de nuevo a la función `other` en el mismo programa, el valor inicial de `a` sería 4. Las variables **static** internas conservan sus valores cuando el programa termina y vuelve a entrar en el bloque en el que se declaran.  
  
## <a name="see-also"></a>Vea también  
 [Especificadores de clase de almacenamiento para las declaraciones de nivel interno](../c-language/storage-class-specifiers-for-internal-level-declarations.md)