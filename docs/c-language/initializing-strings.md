---
title: Inicializar cadenas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- character arrays, initializing
- strings [C++], initializing
- initializing arrays, strings
ms.assetid: 0ab8079d-d0d3-48f9-afd1-36a7bb439b29
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e954fc417fb62d3bd08b1c37d445a3d7f2bc9ec9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034881"
---
# <a name="initializing-strings"></a>Inicializar cadenas

Puede inicializar una matriz de caracteres (o caracteres anchos) con un literal de cadena (o literal de cadena ancho). Por ejemplo:

```
char code[ ] = "abc";
```

inicializa `code` como una matriz de caracteres de cuatro elementos. El cuarto elemento es el carácter null, que finaliza todos los literales de cadena.

La longitud de una lista de identificadores solo puede equivaler al número de identificadores que se inicializarán. Si especifica un tamaño de matriz que es más corto que la cadena, se omiten los caracteres adicionales. Por ejemplo, la declaración siguiente inicializa `code` como una matriz de caracteres de tres elementos:

```
char code[3] = "abcd";
```

Solo los tres primeros caracteres del inicializador se asignan a `code`. Se descartan el carácter `d` y el carácter null que finaliza la cadena. Observe que se crea una cadena no finalizada (es decir, una cadena que carece de un valor 0 que indique su final) y genera un mensaje de diagnóstico para notificar esta condición.

La declaración

```
char s[] = "abc", t[3] = "abc";
```

es idéntica a

```
char s[]  = {'a', 'b', 'c', '\0'},
     t[3] = {'a', 'b', 'c' };
```

Si el tamaño de la cadena es menor que el especificado de la matriz, los elementos restantes de la matriz se inicializan en 0.

**Específicos de Microsoft**

En Microsoft C, los literales de cadena pueden tener hasta 2048 bytes de longitud.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Inicialización](../c-language/initialization.md)