---
title: Interpretar declaradores más complejos
ms.date: 11/04/2016
helpviewer_keywords:
- complex declarators
- interpreting complex declarators
ms.assetid: dd5b7019-c86d-4645-a5cc-21f834de6f4a
ms.openlocfilehash: 13c81728f02963863b641348b58380da099b0013
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232870"
---
# <a name="interpreting-more-complex-declarators"></a>Interpretar declaradores más complejos

Puede incluir cualquier declarador entre paréntesis para especificar una interpretación determinada de un “declarador complejo”. Un declarador complejo es un identificador calificado por más de un modificador de función, puntero o matriz. Puede aplicar varias combinaciones de modificadores de función, puntero y matriz a un único identificador. En general, `typedef` puede utilizarse para simplificar declaraciones. Vea [Declaraciones typedef](../c-language/typedef-declarations.md).

En la interpretación de declaradores complejos, los corchetes y los paréntesis (es decir, los modificadores a la derecha del identificador) tienen prioridad sobre los asteriscos (es decir, los modificadores a la izquierda del identificador). Los corchetes y los paréntesis tienen la misma precedencia y se asocian de izquierda a derecha. Una vez que el declarador se ha interpretado totalmente, se aplica el especificador de tipo al último paso. Mediante el uso de paréntesis, puede reemplazar el orden de asociación predeterminado y forzar una interpretación determinada. Nunca utilice paréntesis, no obstante, alrededor de un nombre de identificador solo. Se podría interpretar como una lista de parámetros.

Una manera sencilla de interpretar declaradores complejos es leerlos “desde dentro hacia fuera” siguiendo estos cuatro pasos:

1. Comience por el identificador y busque corchetes o paréntesis directamente a la derecha (si los hay).

1. Interprete estos corchetes o paréntesis y, a continuación, busque asteriscos a la izquierda.

1. Si encuentra un paréntesis de cierre en cualquier etapa, vuelva y aplique las reglas 1 y 2 a todo lo que haya dentro de los paréntesis.

1. Aplique el especificador de tipo.

    ```
    char *( *(*var)() )[10];
     ^   ^  ^ ^ ^   ^    ^
     7   6  4 2 1   3    5
    ```

En este ejemplo, los pasos se numeran en orden y pueden interpretarse de la manera siguiente:

1. El identificador `var` se declara como

1. un puntero a

1. una función que devuelve

1. un puntero a

1. una matriz de 10 elementos, que son

1. punteros a

1. valores `char`.

## <a name="examples"></a>Ejemplos

En los ejemplos siguientes se muestran otras declaraciones complejas y se muestra cómo pueden afectar los paréntesis al significado de una declaración.

```
int *var[5]; /* Array of pointers to int values */
```

El modificador de matriz tiene mayor prioridad que el modificador de puntero, así que `var` se declara como una matriz. El modificador de puntero se aplica al tipo de los elementos de la matriz; por consiguiente, los elementos de la matriz son punteros a valores `int`.

```
int (*var)[5]; /* Pointer to array of int values */
```

En esta declaración para `var`, los paréntesis dan al modificador de puntero mayor prioridad que el modificador de matriz y `var` se declara como puntero a una matriz de cinco valores `int`.

```
long *var( long, long ); /* Function returning pointer to long */
```

Los modificadores de función también tienen mayor prioridad que los modificadores de puntero, por lo que esta declaración para `var` declara `var` como una función que devuelve un puntero a un valor **long**. La función se declara para que tome dos valores **long** como argumentos.

```
long (*var)( long, long ); /* Pointer to function returning long */
```

Este ejemplo es similar al anterior. Los paréntesis dan al modificador de puntero mayor prioridad que al modificador de función y `var` se declara como puntero a una función que devuelve un valor **long**. Una vez más la función toma dos argumentos **long**.

```
struct both       /* Array of pointers to functions */
{                 /*   returning structures         */
    int a;
    char b;
} ( *var[5] )( struct both, struct both );
```

Los elementos de una matriz no pueden ser funciones, pero esta declaración muestra cómo declarar una matriz de punteros a funciones en su lugar. En este ejemplo, `var` se declara como una matriz de cinco punteros a funciones que devuelven estructuras con dos miembros. Los argumentos para funciones se declaran como dos estructuras con el mismo tipo de estructura, `both`. Observe que los paréntesis que rodean a `*var[5]` son obligatorios. Sin ellos, la declaración es un intento no válido de declarar una matriz de funciones, como se muestra a continuación:

```
/* ILLEGAL */
struct both *var[5](struct both, struct both);
```

La instrucción siguiente declara una matriz de punteros.

```
unsigned int *(* const *name[5][10] ) ( void );
```

La matriz `name` tiene 50 elementos organizados en una matriz multidimensional. Los elementos son punteros a un puntero que es una constante. Este puntero constante apunta a una función que no tiene ningún parámetro y devuelve un puntero a un tipo sin signo.

El ejemplo siguiente es una función que devuelve un puntero a una matriz de tres valores **double**.

```
double ( *var( double (*)[3] ) )[3];
```

En esta declaración, una función devuelve un puntero a una matriz, dado que las funciones que devuelven matrices no son válidas. Aquí, `var` se declara como una función que devuelve un puntero a una matriz de tres valores **double**. La función `var` toma un argumento. El argumento, como el valor devuelto, es un puntero a una matriz de tres valores **double**. El tipo de argumento lo da un elemento *abstract-declarator* complejo. Los paréntesis alrededor del asterisco en el tipo de argumento son obligatorios; sin ellos, el tipo de argumento sería una matriz de tres punteros a valores **double**. Para obtener una descripción y ejemplos de declaradores abstractos, vea [Declaradores abstractos](../c-language/c-abstract-declarators.md).

```
union sign         /* Array of arrays of pointers */
{                  /* to pointers to unions       */
     int x;
     unsigned y;
} **var[5][5];
```

Como se muestra en el ejemplo anterior, un puntero puede señalar a otro puntero y una matriz puede contener matrices como elementos. Aquí, `var` es una matriz de cinco elementos. Cada elemento es una matriz de cinco elementos de punteros a punteros a uniones con dos miembros.

```
union sign *(*var[5])[5]; /* Array of pointers to arrays
                             of pointers to unions        */
```

En este ejemplo se muestra cómo la posición de los paréntesis cambia el significado de la declaración. En este ejemplo, `var` es una matriz de cinco elementos de punteros a matrices de cinco elementos de punteros a uniones. Para obtener ejemplos de cómo usar `typedef` para evitar declaraciones complejas, vea [Declaraciones typedef](../c-language/typedef-declarations.md).

## <a name="see-also"></a>Vea también

[Declaraciones y tipos](../c-language/declarations-and-types.md)
