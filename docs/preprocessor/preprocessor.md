---
title: Preprocesador | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor
ms.assetid: e120eda3-b413-49f1-a07c-e9fb128cf500
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 74cf3ff56f37375cd8f267e3541b78e2d76a18fa
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083313"
---
# <a name="preprocessor"></a>Preprocesador
El preprocesador es un procesador de texto que manipula el texto de un archivo de código fuente como parte de la primera fase de traducción. El preprocesador no analiza el texto original, sino que lo divide en tokens con el fin de buscar llamadas a macros. Aunque el compilador invoca normalmente el preprocesador en el primer paso, también se puede invocar el preprocesador por separado para procesar el texto sin compilación.

El material de referencia del preprocesador incluye las siguientes secciones:

- [Directivas de preprocesador](../preprocessor/preprocessor-directives.md)

- [Operadores de preprocesador](../preprocessor/preprocessor-operators.md)

- [Macros predefinidas](../preprocessor/predefined-macros.md)

- [Pragmas](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

**Específicos de Microsoft**

Puede obtener una lista de código fuente tras el preprocesamiento mediante el uso de la [/E](../build/reference/e-preprocess-to-stdout.md) o [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) opción del compilador. Ambas opciones invocan el preprocesador y envían el texto resultante al dispositivo de salida estándar que, en la mayoría de los casos, es la consola. La diferencia entre las dos opciones es que /E incluye las directivas `#line` y /EP elimina estas directivas.

**FIN de Específicos de Microsoft**

##  <a name="_predir_special_terminology"></a> Terminología especial

En la documentación del preprocesador, el término “argumento” hace referencia a la entidad que se pasa a una función. En algunos casos, se cambia por “real” o “formal”, que describe la expresión de argumento especificada en la llamada de función y la declaración de argumento especificada en la definición de función, respectivamente.

El término “variable” hace referencia a un objeto de datos de tipo C. El término “objeto” hace referencia tanto a objetos como a variables de C++; es un término inclusivo.

## <a name="see-also"></a>Vea también

[Referencia del preprocesador de C/C++](../preprocessor/c-cpp-preprocessor-reference.md)<br/>
[Fases de traducción](../preprocessor/phases-of-translation.md)