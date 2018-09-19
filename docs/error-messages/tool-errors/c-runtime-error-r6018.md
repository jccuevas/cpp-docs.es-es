---
title: C Runtime Error R6018 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6018
dev_langs:
- C++
helpviewer_keywords:
- R6018
ms.assetid: f6dd40d1-a119-4d8b-b39e-97350ea23349
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9265c54175236d96391c64e343771c896de1c744
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031722"
---
# <a name="c-runtime-error-r6018"></a>C Runtime Error R6018

error inesperado en el montón

> [!NOTE]
>  Si encuentra este mensaje de error al ejecutar una aplicación, la aplicación se cerró porque tiene un problema interno. Hay varias razones posibles para este error, pero a menudo se debe a un defecto en el código de la aplicación.
>
>  Puede intentar seguir estos pasos para corregir este error:
>
>  -   Use la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para reparar o reinstalar el programa.
> -   Comprobar **Windows Update** en el **Panel de Control** las actualizaciones de software.
> -   Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

El programa encontró un error inesperado mientras se realiza una operación de administración de memoria.

Este error suele producirse si el programa modifica sin darse cuenta los datos del montón de tiempo de ejecución. Sin embargo, también puede deberse a un error interno en el tiempo de ejecución o el código del sistema operativo.

Para corregir este problema, compruebe si hay errores de daños del montón en el código. Para obtener más información y ejemplos, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). A continuación, compruebe que está usando los archivos redistribuibles más recientes para la implementación de la aplicación. Para obtener información, consulte [implementación en Visual C++](../../ide/deployment-in-visual-cpp.md).