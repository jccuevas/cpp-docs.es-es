---
title: Declaraciones de puntero
ms.date: 11/04/2016
helpviewer_keywords:
- pointer declarations
- declarations, pointers
- const keyword [C]
- pointers, declarations
ms.assetid: 8b3b7fc7-f44d-480d-b6f9-cebe4e5462a6
ms.openlocfilehash: 0ee6e9e78f3793cd1912ece7f8627a4be68e929c
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152006"
---
# <a name="pointer-declarations"></a>Declaraciones de puntero

Una *declaración de puntero* identifica una variable de puntero y especifica el tipo del objeto al que señala la variable. Una variable declarada como puntero contiene una dirección de memoria.

## <a name="syntax"></a>Sintaxis

*declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*direct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(** *declarator* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator* **[** *constant-expression*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator* **(** *parameter-type-list* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator* **(** *identifier-list*<sub>opt</sub> **)**

*pointer*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *type-qualifier-list*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *type-qualifier-list*<sub>opt</sub> *pointer*

*type-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier-list* *type-qualifier*

*type-specifier* proporciona el tipo del objeto, que puede ser un elemento básico, una estructura o un tipo de unión. Las variables de puntero también pueden señalar a funciones, matrices y otros punteros. (Para obtener información sobre la declaración y la interpretación de tipos de puntero más complejos, vea [Interpretación de los declaradores más complejos](../c-language/interpreting-more-complex-declarators.md)).

Si crea *type-specifier* **void**, puede retrasar la especificación del tipo al que hace referencia el puntero. Un elemento de este tipo se conoce como "puntero a **void**" y se escribe como `void *`. Una variable declarada como un puntero a *void* se puede usar para señalar a un objeto de cualquier tipo. Sin embargo, para realizar operaciones en el puntero o en el objeto al que señala, el tipo al que señala debe especificarse explícitamente para cada operación. (Las variables de tipo **char** <strong>\*</strong> y tipo **void** <strong>\*</strong> son compatibles con la asignación sin una conversión de tipo). Esta conversión se puede realizar con una conversión de tipo (vea [Conversiones de tipos](../c-language/type-cast-conversions.md) para obtener más información).

*type-qualifier* puede ser **const** o **volatile**, o ambos. Estos especifican, respectivamente, que el propio programa no puede modificar el puntero (**const**), o que el puntero lo puede modificar de forma legítima algún proceso que supere el control del programa (**volatile**). (Vea [Calificadores de tipo](../c-language/type-qualifiers.md) para obtener más información sobre **const** y **volatile**).

*declarator* identifica la variable y puede incluir un modificador de tipo. Por ejemplo, si *declarator* representa una matriz, el tipo de puntero se modifica para ser un puntero a una matriz.

Puede declarar un puntero a un tipo de estructura, de unión o de enumeración antes de definir el tipo de estructura, de unión o de enumeración. El puntero se declara utilizando la etiqueta de estructura o de unión tal como se muestra en los ejemplos siguientes. Se permiten dichas declaraciones porque el compilador no necesita conocer el tamaño de la estructura o de la unión para asignar espacio para la variable de puntero.

## <a name="examples"></a>Ejemplos

En los ejemplos siguientes se muestran declaraciones de puntero.

```
char *message; /* Declares a pointer variable named message */
```

El puntero *message* señala a una variable con el tipo **char**.

```
int *pointers[10];  /* Declares an array of pointers */
```

La matriz de *pointers* tiene 10 elementos; cada elemento es un puntero a una variable con el tipo **int**.

```
int (*pointer)[10]; /* Declares a pointer to an array of 10 elements */
```

La variable *pointer* señala a una matriz con 10 elementos. Cada elemento de esta matriz tiene el tipo **int**.

```
int const *x;      /* Declares a pointer variable, x,
                      to a constant value */
```

El puntero *x* se puede modificar para que señale a un valor **int** diferente, pero el valor al que señala no puede modificarse.

```
const int some_object = 5 ;
int other_object = 37;
int *const y = &fixed_object;
int volatile *const z = &some_object;
int *const volatile w = &some_object;
```

La variable *y* en estas declaraciones se declara como un puntero de constante a un valor **int**. El valor al que señala se puede modificar, pero el propio puntero debe señalar siempre a la misma ubicación: la dirección de *fixed_object*. De igual forma, *z* es un puntero de constante, pero también se declara para que señale a un elemento **int** cuyo valor no lo pueda modificar el programa. El especificador adicional **volatile** indica que aunque el valor de **const int** al que señala *z* no lo puede modificar el programa, podría modificarlo de forma legítima un proceso ejecutado simultáneamente con el programa. La declaración de *w* especifica que el programa no puede cambiar el valor al que se señala y que el programa no puede modificar el puntero.

```
struct list *next, *previous; /* Uses the tag for list */
```

En este ejemplo se declaran dos variables de puntero, *next* y *previous*, que señalan al tipo de estructura *list*. Esta declaración puede aparecer antes que la definición del tipo de estructura *list* (vea el ejemplo siguiente), mientras que la definición de tipo *list* tiene la misma visibilidad que la declaración.

```
struct list
{
    char *token;
    int count;
    struct list *next;
} line;
```

La variable *line* tiene el tipo de estructura denominado *list*. El tipo de estructura *list* tiene tres miembros: el primer miembro es un puntero a un valor **char**, el segundo es un valor **int** y el tercero es un puntero a otra estructura *list*.

```
struct id
{
    unsigned int id_no;
    struct name *pname;
} record;
```

La variable *record* tiene el tipo de estructura denominado *id*. Observe que *pname* se declara como un puntero a otro tipo de estructura denominado *name*. Esta declaración puede aparecer antes de que se defina el tipo *name*.

## <a name="see-also"></a>Vea también

[Declaradores y declaraciones de variables](../c-language/declarators-and-variable-declarations.md)
