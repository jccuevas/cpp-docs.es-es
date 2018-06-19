---
title: Declaraciones de enumeración de C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declarations, enumerations
- define directive (#define), alternative to
- enumerators, declaring
- '#define directive, alternative to'
- named constants, enumeration declarations
- declaring enumerations
ms.assetid: bd18f673-4dda-4bc1-92fd-d1ce10074910
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 697e4f37c8a59c40df80e29ff89f2021f61fb468
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389746"
---
# <a name="c-enumeration-declarations"></a>Declaraciones de enumeración de C
Una enumeración consta de un conjunto de constantes enteras con nombre. Una declaración de tipos de enumeración proporciona el nombre de la etiqueta de enumeración (opcional) y define el conjunto de identificadores enteros con nombre (denominado “conjunto de enumeración”, “constantes de enumerador”, “enumeradores” o “miembros”). Una variable con tipo de enumeración almacena uno de los valores del conjunto de enumeración definido por ese tipo.  
  
 Las variables de tipo `enum` se pueden usar en expresiones de indización y como operandos de todos los operadores relacionales y aritméticos. Las enumeraciones proporcionan una alternativa a la directiva de preprocesador `#define` con las ventajas de que los valores se pueden generar automáticamente y pueden seguir reglas de ámbito normales.  
  
 En ANSI C, las expresiones que definen el valor de una constante de enumerador siempre tienen el tipo `int`; así, el almacenamiento asociado a una variable de enumeración es el almacenamiento requerido por un único valor `int`. Una constante de enumeración o un valor de tipo enumerado se pueden usar en cualquier lugar donde el lenguaje C permita una expresión de tipo entero.  
  
## <a name="syntax"></a>Sintaxis  
 *enum-specifier*:  
 **enum**  *identifier* opt **{** *enumerator-list* **}**  
  
 **enum**  *identifier*  
  
 El elemento opcional *identifier* nombra el tipo de enumeración definido por el elemento *enumerator-list*. Este identificador se suele denominar la “etiqueta” de la enumeración especificada por la lista. Un especificador de tipo de la forma  
  
```  
  
enum  
identifier  
{  
enumerator-list  
}  
  
```  
  
 declara que *identifier* es la etiqueta de la enumeración especificada por el elemento *enumerator-list* no terminal. El elemento *enumerator-list* define el "contenido del enumerador". El elemento *enumerator-list* se describe en detalle a continuación.  
  
 Si la declaración de una etiqueta es visible, las declaraciones subsiguientes que utilizan la etiqueta pero omiten *enumerator-list* especifican el tipo enumerado declarado previamente. La etiqueta debe hacer referencia a un tipo de enumeración definido y ese tipo de enumeración debe estar en el ámbito actual. Puesto que el tipo de enumeración se define en otro lugar, *enumerator-list* no aparece en esta declaración. Las declaraciones de tipos derivados de enumeraciones y las declaraciones `typedef` para tipos de enumeración pueden utilizar la etiqueta de la enumeración antes de definir el tipo de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
 *enumerator-list*:  
 *enumerator*  
  
 *enumerator-list* **,**  `enumerator`  
  
 `enumerator`:  
 *enumeration-constant*  
  
 *enumeration-constant*  **=**  *constant-expression*  
  
 *enumeration-constant*:  
 *identifier*  
  
 Cada *enumeration-constant* de un elemento *enumeration-list* nombra un valor del conjunto de enumeración. De forma predeterminada, la primera *enumeration-constant* se asocia al valor 0. El siguiente elemento *enumeration-constant* de la lista se asocia al valor de (*constant-expression* + 1), a menos que se asocie explícitamente a otro valor. El nombre de un elemento *enumeration-constant* equivale a su valor.  
  
 Puede utilizar *enumeration-constant = constant-expression* para reemplazar la secuencia predeterminada de valores. Así, si *enumeration-constant = constant-expression* aparece en el elemento *enumerator-list*, *enumeration-constant* se asocia al valor especificado por *constant-expression*. El elemento *constant-expression* debe tener tipo `int` y puede ser negativo.  
  
 Las reglas siguientes se aplican a los miembros de un conjunto de enumeración:  
  
-   Un conjunto de enumeración puede contener valores constantes duplicados. Por ejemplo, puede asociar el valor 0 a dos identificadores diferentes, llamados por ejemplo `null` y `zero`, en el mismo conjunto.  
  
-   Los identificadores de la lista de enumeración deben ser distintos de otros identificadores del mismo ámbito con la misma visibilidad, como nombres de variable normales e identificadores de otras listas de enumeración.  
  
-   Las etiquetas de enumeración siguen las reglas habituales de ámbito. Deben ser distintas de otras etiquetas de enumeración, estructura y unión con la misma visibilidad.  
  
## <a name="examples"></a>Ejemplos  
 Estos ejemplos muestran declaraciones de enumeración:  
  
```  
enum DAY            /* Defines an enumeration type    */  
{  
    saturday,       /* Names day and declares a       */  
    sunday = 0,     /* variable named workday with    */   
    monday,         /* that type                      */  
    tuesday,  
    wednesday,      /* wednesday is associated with 3 */  
    thursday,  
    friday  
} workday;  
```  
  
 El valor 0 se asocia a `saturday` de forma predeterminada. El identificador `sunday` se establece explícitamente en 0. Los identificadores restantes reciben los valores 1 a 5 de forma predeterminada.  
  
 En este ejemplo, un valor del conjunto `DAY` se asigna a la variable `today`.  
  
```  
enum DAY today = wednesday;  
```  
  
 Observe que el nombre de la constante de enumeración se utiliza para asignar el valor. Desde que el tipo de enumeración `DAY` se declaró previamente, solo es necesaria la etiqueta de enumeración `DAY`.  
  
 Para asignar explícitamente un valor entero a una variable de un tipo de datos enumerado, utilice una conversión de tipo:  
  
```  
workday = ( enum DAY ) ( day_value - 1 );  
```  
  
 Esta conversión es recomendable en C, pero no es necesaria.  
  
```  
enum BOOLEAN  /* Declares an enumeration data type called BOOLEAN */  
{  
    false,     /* false = 0, true = 1 */  
    true   
};   
  
enum BOOLEAN end_flag, match_flag; /* Two variables of type BOOLEAN */  
```  
  
 Esta declaración también se puede especificar como  
  
```  
enum BOOLEAN { false, true } end_flag, match_flag;\  
```  
  
 o como  
  
```  
enum BOOLEAN { false, true } end_flag;  
enum BOOLEAN match_flag;  
```  
  
 Un ejemplo que utilizara estas variables sería similar a:  
  
```  
if ( match_flag == false )  
    {  
     .  
     .   /* statement */   
     .  
    }  
    end_flag = true;  
```  
  
 Los tipos de datos de enumerador sin nombre también pueden declararse. El nombre del tipo de datos se omite, pero las variables se pueden declarar. La variable `response` es una variable del tipo definido:  
  
```  
enum { yes, no } response;  
```  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../cpp/enumerations-cpp.md)