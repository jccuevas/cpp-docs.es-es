---
title: R6016 de Error de tiempo de ejecución de C | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6016
dev_langs:
- C++
helpviewer_keywords:
- R6016
ms.assetid: 7bd3f274-d9c4-4bc4-8252-80bf168c4c3a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f366ceff24ce65e6f7869f9709f547651687c327
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33306941"
---
# <a name="c-runtime-error-r6016"></a>R6016 de Error de tiempo de ejecución de C
espacio insuficiente para datos de subproceso  
  
> [!NOTE]
>  Si aparece este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque tiene un problema de memoria interna. Hay muchas razones posibles para este error, pero a menudo está provocada por una condición de memoria muy baja, un error en la aplicación, o a un error en un complemento o una extensión de la aplicación.  
>   
>  Puede intentar seguir estos pasos para corregir este error:  
>   
>  -   Cierre otras aplicaciones en ejecución o reinicie el equipo para liberar memoria.  
> -   Use la **aplicaciones y características** o **programas y características** página en el **el Panel de Control** para reparar o reinstalar la aplicación.  
> -   Use la **aplicaciones y características** o **programas y características** página en el **el Panel de Control** para quitar, reparar o reinstalar complementos o extensiones que usa la aplicación.  
> -   Comprobar **Windows Update** en el **el Panel de Control** las actualizaciones de software.  
> -   Busque una versión actualizada de la aplicación. Si el problema continúa, póngase en contacto con el proveedor de la aplicación.  
  
 **Información para programadores**  
  
 Este error se produce porque el programa no recibió memoria suficiente del sistema operativo para completar una [_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md) o `_beginthreadex` llamada o subproceso almacenamiento local no se inicializó por `_beginthread` o `_beginthreadex`.  
  
 Cuando se inicia un subproceso nuevo, la biblioteca debe crear una base de datos interna para el subproceso. Si la base de datos no se puede ampliar utilizando la memoria proporcionada por el sistema operativo, el subproceso no se puede iniciar y se detiene el proceso de llamada. Esto puede ocurrir cuando el proceso ha creado demasiados subproceso o si se ha agotado el almacenamiento local para el subproceso.  
  
 Se recomienda que se debe usar un archivo ejecutable que llama a la biblioteca en tiempo de ejecución de C (CRT) `_beginthreadex` para la creación de subprocesos en lugar de la API de Windows `CreateThread`. `_beginthreadex` inicializa el almacenamiento estático interno que usan muchas funciones CRT en el almacenamiento local de subprocesos. Si utiliza `CreateThread` para crear un subproceso, CRT puede finalizar el proceso con R6016 cuando se realiza una llamada a una función CRT que requiere que el almacenamiento estático interno se haya inicializado.