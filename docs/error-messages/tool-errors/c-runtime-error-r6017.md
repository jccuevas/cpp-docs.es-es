---
title: C Runtime Error R6017 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6017
dev_langs:
- C++
helpviewer_keywords:
- R6017
ms.assetid: df3ec5f5-6771-4648-ba06-0e26c6a1cc6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2437e33610222183aa03a22cf6638156aaaa5e9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077040"
---
# <a name="c-runtime-error-r6017"></a>C Runtime Error R6017

error inesperado de bloqueo de multiproceso

> [!NOTE]
>  Si encuentra este mensaje de error al ejecutar una aplicación, la aplicación se cerró porque tiene un problema interno. Hay varias razones posibles para este error, pero a menudo se debe a un defecto en el código de la aplicación.
>
>  Puede intentar seguir estos pasos para corregir este error:
>
>  -   Use la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para reparar o reinstalar el programa.
> -   Comprobar **Windows Update** en el **Panel de Control** las actualizaciones de software.
> -   Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

El proceso recibe un error inesperado al intentar obtener acceso a un bloqueo multiproceso de C en tiempo de ejecución en un recurso del sistema. Este error suele producirse si el proceso de forma inadvertida modifica los datos del montón en tiempo de ejecución. Sin embargo, también puede deberse a un error interno en la biblioteca de tiempo de ejecución o el código del sistema operativo.

Para corregir este problema, compruebe si hay errores de daños del montón en el código. Para obtener más información y ejemplos, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). A continuación, compruebe que está usando los archivos redistribuibles más recientes para la implementación de la aplicación. Para obtener información, consulte [implementación en Visual C++](../../ide/deployment-in-visual-cpp.md).