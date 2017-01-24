---
title: "#if, #elif, #else, and #endif (Directivas) (C/C++) | Microsoft Docs"
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
  - "#else"
  - "#endif"
  - "#if"
  - "#elif"
  - "Defined"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#elif (directiva)"
  - "#else (directiva)"
  - "#endif (directiva)"
  - "#if (directiva)"
  - "compilación condicional, directivas"
  - "definición de directiva"
  - "elif (directiva) (#elif)"
  - "else: directiva (#else)"
  - "endif (directiva) (#endif)"
  - "if (directiva) (#if)"
  - "preprocesador, directivas"
ms.assetid: c77a175f-6ca8-47d4-8df9-7bac5943d01b
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #if, #elif, #else, and #endif (Directivas) (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La directiva `#if`, con las directivas `#elif`, `#else` y `#endif`, controla la compilación de partes de un archivo de código fuente.  Si la expresión que se escribe \(después de `#if`\) tiene un valor distinto de cero, el grupo de líneas inmediatamente después de la directiva `#if` se conserva en la unidad de traducción.  
  
## Gramática  
 *conditional* :  
 *if\-part elif\-parts* opt *else\-part*opt *endif\-line*  
  
 *if\-part* :  
 *if\-line text*  
  
 *if\-line* :  
 **\#if**  *constant\-expression*  
  
 **\#ifdef**  *identifier*  
  
 **\#ifndef**  *identifier*  
  
 *elif\-parts* :  
 *elif\-line text*  
  
 *elif\-parts elif\-line text*  
  
 *elif\-line* :  
 **\#elif**  *constant\-expression*  
  
 *else\-part* :  
 *else\-line text*  
  
 *else\-line* :  
 `#else`  
  
 *endif\-line* :  
 `#endif`  
  
 Cada directiva `#if` de un archivo de código fuente debe coincidir con una directiva `#endif` de cierre.  Puede aparecer cualquier número de directivas `#elif` entre las directivas `#if` y `#endif`, pero como máximo se permite una directiva `#else`.  La directiva `#else`, si está presente, debe ser la última directiva antes de `#endif`.  
  
 Las directivas `#if`, `#elif`, `#else` y `#endif` pueden anidarse en partes de texto de otras directivas `#if`.  Cada directiva `#else`, `#elif` o `#endif` anidada pertenece a la directiva `#if` anterior más cercana.  
  
 Todas las directivas de compilación condicional, como `#if` y **\#ifdef**, deben coincidir con directivas `#endif` de cierre antes del fin del archivo; si no, se genera un mensaje de error.  Cuando las directivas de compilación condicional están contenidas en archivos de inclusión, deben cumplir las mismas condiciones: no debe haber directivas de compilación condicional sin coincidencia al final del archivo de inclusión.  
  
 El reemplazo de macros se realiza dentro de la parte de la línea de comandos que sigue a un comando `#elif`, por lo que se puede usar una llamada a una macro en *constant\-expression*.  
  
 El preprocesador selecciona una de las apariciones dadas de *text* para procesamiento adicional.  Un bloque especificado en *text* puede ser cualquier secuencia de texto.  Puede ocupar más de una línea.  Habitualmente, *text* suele ser texto de programa que tiene significado para el compilador o el preprocesador.  
  
 El preprocesador procesa el texto *text* seleccionado y lo pasa al compilador.  Si *text* contiene directivas de preprocesador, el preprocesador ejecuta esas directivas.  Solo se compilan los bloques de texto seleccionados por el preprocesador.  
  
 El preprocesador selecciona un solo elemento *text* mediante la evaluación de la expresión constante que sigue a cada directiva `#if` o `#elif` hasta que encuentra una expresión constante true \(distinta de cero\).  Selecciona todo el texto \(incluidas otras directivas de preprocesador que comiencen por **\#**\) hasta su `#elif`, `#else` o `#endif` asociada.  
  
 Si todas las repeticiones de *constant\-expression* son false o si no aparece ninguna directiva `#elif`, el preprocesador selecciona el bloque de texto después de la cláusula `#else`.  Si se omite la cláusula `#else` y todas las instancias de *constant\-expression* en el bloque `#if` son false, no se selecciona ningún bloque de texto.  
  
 *constant\-expression* es una expresión constante entera con estas restricciones adicionales:  
  
-   Las expresiones deben tener tipo entero y solo pueden incluir constantes de tipo entero, constantes de caracteres y el operador **defined**.  
  
-   La expresión no puede utilizar `sizeof` o un operador de conversión de tipo.  
  
-   Es posible que el entorno de destino no pueda representar todos los intervalos de enteros.  
  
-   La traducción representa el tipo `int` igual que el tipo **long** y `unsigned int` igual que `unsigned long`.  
  
-   El traductor puede traducir constantes de caracteres a un conjunto de valores de código diferentes del conjunto para el entorno de destino.  Para determinar las propiedades del entorno de destino, compruebe los valores de las macros de LIMITS.H en una aplicación compilada para el entorno de destino.  
  
-   La expresión no debe realizar ninguna consulta de ambiente y debe permanecer aislada de los detalles de implementación del equipo de destino.  
  
 El operador de preprocesador **defined** se puede usar en expresiones constantes especiales, como muestra la siguiente sintaxis:  
  
 defined\( `identifier` \)  
  
 defined `identifier`  
  
 Esta expresión constante se considera true \(distinta de cero\) si *identifier* está definido actualmente; en caso contrario, la condición es false \(0\).  Un identificador definido como texto vacío se considera definido.  La directiva **defined** se puede usar en una directiva `#if` y `#elif`, pero en ningún otro lugar.  
  
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
  
 La llamada de función a `credit` se compila si el identificador `CREDIT` está definido.  Si el identificador `DEBIT` está definido, se compila la llamada de función a `debit`.  Si no está definido ninguno de los identificadores, se compila la llamada a `printerror`.  Observe que `CREDIT` y `credit` son identificadores distintos en C y C\+\+ por la distinción entre mayúsculas y minúsculas de ambos.  
  
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
  
 El primer bloque `#if` muestra dos conjuntos de directivas `#if`, `#else` y `#endif` anidadas.  El primer conjunto de directivas se procesa solo si `DLEVEL > 5` es true.  Si no, se procesan las instrucciones después de \#**else**.  
  
 Las directivas `#elif` y `#else` del segundo ejemplo se utilizan para elegir entre cuatro opciones, según el valor de `DLEVEL`.  La constante `STACK` se establece en 0, 100 o 200, según de la definición de `DLEVEL`.  Si `DLEVEL` es mayor que 5, la instrucción  
  
```  
#elif DLEVEL > 5  
display(debugptr);  
```  
  
 se compila y `STACK` no está definido.  
  
 Un uso común para la compilación condicional es evitar inclusiones múltiples del mismo archivo de encabezado.  En C\+\+, donde las clases suelen definirse en archivos de encabezado, se pueden utilizar construcciones como la siguiente para evitar varias definiciones:  
  
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
  
 El código anterior realiza comprobaciones para ver si se define la constante simbólica `EXAMPLE_H`.  Si es así el archivo se ha incluido y no necesita ya volver a procesarse.  Si no, se define la constante `EXAMPLE_H` para marcar EXAMPLE.H como ya procesado.  
  
## Vea también  
 [Directivas de preprocesador](../preprocessor/preprocessor-directives.md)