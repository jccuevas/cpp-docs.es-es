---
title: Tipos de datos de SBCS y MBCS | Microsoft Docs
ms.custom: ''
ms.date: 04/11/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- MBCS
- SBCS
dev_langs:
- C++
helpviewer_keywords:
- SBCS and MBCS data types
- data types [C], MBCS and SBCS
ms.assetid: 4c3ef9da-e397-48d4-800e-49dba36db171
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f75999b1436ef350e12c47405cac911367ffda2b
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="sbcs-and-mbcs-data-types"></a>Tipos de datos de SBCS y MBCS

Cualquier rutina de biblioteca en tiempo de ejecución de MBCS que solo controla un carácter multibyte o un byte de un carácter multibyte espera un argumento `unsigned int` (donde 0x00 <= valor de carácter <= 0xFFFF y 0x00 <= valor de byte <= 0xFF). Una rutina MBCS que controla bytes o caracteres multibyte en un contexto de cadena espera que una cadena de caracteres multibyte se represente como un puntero `unsigned char`.

> [!CAUTION]
> Cada byte de un carácter multibyte se puede representar en un **char** de 8 bits. En cambio, un carácter de un solo byte de SBCS o MBCS de tipo **char** con un valor mayor que 0x7F es negativo. Cuando este tipo de caracteres se convierten directamente a un **int** o un **long**, el resultado es la extensión de signo por el compilador y, por tanto, se pueden producir resultados inesperados.

Por consiguiente, es mejor representar un byte de un carácter multibyte como un `unsigned char` de 8 bits . O bien, para evitar un resultado negativo, basta con convertir un carácter de un solo byte de tipo **char** a un `unsigned char` antes de convertirlo en un **int** o un **long**.

Dado que algunas funciones de control de cadenas de SBCS reciben parámetros **char\*** (con signo), se genera una advertencia del compilador de error de coincidencia de tipos cuando se define **_MBCS**. Hay tres formas de evitar esta advertencia, por orden de eficacia:

1. Usar las funciones insertadas con seguridad de tipos en TCHAR.H. Éste es el comportamiento predeterminado.

1. Usar las macros directas en TCHAR.H al definir **_MB_MAP_DIRECT** en la línea de comandos. Si lo hace, deberá hacer coincidir los tipos manualmente. Este es el método más rápido, pero no incluye seguridad de tipos.

1. Usar las funciones de biblioteca vinculada estáticamente con seguridad de tipos en TCHAR.H. Para ello, defina la constante **_NO_INLINING** en la línea de comandos. Este es el método más lento, pero garantiza prácticamente la seguridad de tipos.

## <a name="see-also"></a>Vea también

[Internacionalización](../c-runtime-library/internationalization.md)<br/>
[Rutinas en tiempo de ejecución Universal C por categoría](../c-runtime-library/run-time-routines-by-category.md)<br/>
