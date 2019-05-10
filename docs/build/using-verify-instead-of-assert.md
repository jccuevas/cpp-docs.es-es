---
title: Usar VERIFY en lugar de ASSERT
ms.date: 05/06/2019
f1_keywords:
- assert
helpviewer_keywords:
- ASSERT statements
- debugging [MFC], ASSERT statements
- VERIFY macro
- assertions, troubleshooting ASSERT statements
- debugging assertions
- assertions, debugging
ms.assetid: 4c46397b-3fb1-49c1-a09b-41a72fae3797
ms.openlocfilehash: 83ea24904c75d41f7c9c9b383f8b7cf8c39e328f
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65217672"
---
# <a name="using-verify-instead-of-assert"></a>Usar VERIFY en lugar de ASSERT

Supongamos que al ejecutar la versión de depuración de la aplicación MFC, no hay ningún problema. Sin embargo, la versión de lanzamiento de la misma aplicación se bloquea, devuelve resultados incorrectos o presenta algún otro comportamiento extraño.

Este problema puede deberse al colocar código importante en una instrucción ASSERT para comprobar que funciona correctamente. Dado que las instrucciones de aserción se comentaron en una versión de lanzamiento de un programa MFC, el código no se ejecuta en una versión de lanzamiento.

Si está utilizando ASSERT para confirmar que una llamada de función se realizó correctamente, considere el uso de [compruebe](../mfc/reference/diagnostic-services.md#verify) en su lugar. La macro VERIFY evalúa sus propios argumentos en ambas versiones de depuración y lanzamiento de la aplicación.

Otra preferencia técnica consiste en asignar el valor devuelto de la función a una variable temporal y, a continuación, pruebe la variable en una instrucción ASSERT.

Examine el siguiente fragmento de código:

```
enum {
    sizeOfBuffer = 20
};
char *buf;
ASSERT(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

Este código se ejecuta perfectamente en una versión de depuración de una aplicación MFC. Si la llamada a `calloc( )` se produce un error, un mensaje de diagnóstico que incluye el número de archivo y la línea aparece. Sin embargo, en una compilación comercial de una aplicación MFC:

- la llamada a `calloc( )` nunca se produce, dejando `buf` sin inicializar, o

- `strcpy_s( )` copias "`Hello, World`" en una ubicación aleatoria de memoria, posiblemente, termina la aplicación o lo que hace que el sistema deje de responder, o

- `free()` intenta liberar memoria que nunca se ha asignado.

Para utilizar ASSERT correctamente, el ejemplo de código se debe cambiar a lo siguiente:

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

O bien, puede usar en su lugar, compruebe:

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
