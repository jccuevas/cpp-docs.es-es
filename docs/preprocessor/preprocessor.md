---
title: Preprocesador
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
ms.assetid: e120eda3-b413-49f1-a07c-e9fb128cf500
ms.openlocfilehash: 7188d7a6803c9eec109a59906cf0c016a460819d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337501"
---
# <a name="preprocessor"></a>Preprocesador

El preprocesador es un procesador de texto que manipula el texto de un archivo de código fuente como parte de la primera fase de traducción. El preprocesador no analiza el texto de origen, pero sí lo divide en tokens para localizar llamadas de macro. Aunque el compilador invoca normalmente el preprocesador en el primer paso, también se puede invocar el preprocesador por separado para procesar el texto sin compilación.

El material de referencia del preprocesador incluye las siguientes secciones:

- [Directivas de preprocesador](../preprocessor/preprocessor-directives.md)

- [Operadores de preprocesador](../preprocessor/preprocessor-operators.md)

- [Macros predefinidas](../preprocessor/predefined-macros.md)

- [Pragmas](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

**Microsoft Specific**

Puede obtener una lista del código fuente después del preprocesamiento mediante la opción del compilador [/E](../build/reference/e-preprocess-to-stdout.md) o [/EP.](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) Ambas opciones invocan el preprocesador y envían el texto resultante al dispositivo de salida estándar, que, en la mayoría de los casos, es la consola. La diferencia entre las `/E` dos `#line` opciones es `/EP` que incluye directivas y elimina estas directivas.

**END Microsoft Specific**

## <a name="special-terminology"></a><a name="_predir_special_terminology"></a>Terminología especial

En la documentación del preprocesador, el término “argumento” hace referencia a la entidad que se pasa a una función. En algunos casos, se modifica por "real" o "formal", que describe la expresión de argumento especificada en la llamada de función y la declaración de argumento especificada en la definición de función, respectivamente.

El término “variable” hace referencia a un objeto de datos de tipo C. El término "objeto" se refiere tanto a los objetos c++ como a las variables; es un término inclusivo.

## <a name="see-also"></a>Consulte también

[Referencia del preprocesador C/C++](../preprocessor/c-cpp-preprocessor-reference.md)\
[Fases de traducción](../preprocessor/phases-of-translation.md)
