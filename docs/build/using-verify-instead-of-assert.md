---
title: Usar VERIFY en lugar de ASSERT
ms.date: 05/06/2019
helpviewer_keywords:
- ASSERT statements
- debugging [MFC], ASSERT statements
- VERIFY macro
- assertions, troubleshooting ASSERT statements
- debugging assertions
- assertions, debugging
ms.assetid: 4c46397b-3fb1-49c1-a09b-41a72fae3797
ms.openlocfilehash: bfc0847677ae232fef67ab6200c626472f042bdb
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438611"
---
# <a name="using-verify-instead-of-assert"></a>Usar VERIFY en lugar de ASSERT

Supongamos que, al ejecutar la versión de depuración de la aplicación de MFC, no hay problemas. Sin embargo, la versión de lanzamiento de la misma aplicación se bloquea, devuelve resultados incorrectos o exhibe algún otro comportamiento anómalo.

Este problema puede producirse cuando se coloca código importante en una instrucción Assert para comprobar que funciona correctamente. Dado que las instrucciones Assert están comentadas en una compilación de versión de un programa de MFC, el código no se ejecuta en una compilación de versión.

Si usa la instrucción Assert para confirmar que una llamada de función se ha realizado correctamente, considere la posibilidad de usar la macro [VERIFY](../mfc/reference/diagnostic-services.md#verify) en su lugar. La macro VERIFY evalúa sus propios argumentos en las compilaciones de depuración y de versión de la aplicación.

Otra técnica preferida es asignar el valor devuelto de la función a una variable temporal y, a continuación, probar la variable en una instrucción Assert.

Observe el siguiente fragmento de código:

```
enum {
    sizeOfBuffer = 20
};
char *buf;
ASSERT(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

Este código se ejecuta perfectamente en una versión de depuración de una aplicación de MFC. Si se produce un error en la llamada a `calloc( )`, aparece un mensaje de diagnóstico que incluye el archivo y el número de línea. Sin embargo, en una compilación comercial de una aplicación de MFC:

- La llamada a `calloc( )` nunca se produce y se deja `buf` no inicializado.

- `strcpy_s( )` copia "`Hello, World`" en una parte aleatoria de la memoria, lo que posiblemente bloquea la aplicación o hace que el sistema deje de responder.

- `free()` intenta liberar memoria que nunca se ha asignado.

Para usar Assert correctamente, el ejemplo de código se debe cambiar por lo siguiente:

```
enum {
    sizeOfBuffer = 20
};
char *buf;
buf = (char *) calloc(sizeOfBuffer, sizeof(char) );
ASSERT( buf != NULL );
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

O bien, puede usar la macro VERIFY en su lugar:

```
enum {
    sizeOfBuffer = 20
};
char *buf;
VERIFY(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

## <a name="see-also"></a>Vea también

[Solucionar problemas de versiones de lanzamiento](fixing-release-build-problems.md)
