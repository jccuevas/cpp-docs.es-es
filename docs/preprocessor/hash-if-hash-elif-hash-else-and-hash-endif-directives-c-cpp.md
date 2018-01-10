---
title: '#<a name="if-elif-else-and-endif-directives-cc--microsoft-docs"></a>if, #elif, #else y #endif directivas (C/C ++) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- '#else'
- '#endif'
- '#if'
- '#elif'
- defined
- __has_include
dev_langs: C++
helpviewer_keywords:
- '#elif directive'
- conditional compilation, directives
- endif directive (#endif)
- preprocessor, directives
- '#else directive'
- '#endif directive'
- if directive (#if)
- else directive (#else)
- '#if directive'
- elif directive (#elif)
- defined directive
ms.assetid: c77a175f-6ca8-47d4-8df9-7bac5943d01b
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8acd8444295175e6aa9fe329e7851456fcd5f7c4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="if-elif-else-and-endif-directives-cc"></a>#if, #elif, #else, and #endif (Directivas) (C/C++)
La directiva `#if`, con las directivas `#elif`, `#else` y `#endif`, controla la compilación de partes de un archivo de código fuente. Si la expresión que se escribe (después de `#if`) tiene un valor distinto de cero, el grupo de líneas inmediatamente después de la directiva `#if` se conserva en la unidad de traducción.  
  
## <a name="grammar"></a>Gramática  
 *condicional* :  
 *partes de elif parte si*opt*parte else*opt*endif línea*  
  
 *parte de si* :  
 *texto de la línea de If*  
  
 *línea de IF* :  
 **#if***expresión constante*   
  
 **#ifdef***identificador*   
  
 **#ifndef***identificador*   
  
 *elif partes* :  
 *texto de la línea de elif*  
  
 *texto de línea elif elif partes*  
  
 *elif línea* :  
 **#elif***expresión constante*   
  
 *parte Else* :  
 *texto de línea Else*  
  
 *línea Else* :  
 `#else`  
  
 *endif línea* :  
 `#endif`  
  
 Cada directiva `#if` de un archivo de código fuente debe coincidir con una directiva `#endif` de cierre. Puede aparecer cualquier número de directivas `#elif` entre las directivas `#if` y `#endif`, pero como máximo se permite una directiva `#else`. La directiva `#else`, si está presente, debe ser la última directiva antes de `#endif`.  
  
 Las directivas `#if`, `#elif`, `#else` y `#endif` pueden anidarse en partes de texto de otras directivas `#if`. Cada directiva `#else`, `#elif` o `#endif` anidada pertenece a la directiva `#if` anterior más cercana.  
  
 Todas las directivas de compilación condicional, como `#if` y **#ifdef**, deben coincidir con cierre `#endif` directivas antes del final del archivo; en caso contrario, se genera un mensaje de error. Cuando las directivas de compilación condicional están contenidas en archivos de inclusión, deben cumplir las mismas condiciones: no debe haber directivas de compilación condicional sin coincidencia al final del archivo de inclusión.  
  
 Reemplazo de macros se realiza dentro de la parte de la línea de comandos que sigue a un `#elif` comando, por lo que puede usar una llamada de macro en el *expresión constante*.  
  
 El preprocesador selecciona una de las apariciones dadas de *texto* para su posterior procesamiento. Un bloque especificado en *texto* puede ser cualquier secuencia de texto. Puede ocupar más de una línea. Normalmente *texto* es el texto de programa que tiene un significado para el compilador o el preprocesador.  
  
 El preprocesador procesa seleccionado *texto* y lo pasa al compilador. Si *texto* contiene directivas de preprocesador, el preprocesador ejecuta esas directivas. Solo se compilan los bloques de texto seleccionados por el preprocesador.  
  
 El preprocesador selecciona una sola *texto* elemento mediante la evaluación de la expresión constante que sigue a cada `#if` o `#elif` directiva hasta que encuentra una expresión de constante true (distinto de cero). Selecciona todo el texto (incluidas otras directivas de preprocesador que comiencen con  **#** ) hasta su asociado `#elif`, `#else`, o `#endif`.  
  
 Si todas las apariciones de *expresión constante* son false, o si no hay ningún `#elif` aparecen directivas, el preprocesador selecciona el bloque de texto después de la `#else` cláusula. Si el `#else` se omite la cláusula y todas las instancias de *expresión constante* en el `#if` bloque son false, no se selecciona ningún bloque de texto.  
  
 El *expresión constante* es una expresión constante entera con estas restricciones adicionales:  
  
-   Las expresiones deben tener tipo entero y puede incluir solo constantes enteras, constantes de caracteres y el **definido** operador.  
  
-   La expresión no puede utilizar `sizeof` o un operador de conversión de tipo.  
  
-   Es posible que el entorno de destino no pueda representar todos los intervalos de enteros.  
  
-   La traducción representa el tipo `int` igual tipo **largo**, y `unsigned int` igual a `unsigned long`.  
  
-   El traductor puede traducir constantes de caracteres a un conjunto de valores de código diferentes del conjunto para el entorno de destino. Para determinar las propiedades del entorno de destino, compruebe los valores de las macros de LIMITS.H en una aplicación compilada para el entorno de destino.  
  
-   La expresión no debe realizar ninguna consulta de ambiente y debe permanecer aislada de los detalles de implementación del equipo de destino.  

## <a name="defined"></a>definición  
 El operador de preprocesador **definido** puede usarse en expresiones constantes especiales, como se muestra en la siguiente sintaxis:  
  
 defined( `identifier` )  
  
 defined `identifier`  
  
 Esta expresión constante se considera true (distinto de cero) si el *identificador* está definido actualmente; en caso contrario, la condición es false (0). Un identificador definido como texto vacío se considera definido. El **definido** directiva puede utilizarse en una `#if` y un `#elif` directiva, pero ningún otro lugar.  
  
 En el ejemplo siguiente, las directivas `#if` y `#endif` controlan la compilación de una de las tres llamadas de función:  
  
```  
#if defined(CREDIT)  
    credit();  
#elif defined(DEBIT)  
    debit();  
#else  
    printerror();  
#endif  
```  
  
 La llamada de función a `credit` se compila si el identificador `CREDIT` está definido. Si el identificador `DEBIT` está definido, se compila la llamada de función a `debit`. Si no está definido ninguno de los identificadores, se compila la llamada a `printerror`. Observe que `CREDIT` y `credit` son identificadores distintos en C y C++ por la distinción entre mayúsculas y minúsculas de ambos.  
  
 Las instrucciones de compilación condicional del ejemplo siguiente suponen una constante simbólica previamente definida denominada `DLEVEL`.  
  
```  
#if DLEVEL > 5  
    #define SIGNAL  1  
    #if STACKUSE == 1  
        #define STACK   200  
    #else  
        #define STACK   100  
    #endif  
#else  
    #define SIGNAL  0  
    #if STACKUSE == 1  
        #define STACK   100  
    #else  
        #define STACK   50  
    #endif  
#endif  
#if DLEVEL == 0  
    #define STACK 0  
#elif DLEVEL == 1  
    #define STACK 100  
#elif DLEVEL > 5  
    display( debugptr );  
#else  
    #define STACK 200  
#endif  
```  
  
 El primer bloque `#if` muestra dos conjuntos de directivas `#if`, `#else` y `#endif` anidadas. El primer conjunto de directivas se procesa solo si `DLEVEL > 5` es true. De lo contrario, las instrucciones después de #**else** se procesan.  
  
 Las directivas `#elif` y `#else` del segundo ejemplo se utilizan para elegir entre cuatro opciones, según el valor de `DLEVEL`. La constante `STACK` se establece en 0, 100 o 200, según de la definición de `DLEVEL`. Si `DLEVEL` es mayor que 5, la instrucción  
  
```  
#elif DLEVEL > 5  
display(debugptr);  
```  
  
 se compila y `STACK` no está definido.  
  
 Un uso común para la compilación condicional es evitar inclusiones múltiples del mismo archivo de encabezado. En C++, donde las clases suelen definirse en archivos de encabezado, se pueden utilizar construcciones como la siguiente para evitar varias definiciones:  
  
```  
/*  EXAMPLE.H - Example header file  */  
#if !defined( EXAMPLE_H )  
#define EXAMPLE_H  
  
class Example  
{  
...  
};  
  
#endif // !defined( EXAMPLE_H )  
```  
  
 El código anterior realiza comprobaciones para ver si se define la constante simbólica `EXAMPLE_H`. Si es así el archivo se ha incluido y no necesita ya volver a procesarse. Si no, se define la constante `EXAMPLE_H` para marcar EXAMPLE.H como ya procesado.  

## <a name="hasinclude"></a>__has_include
**Visual Studio 2017 15,3 y versiones posteriores**: determina si un encabezado de la biblioteca está disponible para su inclusión:  

```cpp
#ifdef __has_include
#  if __has_include(<filesystem>)
#    include <filesystem>
#    define have_filesystem 1
#  elif __has_include(<experimental/filesystem>)
#    include <experimental/filesystem>
#    define have_filesystem 1
#    define experimental_filesystem
#  else
#    define have_filesystem 0
#  endif
#endif
```
  
## <a name="see-also"></a>Vea también  
 [Directivas de preprocesador](../preprocessor/preprocessor-directives.md)