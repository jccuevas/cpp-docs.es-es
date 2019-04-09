---
title: C Runtime Error R6017
ms.date: 11/04/2016
f1_keywords:
- R6017
helpviewer_keywords:
- R6017
ms.assetid: df3ec5f5-6771-4648-ba06-0e26c6a1cc6a
ms.openlocfilehash: 45f3b07f540cb72a955b19420130a5a806b750d7
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "58774703"
---
# <a name="c-runtime-error-r6017"></a>C Runtime Error R6017

error inesperado de bloqueo de multiproceso

> [!NOTE]
> Si encuentra este mensaje de error al ejecutar una aplicación, la aplicación se cerró porque tiene un problema interno. Hay varias razones posibles para este error, pero a menudo se debe a un defecto en el código de la aplicación.
>
> Puede intentar seguir estos pasos para corregir este error:
>
> - Use la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para reparar o reinstalar el programa.
> - Comprobar **Windows Update** en el **Panel de Control** las actualizaciones de software.
> - Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

El proceso recibe un error inesperado al intentar obtener acceso a un bloqueo multiproceso de C en tiempo de ejecución en un recurso del sistema. Este error suele producirse si el proceso de forma inadvertida modifica los datos del montón en tiempo de ejecución. Sin embargo, también puede deberse a un error interno en la biblioteca de tiempo de ejecución o el código del sistema operativo.

Para corregir este problema, compruebe si hay errores de daños del montón en el código. Para obtener más información y ejemplos, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). A continuación, compruebe que está usando los archivos redistribuibles más recientes para la implementación de la aplicación. Para obtener información, consulte [implementación en Visual C++](../../windows/deployment-in-visual-cpp.md).