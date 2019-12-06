---
title: Expansión de caracteres comodín
ms.date: 11/04/2016
f1_keywords:
- _setargv
helpviewer_keywords:
- asterisk wildcard
- _setargv function
- command line [C++], processing arguments
- command line [C++], wildcards
- command-line wildcards
- question mark, wildcard
ms.assetid: 1a543398-607b-4404-93d1-45d290bde638
ms.openlocfilehash: 1fdea297bb45a06a08bde4f63f90eabef6ddb539
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857182"
---
# <a name="wildcard-expansion"></a>Expansión de caracteres comodín

**Específicos de Microsoft**

Puede utilizar caracteres comodín (signo de interrogación (?) y asterisco (*)) para especificar los argumentos de nombre de archivo y ruta de acceso en la línea de comandos.

Los argumentos de línea de comandos se controlan mediante una rutina llamada `_setargv` (o `_wsetargv` en el entorno de caracteres anchos), que, de forma predeterminada, no expande los caracteres comodín en cadenas independientes en la matriz de cadenas de `argv`. Para obtener más información sobre cómo habilitar la expansión de caracteres comodín, consulte [expandir argumentos comodín](../c-language/expanding-wildcard-arguments.md).

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[main: Inicio de programa](../cpp/main-program-startup.md)