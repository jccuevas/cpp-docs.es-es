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
ms.openlocfilehash: 4101c2fe30bcba44e9b69ed4d6d022845e6e8904
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57827004"
---
# <a name="makefile-preprocessing-operators"></a>Operadores de preprocesamiento de archivos MAKE

Las expresiones de preprocesamiento de archivos Make pueden usar operadores que actúan sobre valores constantes, códigos de salida de comandos, cadenas, macros y rutas de acceso del sistema de archivos. Para evaluar la expresión, el preprocesador expande primero las macros, luego ejecuta los comandos y, después, realiza las operaciones. Las operaciones se evalúan en el orden de agrupación explícita entre paréntesis y, luego, en el orden de precedencia de los operadores. El resultado es un valor constante.

El **DEFINED** operador es un operador lógico que actúa en nombre de una macro. La expresión **DEFINED (**_Nombredelamacro_**)** es true si *Nombredelamacro* están definidos, incluso si no tiene un valor asignado. **DEFINED** en combinación con **! IF** o **! ELSE IF** es equivalente a **! IFDEF** o **! ELSE IFDEF**. Sin embargo, a diferencia de estas directivas, **DEFINED** se puede usar en expresiones complejas.

El **EXIST** operador es un operador lógico que actúa en una ruta de acceso del sistema de archivos. **EXIST (**_ruta_**)** es true si *ruta* existe. El resultado de **EXIST** se puede usar en expresiones binarias. Si *ruta* contiene espacios, escríbalo entre comillas dobles.

Para comparar dos cadenas, utilice la igualdad (**==**) operador o la desigualdad (**! =**) operador. Escriba las cadenas entre comillas dobles.

Constantes de tipo entero pueden usar los operadores unarios para la negación numérica (**-**), un complemento de (**~**) y la negación lógica (**!**).

Las expresiones pueden usar los siguientes operadores. Agrupamos los operadores que tienen la misma precedencia, y estos grupos se muestran en orden de mayor a menor precedencia. Los operadores unarios se asocian con el operando de la derecha. Los operadores binarios que tienen la misma precedencia asocian los operandos de izquierda a derecha.

|Operador|Descripción|
|--------------|-----------------|
|**DEFINED (** *Nombredelamacro* **)**|Genera un valor lógico para el estado actual de la definición de *Nombredelamacro*.|
|**EXIST(** *path* **)**|Genera un valor lógico de la existencia de un archivo en *ruta de acceso*.|
|||
|**\!**|NOT lógico unario.|
|**~**|Complemento de uno unario.|
|**-**|Negación unaria.|
|||
|**&#42;**|Multiplicación.|
|**/**|División.|
|**%**|Módulo (resto).|
|||
|**+**|Adición.|
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
|**\!=**|Desigualdad.|
|||
|**&**|AND bit a bit.|
|**^**|XOR bit a bit.|
|**&#124;**|OR bit a bit.|
|||
|**&&**|AND lógico.|
|||
|**&#124;&#124;**|OR lógico.|

> [!NOTE]
> El operador XOR bit a bit (**^**) es el mismo que el carácter de escape y se debe escapar (como **^^**) cuando se usa en una expresión.

## <a name="see-also"></a>Vea también

- [Expresiones de preprocesamiento de archivos MAKE](expressions-in-makefile-preprocessing.md)