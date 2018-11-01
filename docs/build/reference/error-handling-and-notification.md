---
title: Notificación y control de errores
ms.date: 11/04/2016
helpviewer_keywords:
- error handling, and notification
ms.assetid: b621cf60-d869-451a-b05e-dc86d78addaa
ms.openlocfilehash: 845a79e035943dbbde0d498702f70ec7dd6b4d3b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432408"
---
# <a name="error-handling-and-notification"></a>Notificación y control de errores

Para obtener más información sobre la notificación y control de errores, vea [descripción de la función auxiliar](understanding-the-helper-function.md).

Para obtener más información sobre las funciones de enlace, consulte [definiciones de estructura y constante](../../build/reference/structure-and-constant-definitions.md).

Si el programa utiliza archivos DLL de carga retrasada, deberá controlar los errores con solidez puesto que dará como resultado errores que se producen mientras se ejecuta el programa en las excepciones no controladas. Control de errores está formado por dos partes:

Recuperación mediante un enlace.
Si el código necesita recuperar o proporcionar una biblioteca y/o rutina alternativas en caso de error, se puede proporcionar un enlace a la función auxiliar que puede proporcionar o solucionar el problema. La rutina de enlace tiene que devolver un valor adecuado, por lo que el proceso puede continuar (HINSTANCE o FARPROC) o 0 para indicar que debe producirse una excepción. También podría iniciar su propia excepción o **longjmp** desde el enlace. Existen enlaces de notificación y enlaces de error.

Informes a través de una excepción.
Si todo lo necesario para controlar el error es anular el procedimiento, no hay enlace es necesario siempre que el código de usuario pueda controlar la excepción.

Los temas siguientes describen la notificación y control de errores:

- [Enlaces de notificación](../../build/reference/notification-hooks.md)

- [Enlaces de error](../../build/reference/failure-hooks.md)

- [Excepciones](../../build/reference/exceptions-c-cpp.md)

## <a name="see-also"></a>Vea también

[Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)