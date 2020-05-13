---
title: Error irrecuperable C1060
ms.date: 11/04/2016
f1_keywords:
- C1060
helpviewer_keywords:
- C1060
ms.assetid: feaf305c-c84c-4160-b974-50e283412849
ms.openlocfilehash: 83135b77ceb75b4c2b05211260d1aed8fac6777f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320298"
---
# <a name="fatal-error-c1060"></a>Error irrecuperable C1060

espacio de montón insuficiente en el compilador

El sistema operativo o la biblioteca en tiempo de ejecución no pueden satisfacer una solicitud de memoria.

### <a name="to-fix-this-error-try-the-following-possible-solutions"></a>Para corregir este error pruebe las siguientes soluciones

1. Si el compilador también emite errores [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) y [C3859,](../../error-messages/compiler-errors-2/compiler-error-c3859.md)use la opción del compilador [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) para reducir el límite de asignación de memoria. Habrá más espacio de montón disponible para la aplicación si reduce la asignación de memoria restante.

   Si la opción [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) ya está establecida, intente quitarla. El espacio de montón podría agotarse si el límite de asignación de memoria especificado en la opción es demasiado alto. El compilador utiliza un límite predeterminado si quita la opción [/Zm.](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)

1. Si está compilando en una plataforma de 64 bits, utilice el conjunto de herramientas del compilador de 64 bits. Para obtener información, consulte Cómo: Habilitar un conjunto de herramientas [Visual C++](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)de 64 bits en la línea de comandos .

1. En Windows de 32 bits, intente usar el modificador boot.ini [de 3 GB.](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200)

1. Aumente el tamaño del archivo de intercambio de Windows.

1. Cierre los demás programas que se estén ejecutando.

1. Elimine los archivos de inclusión innecesarios.

1. Elimine las variables globales que no son necesarias, por ejemplo, asignando memoria dinámicamente, en lugar de declarar una matriz grande.

1. Elimine las declaraciones que no utilice.

1. Divida el archivo actual en archivos más pequeños.
