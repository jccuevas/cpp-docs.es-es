---
title: Resolver declaraciones ambiguas (C++)
ms.date: 11/04/2016
ms.assetid: 3d773ee7-bbea-47de-80c2-cb0a9d4ec0b9
ms.openlocfilehash: 52e94f474d59505298cb4f78a477cedd21b90aad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507372"
---
# <a name="resolving-ambiguous-declarations-c"></a>Resolver declaraciones ambiguas (C++)

Para realizar conversiones explícitas de un tipo a otro, debe utilizar las conversiones especificando el nombre de tipo que desee. Algunas conversiones de tipos producen ambigüedad sintáctica. La siguiente conversión de tipo de estilo de función es ambigua:

```cpp
char *aName( String( s ) );
```

No está claro si es una declaración de función o una declaración de objeto con un estilo de función de conversión como inicializador: podría declarar una función que devuelve el tipo `char *` que toma un argumento de tipo `String`, o podría declarar el objeto `aName` e inicialícela con el valor de `s` conversión al tipo `String`.

Si una declaración puede considerarse una declaración de función válida, se trata como tal. Solo si no puede ser una declaración de función (es decir, si fuera sintácticamente incorrecta) es una instrucción que podría tratarse como una conversión de tipo de estilo de función. Por consiguiente, el compilador interpreta la instrucción como una declaración de una función y omite los paréntesis incluidos alrededor del identificador `s`. Sin embargo, las instrucciones:

```cpp
char *aName( (String)s );
```

y

```cpp
char *aName = String( s );
```

son claramente declaraciones de objetos y conversión de tipo definido por el usuario `String` escriba `char *` se invoca para llevar a cabo la inicialización de `aName`.