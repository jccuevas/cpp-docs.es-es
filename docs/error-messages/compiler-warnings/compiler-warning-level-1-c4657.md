---
title: Advertencia del compilador (nivel 1) C4657
ms.date: 11/04/2016
f1_keywords:
- C4657
helpviewer_keywords:
- C4657
ms.assetid: eb750050-cea6-4ead-b80c-d5dcd4971cfc
ms.openlocfilehash: 6cc049d99339a6f19ca86cd5c7a10f062a1451a9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199505"
---
# <a name="compiler-warning-level-1-c4657"></a>Advertencia del compilador (nivel 1) C4657

la expresión requiere un tipo de datos que sea nuevo desde la última compilación

El usuario agrega o cambia un tipo de datos, que se convierte en nuevo para el código fuente desde la última compilación correcta. La función Editar y continuar no admite cambios en los tipos de datos existentes.

Esta advertencia siempre irá seguida del [Error irrecuperable C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md). Para obtener más información, consulte [Cambios admitidos en el código](/visualstudio/debugger/supported-code-changes-cpp).

### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>Para quitar la advertencia sin terminar la sesión de depuración actual

1. Cambie el tipo de datos a su estado anterior al error.

1. En el menú **Depurar** , elija **Aplicar cambios en el código**.

### <a name="to-remove-this-error-without-changing-your-source-code"></a>Para quitar este error sin cambiar el código fuente

1. En el menú **Depurar** , elija **Detener depuración**.

1. En el menú **Compilar** , elija **Compilar**.
