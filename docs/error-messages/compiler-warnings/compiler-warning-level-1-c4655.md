---
title: Advertencia del compilador (nivel 1) C4655
ms.date: 08/27/2018
f1_keywords:
- C4655
helpviewer_keywords:
- C4655
ms.assetid: 540f2c7a-e4a1-49af-84b4-03eeea1bbf41
ms.openlocfilehash: d4c409c2d69099853a872142e05ef0fcda5a7655
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199536"
---
# <a name="compiler-warning-level-1-c4655"></a>Advertencia del compilador (nivel 1) C4655

> '*Symbol*': el tipo de variable es nuevo desde la última compilación o bien se ha definido de forma distinta en otro lugar

## <a name="remarks"></a>Observaciones

Ha cambiado o agregado un nuevo tipo de datos desde la última compilación correcta. La función Editar y continuar no admite cambios en los tipos de datos existentes.

Esta advertencia va seguida de un [Error irrecuperable C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md). Para obtener más información, consulte [Cambios admitidos en el código](/visualstudio/debugger/supported-code-changes-cpp).

### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>Para quitar la advertencia sin terminar la sesión de depuración actual

1. Cambie el tipo de datos a su estado anterior al error.

2. En el menú **Depurar** , elija **Aplicar cambios en el código**.

### <a name="to-remove-this-warning-without-changing-your-source-code"></a>Para quitar la advertencia sin cambiar el código fuente

1. En el menú **Depurar** , elija **Detener depuración**.

2. En el menú **Compilar** , elija **Compilar**.
