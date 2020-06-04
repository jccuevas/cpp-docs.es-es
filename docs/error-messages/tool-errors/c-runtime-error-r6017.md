---
title: Error en tiempo de ejecución de C R6017
ms.date: 11/04/2016
f1_keywords:
- R6017
helpviewer_keywords:
- R6017
ms.assetid: df3ec5f5-6771-4648-ba06-0e26c6a1cc6a
ms.openlocfilehash: 2d868939425c11f13dffd84e28c1afee45e3b11a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197307"
---
# <a name="c-runtime-error-r6017"></a>Error en tiempo de ejecución de C R6017

error inesperado de bloqueo multiproceso

> [!NOTE]
> Si encuentra este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque tiene un problema interno. Hay varias razones posibles para este error, pero a menudo se debe a un defecto en el código de la aplicación.
>
> Puede intentar seguir estos pasos para corregir este error:
>
> - Use la página **aplicaciones y características** o **programas y características** del **Panel de control** para reparar o reinstalar el programa.
> - Compruebe **Windows Update** en el **Panel de control** para las actualizaciones de software.
> - Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

El proceso recibió un error inesperado al intentar obtener acceso a un bloqueo multiproceso en tiempo de ejecución de C en un recurso del sistema. Este error suele producirse si el proceso modifica accidentalmente los datos del montón en tiempo de ejecución. Sin embargo, también puede deberse a un error interno en la biblioteca en tiempo de ejecución o en el código del sistema operativo.

Para corregir este problema, compruebe si hay errores de daños en el montón en el código. Para obtener más información y ejemplos, vea [detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details). A continuación, compruebe que está usando los redistribuibles más recientes para la implementación de la aplicación. Para obtener más información, consulte [implementación C++en Visual ](../../windows/deployment-in-visual-cpp.md).
