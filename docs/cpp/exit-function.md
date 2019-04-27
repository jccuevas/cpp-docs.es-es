---
title: exit (Función)
ms.date: 11/04/2016
f1_keywords:
- Exit
helpviewer_keywords:
- exit function
ms.assetid: 26ce439f-81e2-431c-9ff8-a09a96f32127
ms.openlocfilehash: 82c9d00a49c8a080d893a51052739a0265ad0860
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154443"
---
# <a name="exit-function"></a>exit (Función)

El **salir** función, declarada en el archivo de inclusión estándar \<stdlib.h >, finaliza un programa de C++.

El valor proporcionado como argumento a **salir** se devuelve al sistema operativo como código de salida o de código de retorno del programa. Por convención, un código de retorno de cero significa que el programa se completó correctamente.

> [!NOTE]
>  Puede usar las constantes EXIT_FAILURE y EXIT_SUCCESS, definido en \<stdlib.h >, para indicar éxito o error del programa.

Emitir un **devolver** instrucción desde el `main` función es equivalente a llamar a la **salir** función con el valor devuelto como argumento.

Para obtener más información, consulte [salir](../c-runtime-library/reference/exit-exit-exit.md) en el *referencia de la biblioteca de tiempo de ejecución*.

## <a name="see-also"></a>Vea también

[Finalización del programa](../cpp/program-termination.md)