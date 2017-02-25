---
title: "Prototipos de funci&#243;n | Microsoft Docs"
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
  - "tipos de datos [C], tipos de valores devueltos de las funciones"
  - "prototipos de función"
  - "tipos de valores devueltos de las funciones, prototipos de función"
  - "funciones [C], tipos de valor devueltos"
  - "prototipos [C++], función"
ms.assetid: d152f8e6-971e-432c-93ca-5a91400653c2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Prototipos de funci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una declaración de función precede a la definición de función y especifica el nombre, el tipo devuelto, la clase de almacenamiento y otros atributos de una función.  Para ser un prototipo, la declaración de función también debe establecer tipos e identificadores para los argumentos de la función.  
  
## Sintaxis  
 `declaration`:  
 *declaration\-specifiers attribute\-seq*  opt *init\-declarator\-list* opt**;**  
  
 \/\* *attribute\-seq* opt es específico de Microsoft \*\/  
  
 *declaration\-specifiers*:  
 *storage\-class\-specifier declaration\-specifiers*  opt  
  
 *type\-specifier declaration\-specifiers*  opt  
  
 *type\-qualifier declaration\-specifiers*  opt  
  
 *init\-declarator\-list*:  
 *init\-declarator*  
  
 *init\-declarator\-list*  **,**  *init\-declarator*  
  
 *init\-declarator*:  
 *declarator*  
  
 *declarator \= initializer*  
  
 `declarator`:  
 *pointer*  opt *direct\-declarator*  
  
 *direct\-declarator*: \/\* Un declarador de función \*\/  
 *direct\-declarator*  **\(**  *parameter\-type\-list*  **\)**  \/\* Declarador de estilo nuevo \*\/  
  
 *direct\-declarator*  **\(**  *identifier\-list*  opt **\)** \/\* Declarador de estilo obsoleto \*\/  
  
 El prototipo tiene la misma forma que la definición de función, excepto en que termina con un punto y coma inmediatamente después del paréntesis de cierre y, por consiguiente, no tiene ningún cuerpo.  En cualquier caso, el tipo de valor devuelto debe coincidir con el tipo de valor devuelto especificado en la definición de función.  
  
 Los prototipos de función tienen los siguientes usos importantes:  
  
-   Establecen el tipo de valor devuelto para funciones que devuelven tipos diferentes de `int`.  Aunque las funciones que devuelven valores `int` no requieren prototipos, estos son recomendables.  
  
-   Sin prototipos completos se realizan conversiones estándar, pero no se hace ningún intento de comprobar el tipo o el número de argumentos con el número de parámetros.  
  
-   Los prototipos se utilizan para inicializar punteros a funciones antes de que se definan esas funciones.  
  
-   La lista de parámetros se utiliza para comprobar la correspondencia de los argumentos de la llamada de función con los parámetros de la definición de función.  
  
 El tipo convertido de cada parámetro determina la interpretación de los argumentos que la llamada de función coloca en la pila.  Un error de coincidencia de tipos entre un argumento y un parámetro puede provocar que los argumentos de la pila no se interpreten correctamente.  Por ejemplo, en un equipo de 16 bits, si se pasa un puntero de 16 bits como argumento y, a continuación, se declara como un parámetro **long**, los primeros 32 bits de la pila se interpretan como un parámetro **long**.  Este error crea problemas no solo con el parámetro **long**, sino con cualquier parámetro que lo siga.  Puede detectar errores de este tipo declarando prototipos de función completos para todas las funciones.  
  
 Un prototipo establece los atributos de una función para poder comprobar si en las llamadas a la función que preceden a la definición \(o aparecen en otros archivos de código fuente\) aparecen discordancias entre tipos de argumentos y tipos devueltos.  Por ejemplo, si especifica el especificador de clase de almacenamiento **static** en un prototipo, también debe especificar la clase de almacenamiento **static** en la definición de función.  
  
 Las declaraciones de parámetro completas \(`int a`\) se pueden mezclar con declaradores abstractos \(`int`\) en la misma declaración.  Por ejemplo, la siguiente declaración es válida:  
  
```  
int add( int a, int );  
```  
  
 El prototipo puede incluir tanto el tipo como el identificador de cada expresión que se pasa como argumento.  Sin embargo, tales identificadores solo tienen ámbito hasta el final de la declaración.  El prototipo también puede reflejar el hecho de que el número de argumentos es variable o que no se pasa ningún argumento.  Sin esta lista es posible que las discordancias no se revelen, así que el compilador no puede generar mensajes de diagnóstico relacionados con ellos.  Vea [Argumentos](../c-language/arguments.md) para ver más información sobre la comprobación de tipos.  
  
 El ámbito de prototipo en el compilador de Microsoft C es ahora compatible con ANSI cuando se compila con la opción del compilador \/Za.  Esto significa que, si declara una etiqueta `struct` o **union** dentro de un prototipo, la etiqueta se introduce en ese ámbito en lugar de en el ámbito global.  Por ejemplo, al compilar con \/Za para la compatibilidad con ANSI, nunca se puede llamar a esta función sin obtener un error de coincidencia de tipos:  
  
```  
void func1( struct S * );  
```  
  
 Para corregir el código, definir o declarar `struct` o **union** en el ámbito global antes del prototipo de función:  
  
```  
struct S;  
void func1( struct S * );  
```  
  
 Bajo \/Ze, la etiqueta continúa introduciéndose en el ámbito global.  
  
## Vea también  
 [Funciones](../c-language/functions-c.md)