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
ms.openlocfilehash: 212f39ee62008b391977aaa91d5c8c4fadfd9730
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336469"
---
# <a name="makefile-preprocessing-operators"></a>Operadores de preprocesamiento de archivos MAKE

Las expresiones de preprocesamiento de archivos Make pueden usar operadores que actúan sobre valores constantes, códigos de salida de comandos, cadenas, macros y rutas de acceso del sistema de archivos. Para evaluar la expresión, el preprocesador expande primero las macros, luego ejecuta los comandos y, después, realiza las operaciones. Las operaciones se evalúan en el orden de agrupación explícita entre paréntesis y, luego, en el orden de precedencia de los operadores. El resultado es un valor constante.

El operador **DEFINED** es un operador lógico que actúa sobre un nombre de macro. La expresión **DEFINED(**_macroname_**)** es true si se define *macroname,* incluso si no tiene un valor asignado. **DEFINIDO** en combinación con **! SI** o **! ELSE IF** es equivalente a **! IFDEF** o **! ELSE IFDEF**. Sin embargo, a diferencia de estas directivas, **DEFINED** se puede utilizar en expresiones complejas.

El operador **EXIST** es un operador lógico que actúa en una ruta de acceso del sistema de archivos. **EXIST(**_path_**)** es true si existe la ruta de *acceso.* El resultado de **EXIST** se puede utilizar en expresiones binarias. Si *path* contiene espacios, enciérrela entre comillas dobles.

Para comparar dos cadenas, utilice**==** el operador de igualdad ( ) o el operador de desigualdad (**! .** Escriba las cadenas entre comillas dobles.

Las constantes enteras pueden utilizar los**-** operadores unarios**~** para la negación numérica ( ), el complemento ( ) y la negación lógica (**!**).

Las expresiones pueden usar los siguientes operadores. Agrupamos los operadores que tienen la misma precedencia, y estos grupos se muestran en orden de mayor a menor precedencia. Los operadores unarios se asocian con el operando de la derecha. Los operadores binarios que tienen la misma precedencia asocian los operandos de izquierda a derecha.

|Operator|Descripción|
|--------------|-----------------|
|**DEFINED(** *macroname* **)**|Produce un valor lógico para el estado de definición actual de *macroname*.|
|**EXIST(** *path* **)**|Produce un valor lógico para la existencia de un archivo en la ruta de *acceso.*|
|||
|**!**|NOT lógico unario.|
|**~**|Complemento de unaría.|
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
> El operador XOR**^** bit a bit ( ) es el mismo **^^** que el carácter de escape y debe tener escape (como ) cuando se utiliza en una expresión.

## <a name="see-also"></a>Consulte también

- [Expresiones en el preprocesamiento de Makefile](expressions-in-makefile-preprocessing.md)
