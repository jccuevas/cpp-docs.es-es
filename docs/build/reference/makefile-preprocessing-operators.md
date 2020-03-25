---
title: Operadores de preprocesamiento de archivos MAKE
ms.date: 06/14/2018
helpviewer_keywords:
- operators [C++], makefile preprocessing
- EXIST operator
- preprocessing NMAKE makefile operators
- NMAKE program, operators
- DEFINED operator
- makefiles, preprocessing operators
ms.assetid: a46e4d39-afdb-43c1-ac3b-025d33e6ebdb
ms.openlocfilehash: 2276f6a3c28c6f2fac509ef0e4bc14cce9932582
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170468"
---
# <a name="makefile-preprocessing-operators"></a>Operadores de preprocesamiento de archivos MAKE

Las expresiones de preprocesamiento de archivos Make pueden usar operadores que actúan sobre valores constantes, códigos de salida de comandos, cadenas, macros y rutas de acceso del sistema de archivos. Para evaluar la expresión, el preprocesador expande primero las macros, luego ejecuta los comandos y, después, realiza las operaciones. Las operaciones se evalúan en el orden de agrupación explícita entre paréntesis y, luego, en el orden de precedencia de los operadores. El resultado es un valor constante.

El operador **definido** es un operador lógico que actúa sobre un nombre de macro. La expresión **definida (** _nombremacro_ **)** es true si se define *nombremacro* , aunque no tenga un valor asignado. **Definido** en combinación con **! Si** o **.** De lo contrario, si es equivalente a **! IFDEF** o **!** en caso contrario, ifdef. Sin embargo, a diferencia de estas directivas, se pueden usar **definidas** en expresiones complejas.

El operador **exist** es un operador lógico que actúa en una ruta de acceso del sistema de archivos. **Exist (** _path_ **)** es true si la *ruta de acceso* existe. El resultado de **exist** se puede usar en expresiones binarias. Si *path* contiene espacios, escríbalo entre comillas dobles.

Para comparar dos cadenas, utilice el operador de igualdad ( **==** ) o el operador de desigualdad ( **! =** ). Escriba las cadenas entre comillas dobles.

Las constantes de tipo entero pueden usar los operadores unarios para la negación numérica ( **-** ), el complemento de uno ( **~** ) y la negación lógica ( **!** ).

Las expresiones pueden usar los siguientes operadores. Agrupamos los operadores que tienen la misma precedencia, y estos grupos se muestran en orden de mayor a menor precedencia. Los operadores unarios se asocian con el operando de la derecha. Los operadores binarios que tienen la misma precedencia asocian los operandos de izquierda a derecha.

|Operator|Descripción|
|--------------|-----------------|
|**Definido (** *nombremacro* **)**|Genera un valor lógico para el estado de definición actual de *nombremacro*.|
|**Exist (** *ruta de acceso* **)**|Genera un valor lógico para la existencia de un archivo en la *ruta de acceso*.|
|||
|**!**|NOT lógico unario.|
|**~**|Complemento de uno unario.|
|**-**|Negación unaria.|
|||
|**&#42;**|Multiplicación.|
|**/**|División.|
|**%**|Módulo (resto).|
|||
|**+**|Suma.|
|**-**|Resta.|
|||
|**\<\<**|Desplazamiento bit a bit a la izquierda.|
|**>>**|Desplazamiento bit a bit a la derecha.|
|||
|**\<=**|Menor o igual que.|
|**>=**|Mayor o igual que.|
|**\<**|Menor que.|
|**>**|Mayor que.|
|||
|**==**|Igualdad.|
|**!=**|Desigualdad.|
|||
|**&**|AND bit a bit.|
|**^**|XOR bit a bit.|
|**&#124;**|OR bit a bit.|
|||
|**&&**|Y lógico.|
|||
|**&#124;&#124;**|O lógico.|

> [!NOTE]
> El operador XOR bit a bit ( **^** ) es el mismo que el carácter de escape y debe ser un carácter de escape (como **^^** ) cuando se usa en una expresión.

## <a name="see-also"></a>Consulte también

- [Expresiones de preprocesamiento de archivos MAKE](expressions-in-makefile-preprocessing.md)
