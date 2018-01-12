---
title: Usar VERIFY en lugar de ASSERT | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: assert
dev_langs: C++
helpviewer_keywords:
- ASSERT statements
- debugging [MFC], ASSERT statements
- VERIFY macro
- assertions, troubleshooting ASSERT statements
- debugging assertions
- assertions, debugging
ms.assetid: 4c46397b-3fb1-49c1-a09b-41a72fae3797
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4ffe046a281bbbbefc251b48df55ecd275515e60
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-verify-instead-of-assert"></a>Usar VERIFY en lugar de ASSERT
Imagine que cuando se ejecuta la versión de depuración de la aplicación MFC, no hay ningún problema. Sin embargo, la versión de lanzamiento de la misma aplicación se bloquea, devuelve resultados incorrectos o presenta algún otro comportamiento extraño.  
  
 Este problema puede deberse al colocar código importante en una instrucción ASSERT para comprobar que funciona correctamente. Dado que las instrucciones de aserción se comenta en una versión de lanzamiento de un programa MFC, el código no se ejecuta en una versión de lanzamiento.  
  
 Si está utilizando ASSERT para confirmar que se ha realizado correctamente en una llamada de función, considere el uso de [compruebe](../../mfc/reference/diagnostic-services.md#verify) en su lugar. La macro VERIFY evalúa sus propios argumentos en ambas versiones de depuración y de lanzamiento de la aplicación.  
  
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
  
 Este código se ejecuta perfectamente en una versión de depuración de una aplicación MFC. Si la llamada a `calloc( )` se produce un error, un mensaje de diagnóstico que incluye el archivo y número de línea aparece. Sin embargo, en una compilación comercial de una aplicación MFC:  
  
-   la llamada a `calloc( )` nunca se produce, dejando `buf` no inicializado, o  
  
-   `strcpy_s( )`copias "`Hello, World`" en una ubicación aleatoria de la memoria, posiblemente, termina la aplicación o haciendo que el sistema deje de responder, o  
  
-   `free()`intenta liberar memoria que nunca se asignó.  
  
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
 [Solucionar problemas de versiones de lanzamiento](../../build/reference/fixing-release-build-problems.md)