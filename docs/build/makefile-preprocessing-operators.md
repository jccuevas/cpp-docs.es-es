---
title: "Operadores de preprocesamiento de archivos MAKE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DEFINED (operador)"
  - "EXIST (operador)"
  - "Make (archivos), preprocesar operadores"
  - "NMAKE (programa), operadores"
  - "operadores [C++], preprocesamiento de archivos make"
  - "operadores de preprocesamiento de archivos make de NMAKE"
ms.assetid: a46e4d39-afdb-43c1-ac3b-025d33e6ebdb
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Operadores de preprocesamiento de archivos MAKE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las expresiones de preprocesamiento de archivos Make pueden usar operadores que actúan sobre valores constantes, códigos de salida de comandos, cadenas, macros y rutas de acceso del sistema de archivos.  Para evaluar la expresión, el preprocesador expande primero las macros, luego ejecuta los comandos y, después, realiza las operaciones.  Las operaciones se evalúan en el orden de agrupación explícita entre paréntesis y, luego, en el orden de precedencia de los operadores.  El resultado es un valor constante.  
  
 El operador `DEFINED` es un operador lógico que actúa sobre el nombre de una macro.  La expresión `DEFINED(`*nombreDeLaMacro*`)` es verdadera si se definió *nombreDeLaMacro*, aunque no tenga ningún valor asignado.  `DEFINED` combinado con `!IF` o `!ELSE IF` equivale a `!IFDEF` o a `!ELSE IFDEF`.  Sin embargo, a diferencia de estas directivas, `DEFINED` se puede usar en expresiones complejas.  
  
 El operador `EXIST` es un operador lógico que actúa sobre una ruta de acceso del sistema de archivos.  `EXIST(`*rutaDeAcceso*`)` es verdadero si *rutaDeAcceso* existe.  El resultado de `EXIST` se puede usar en expresiones binarias.  Si *rutaDeAcceso* contiene espacios, escríbalo entre comillas dobles.  
  
 Para comparar dos cadenas, utilice el operador de igualdad \(`==`\) o el de desigualdad \(`!=`\).  Escriba las cadenas entre comillas dobles.  
  
 Las constantes de tipo entero pueden usar los operadores unarios para la negación numérica \(`–`\), el complemento de uno \(`~`\) y la negación lógica \(`!`\).  
  
 Las expresiones pueden usar los siguientes operadores.  Agrupamos los operadores que tienen la misma precedencia, y estos grupos se muestran en orden de mayor a menor precedencia.  Los operadores unarios se asocian con el operando de la derecha.  Los operadores binarios que tienen la misma precedencia asocian los operandos de izquierda a derecha.  
  
|Operador|Descripción|  
|--------------|-----------------|  
|`DEFINED(` *nombreDeLaMacro* `)`|Produce un valor lógico del estado de definición actual de *nombreDeLaMacro*.|  
|`EXIST(` *rutaDeAcceso* `)`|Produce un valor lógico de la existencia de un archivo en *rutaDeAcceso*.|  
|||  
|`!`|NOT lógico unario.|  
|`~`|Complemento de uno unario.|  
|`-`|Negación unaria.|  
|||  
|`*`|Multiplicación.|  
|`/`|División.|  
|`%`|Módulo \(resto\).|  
|||  
|`+`|Adición.|  
|`-`|Resta.|  
|||  
|`<<`|Desplazamiento bit a bit a la izquierda.|  
|`>>`|Desplazamiento bit a bit a la derecha.|  
|||  
|`<=`|Menor o igual que.|  
|`>=`|Mayor o igual que.|  
|`<`|Menor que.|  
|`>`|Mayor que.|  
|||  
|`==`|Igualdad.|  
|`!=`|Desigualdad.|  
|||  
|`&`|AND bit a bit.|  
|`^`|XOR bit a bit.|  
|`&#124;`|OR bit a bit.|  
|||  
|`&&`|AND lógico.|  
|||  
|`&#124;&#124;`|OR lógico.|  
  
> [!NOTE]
>  El operador XOR bit a bit \(`^`\) es el mismo que el carácter de escape y se debe escapar \(como `^^`\) cuando se use en una expresión.  
  
## Vea también  
 [Expresiones de preprocesamiento de archivos MAKE](../build/expressions-in-makefile-preprocessing.md)