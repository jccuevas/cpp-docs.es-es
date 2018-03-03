---
title: Operadores de preprocesamiento de archivos MAKE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], makefile preprocessing
- EXIST operator
- preprocessing NMAKE makefile operators
- NMAKE program, operators
- DEFINED operator
- makefiles, preprocessing operators
ms.assetid: a46e4d39-afdb-43c1-ac3b-025d33e6ebdb
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 59007bdabc81b5fe49aa4b5265dc0fc73ef4f0b3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="makefile-preprocessing-operators"></a>Operadores de preprocesamiento de archivos MAKE
Las expresiones de preprocesamiento de archivos Make pueden usar operadores que actúan sobre valores constantes, códigos de salida de comandos, cadenas, macros y rutas de acceso del sistema de archivos. Para evaluar la expresión, el preprocesador expande primero las macros, luego ejecuta los comandos y, después, realiza las operaciones. Las operaciones se evalúan en el orden de agrupación explícita entre paréntesis y, luego, en el orden de precedencia de los operadores. El resultado es un valor constante.  
  
 El operador `DEFINED` es un operador lógico que actúa sobre el nombre de una macro. La expresión `DEFINED(` *Nombredelamacro* `)` es true si *Nombredelamacro* se define, incluso si no tiene un valor asignado. `DEFINED` combinado con `!IF` o `!ELSE IF` equivale a `!IFDEF` o a `!ELSE IFDEF`. Sin embargo, a diferencia de estas directivas, `DEFINED` se puede usar en expresiones complejas.  
  
 El operador `EXIST` es un operador lógico que actúa sobre una ruta de acceso del sistema de archivos. `EXIST(`*ruta de acceso* `)` es true si *ruta de acceso* existe. El resultado de `EXIST` se puede usar en expresiones binarias. Si *ruta de acceso* contiene espacios, escríbalo entre comillas dobles.  
  
 Para comparar dos cadenas, utilice el operador de igualdad (`==`) o el de desigualdad (`!=`). Escriba las cadenas entre comillas dobles.  
  
 Las constantes de tipo entero pueden usar los operadores unarios para la negación numérica (`-`), el complemento de uno (`~`) y la negación lógica (`!`).  
  
 Las expresiones pueden usar los siguientes operadores. Agrupamos los operadores que tienen la misma precedencia, y estos grupos se muestran en orden de mayor a menor precedencia. Los operadores unarios se asocian con el operando de la derecha. Los operadores binarios que tienen la misma precedencia asocian los operandos de izquierda a derecha.  
  
|Operador|Descripción|  
|--------------|-----------------|  
|`DEFINED(`*Nombredelamacro*`)`|Genera un valor lógico para el estado actual de la definición de *Nombredelamacro*.|  
|`EXIST(`*ruta de acceso*`)`|Genera un valor lógico de la existencia de un archivo en *ruta de acceso*.|  
|||  
|`!`|NOT lógico unario.|  
|`~`|Complemento de uno unario.|  
|`-`|Negación unaria.|  
|||  
|`*`|Multiplicación.|  
|`/`|División.|  
|`%`|Módulo (resto).|  
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
>  El operador XOR bit a bit (`^`) es el mismo que el carácter de escape y se debe escapar (como `^^`) cuando se use en una expresión.  
  
## <a name="see-also"></a>Vea también  
 [Expresiones de preprocesamiento de archivos MAKE](../build/expressions-in-makefile-preprocessing.md)