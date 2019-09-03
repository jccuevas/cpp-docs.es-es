---
title: Preprocesador
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
ms.assetid: e120eda3-b413-49f1-a07c-e9fb128cf500
ms.openlocfilehash: 883504810f1b659e28764a75ebc7cfda325920a5
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222237"
---
# <a name="preprocessor"></a>Preprocesador

El preprocesador es un procesador de texto que manipula el texto de un archivo de código fuente como parte de la primera fase de traducción. El preprocesador no analiza el texto de origen, pero lo divide en tokens para buscar llamadas de macro. Aunque el compilador invoca normalmente el preprocesador en el primer paso, también se puede invocar el preprocesador por separado para procesar el texto sin compilación.

El material de referencia del preprocesador incluye las siguientes secciones:

- [Directivas de preprocesador](../preprocessor/preprocessor-directives.md)

- [Operadores de preprocesador](../preprocessor/preprocessor-operators.md)

- [Macros predefinidas](../preprocessor/predefined-macros.md)

- [Pragmas](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

**Específicos de Microsoft**

Puede obtener una lista del código fuente después del preprocesamiento mediante la opción del compilador [/e](../build/reference/e-preprocess-to-stdout.md) o [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) . Ambas opciones invocan el preprocesador y envían el texto resultante al dispositivo de salida estándar, que, en la mayoría de los casos, es la consola. La diferencia entre las dos opciones es que `/E` incluye `#line` directivas y `/EP` elimina estas directivas.

**FIN de Específicos de Microsoft**

##  <a name="_predir_special_terminology"></a>Terminología especial

En la documentación del preprocesador, el término “argumento” hace referencia a la entidad que se pasa a una función. En algunos casos, es modificado por "real" o "formal", que describe la expresión de argumento especificada en la llamada de función, y la declaración de argumento especificada en la definición de función, respectivamente.

El término “variable” hace referencia a un objeto de datos de tipo C. El término "objeto" hace referencia tanto C++ a objetos como a variables. es un término inclusivo.

## <a name="see-also"></a>Vea también

[Referencia deC++ C/preprocesador](../preprocessor/c-cpp-preprocessor-reference.md)\
[Fases de traducción](../preprocessor/phases-of-translation.md)
