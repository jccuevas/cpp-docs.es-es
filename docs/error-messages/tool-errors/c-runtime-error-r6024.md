---
title: Error en tiempo de ejecución de C R6024
ms.date: 11/04/2016
f1_keywords:
- R6024
helpviewer_keywords:
- R6024
ms.assetid: 0fb11c0f-9b81-4cab-81bd-4785742946a5
ms.openlocfilehash: de89d2e9e2b34f40b906a5dacca4179eade23f7e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197202"
---
# <a name="c-runtime-error-r6024"></a>Error en tiempo de ejecución de C R6024

no hay espacio suficiente para _onexit tabla/AtExit

> [!NOTE]
> Si encuentra este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque tiene un problema de memoria interna. Normalmente, este error se debe a una condición de memoria extremadamente baja o, en raras ocasiones, a un error en el programa o a C++ daños en las bibliotecas visuales que usa.
>
> Puede intentar seguir estos pasos para corregir este error:
>
> - Cierre otras aplicaciones en ejecución o reinicie el equipo para liberar memoria.
> - Use la página **aplicaciones y características** o **programas y características** del **Panel de control** para reparar o reinstalar el programa.
> - Use la página **aplicaciones y características** o **programas y características** del **Panel de control** para reparar o reinstalar todas las copias del paquete redistribuible de Microsoft Visual. C++
> - Compruebe **Windows Update** en el **Panel de control** para las actualizaciones de software.
> - Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

Este error se produce porque no hay memoria disponible para la función `_onexit` o `atexit`. Este error se debe a una condición de memoria insuficiente. Puede considerar la asignación previa de búferes en el inicio de la aplicación para ayudar a guardar los datos de usuario y realizar una salida limpia de la aplicación en condiciones de memoria insuficiente.
