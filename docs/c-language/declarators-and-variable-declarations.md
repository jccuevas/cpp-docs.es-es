---
title: Declaradores y declaraciones de variables
ms.date: 11/04/2016
helpviewer_keywords:
- declaring variables, declarators
- declarators, definition
- declaring variables, declaration statements
ms.assetid: 5fd67a6a-3a6a-4ec9-b257-3f7390a48d40
ms.openlocfilehash: 928de4b1724577a9fdb282f5109b4b5d0b31c4e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234535"
---
# <a name="declarators-and-variable-declarations"></a>Declaradores y declaraciones de variables

En el resto de esta sección se describe el formato y el significado de las declaraciones de tipos de variable resumidos en esta lista. En concreto, en las secciones restantes se explica cómo declarar los siguientes elementos:

|Tipo de variable|Descripción|
|----------------------|-----------------|
|[Variables simples](../c-language/simple-variable-declarations.md)|Variables de valor único con tipo entero o de punto flotante|
|[Matrices](../c-language/array-declarations.md)|Variables compuestas por una colección de elementos con el mismo tipo|
|[Punteros](../c-language/pointer-declarations.md)|Variables que apuntan a otras variables y contienen ubicaciones variables (en forma de direcciones) en lugar de valores|
|[Variables de enumeración](../c-language/c-enumeration-declarations.md)|Variables simples con tipo entero que contiene un valor de un conjunto de constantes enteras con nombre|
|[Estructuras](../c-language/structure-declarations.md)|Variables compuestas por una colección de valores que pueden tener diferentes tipos|
|[Uniones](../c-language/union-declarations.md)|Variables formadas por varios valores de tipos diferentes que ocupan el mismo espacio de almacenamiento|

Un declarador es la parte de una declaración que especifica el nombre que se va a introducir en el programa. Puede incluir modificadores como <strong>\*</strong> (puntero a) y cualquiera de las palabras clave de convención de llamada de Microsoft.

**Específicos de Microsoft**

En el declarador

```C
__declspec(thread) char *var;
```

`char` es el especificador de tipo, `__declspec(thread)` y `*` son los modificadores y `var` es el nombre del identificador.

**FIN de Específicos de Microsoft**

Utilice declaradores para declarar matrices de valores, punteros a valores y funciones que devuelvan valores de un tipo especificado. Los declaradores aparecen en las declaraciones de matriz y puntero descritas más adelante en esta sección.

## <a name="syntax"></a>Sintaxis

*declarator*:<br/>
&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*direct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(**  *declarator*  **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **[**  *constant-expression*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *parameter-type-list*  **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *identifier-list*<sub>opt</sub> **)**

*pointer*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *type-qualifier-list*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *type-qualifier-list*<sub>opt</sub> *pointer*

*type-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier-list type-qualifier*

> [!NOTE]
> Vea la sintaxis de *declaration* en [Información general de declaraciones](../c-language/overview-of-declarations.md) o [Resumen de la sintaxis del lenguaje C](../c-language/c-language-syntax-summary.md) para conocer la sintaxis que hace referencia a un *declarator*.

Cuando un declarador consta de un identificador sin modificar, el elemento que se va a declarar tiene un tipo base. Si aparece un asterisco (<strong>\*</strong>) a la izquierda de un identificador, el tipo se modifica en un tipo de puntero. Si el identificador va seguido de corchetes ( **[ ]** ), el tipo se modifica en un tipo de matriz. Si el identificador va seguido de paréntesis, el tipo se modifica en un tipo de función. Para obtener más información sobre cómo interpretar la prioridad en declaraciones, vea [Interpretación de declaradores más complejos](../c-language/interpreting-more-complex-declarators.md).

Cada declarador declara al menos un identificador. Un declarador debe incluir un especificador de tipo para que sea una declaración completa. El especificador de tipo proporciona el tipo de los elementos de un tipo de matriz, el tipo de objeto al que apunta un tipo de puntero o el tipo de valor devuelto de una función.

Las declaraciones de [matriz](../c-language/array-declarations.md) y [puntero](../c-language/pointer-declarations.md) se explican con más detalle más adelante en esta sección. En los ejemplos siguientes se muestran algunas formas simples de declaradores:

```C
int list[20]; // Declares an array of 20 int values named list
char *cp;     // Declares a pointer to a char value
double func( void ); // Declares a function named func, with no
                     // arguments, that returns a double value
int *aptr[10] // Declares an array of 10 pointers
```

**Específicos de Microsoft**

El compilador de Microsoft C no limita el número de declaradores que pueden modificar un tipo aritmético, de estructura o de unión. El número solo está limitado por la memoria disponible.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Declaraciones y tipos](../c-language/declarations-and-types.md)
