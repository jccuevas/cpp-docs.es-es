---
title: Compilador advertencia (nivel 1) C4657 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4657
dev_langs:
- C++
helpviewer_keywords:
- C4657
ms.assetid: eb750050-cea6-4ead-b80c-d5dcd4971cfc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0eb3701496b2300aa52f4734cb2d1ea6e236ad0a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098840"
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