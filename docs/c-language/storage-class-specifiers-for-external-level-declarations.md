---
title: Especificadores de clase de almacenamiento para las declaraciones de nivel externo | Microsoft Docs
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
- external definitions
- linkage [C++], external
- external linkage, variable declarations
- declaring variables, external variables
- declarations [C++], external
- declarations [C++], specifiers
- external declarations
- static variables, external declarations
- variables, visibility
- external linkage, storage-class specifiers
- referencing declarations
- visibility, variables
- static storage class specifiers
ms.assetid: b76b623a-80ec-4d5d-859b-6cef422657ee
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3764eb29cc46ec7b6159456131dde1024b187f61
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="storage-class-specifiers-for-external-level-declarations"></a>Especificadores de clase de almacenamiento para las declaraciones de nivel externo
Las variables externas son variables en el ámbito de archivo. Se definen fuera de cualquier función y pueden estar disponibles para muchas funciones. Las funciones solo se pueden definir en el nivel externo y, por consiguiente, no pueden anidarse. De forma predeterminada, todas las referencias a variables y funciones externas del mismo nombre son referencias al mismo objeto, lo que significa que tienen “vinculación externa”. (Puede utilizar la palabra clave **static** para invalidar esto. Vea la información que aparece más adelante en esta sección para conocer más detalles sobre **static**).  
  
 Las declaraciones de variable en el nivel de externo son definiciones de variables (“declaraciones de definición”) o referencias a variables definidas en otro lugar (“declaraciones de referencia”).  
  
 Una declaración de variable externa que también inicializa la variable (implícita o explícitamente) es una declaración de definición de variable. Una definición en el nivel externo puede adoptar varias formas:  
  
-   Una variable declarada con el especificador de clase de almacenamiento **static**. Puede inicializar explícitamente la variable **static** con una expresión constante, como se describe en [Inicialización](../c-language/initialization.md). Si omite el inicializador, la variable se inicializa en 0 de forma predeterminada. Por ejemplo, estas dos instrucciones se consideran definiciones de la variable `k`.  
  
    ```  
    static int k = 16;  
    static int k;  
    ```  
  
-   Una variable que se inicializa explícitamente en el nivel externo. Por ejemplo, `int j = 3;` es una definición de la variable `j`.  
  
 En las declaraciones de variable de nivel externo (es decir, fuera de todas las funciones), puede utilizar el especificador de clase de almacenamiento **static** o `extern` u omitir el especificador de clase de almacenamiento completamente. No puede utilizar los terminales **auto** y **register** *storage-class-specifier* en el nivel externo.  
  
 Una vez que se define una variable en el nivel externo, es visible en el resto de la unidad de traducción. La variable no es visible antes de su declaración en el mismo archivo de código fuente. Además, no es visible en otros archivos de código fuente del programa, a menos que una declaración de referencia la haga visible, como se describe a continuación.  
  
 Las reglas relativas a **static** incluyen:  
  
-   Las variables declaradas fuera de todos los bloques sin la palabra clave **static** conservan siempre sus valores en el programa. Para restringir el acceso a una unidad de traducción determinada, debe utilizar la palabra clave **static**. Esto le otorga “vinculación interna”. Para hacerlas globales para todo un programa, omita la clase de almacenamiento explícita o use la palabra clave `extern` (vea las reglas en la lista siguiente). Esto le otorga “vinculación externa”. La vinculación interna y externa también se explican en [Vinculación](../c-language/linkage.md).  
  
-   Puede definir una variable en el nivel externo una única vez dentro de un programa. Puede definir otra variable con el mismo nombre y el especificador de clase de almacenamiento **static** en una unidad de traducción diferente. Puesto que cada definición **static** solo es visible dentro de su propia unidad de traducción, no se produce ningún conflicto. Esto proporciona una manera útil de ocultar nombres de identificación que se deban compartir entre funciones de una única unidad de traducción, pero que no deban ser visibles para otras unidades de traducción.  
  
-   El especificador de clase de almacenamiento **static** se puede aplicar también a funciones. Si se declara una función **static**, su nombre es invisible fuera del archivo en el que se declara.  
  
 Las reglas para usar `extern` son:  
  
-   El especificador de clase de almacenamiento `extern` declara una referencia a una variable definida en otro lugar. Puede usar una declaración `extern` para crear una definición en otro archivo de código fuente visible o para hacer que una variable sea visible antes de su definición en el mismo archivo de código fuente. Una vez que se ha declarado una referencia a la variable en el nivel externo, la variable está visible en el resto de la unidad de traducción en la que aparece la referencia declarada.  
  
-   Para que una referencia `extern` sea válida, la variable a la que hace referencia debe definirse una vez y solo una vez en el nivel externo. Esta definición (sin la clase de almacenamiento `extern`) puede estar en cualquier unidad de traducción de las que componen el programa.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestran declaraciones externas:  
  
```  
/******************************************************************  
                      SOURCE FILE ONE   
*******************************************************************/  
#include <stdio.h>  
  
extern int i;                // Reference to i, defined below   
void next( void );           // Function prototype              
  
int main()  
{  
    i++;  
    printf_s( "%d\n", i );   // i equals 4   
    next();  
}  
  
int i = 3;                  // Definition of i  
  
void next( void )  
{  
    i++;  
    printf_s( "%d\n", i );  // i equals 5  
    other();  
}  
  
/******************************************************************  
                      SOURCE FILE TWO   
*******************************************************************/  
#include <stdio.h>  
  
extern int i;              // Reference to i in   
                           // first source file   
void other( void )  
{  
    i++;  
    printf_s( "%d\n", i ); // i equals 6   
}  
```  
  
 Los dos archivos de código fuente de este ejemplo contienen un total de tres declaraciones externas de `i`. Solo una declaración es una “declaración de definición”. Esa declaración,  
  
```  
int i = 3;  
```  
  
 define la variable global `i` y se inicializa con el valor inicial 3. La declaración de “referencia” de `i` al principio del primer archivo de código fuente que utiliza `extern` hace visible la variable global antes de su declaración de definición en el archivo. La declaración de referencia de `i` en el segundo archivo de código fuente también hace visible la variable en ese archivo de código fuente. Si no se proporciona una instancia de definición para una variable en la unidad de traducción, el compilador supone que hay una  
  
```  
extern int x;  
```  
  
 declaración de referencia y que parece una referencia de definición  
  
```  
int x = 0;  
```  
  
 en otra unidad de traducción del programa.  
  
 Las tres funciones, `main`, `next` y `other`, realizan la misma tarea: incrementan `i` y la imprimen. Se imprimen los valores 4, 5 y 6.  
  
 Si la variable `i` no se hubiera inicializado, se habría establecido en 0 automáticamente. En este caso, se habrían imprimido los valores 1, 2 y 3. Vea [Inicialización](../c-language/initialization.md) para obtener información sobre la inicialización de variables.  
  
## <a name="see-also"></a>Vea también  
 [Clases de almacenamiento de C](../c-language/c-storage-classes.md)