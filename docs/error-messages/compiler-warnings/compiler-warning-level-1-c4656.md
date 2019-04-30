---
title: Advertencia del compilador (nivel 1) C4656
ms.date: 11/04/2016
f1_keywords:
- C4656
helpviewer_keywords:
- C4656
ms.assetid: b5aaef74-2320-4345-a6ae-b813881a491c
ms.openlocfilehash: 4285ce20f6131c2503304ed1bdb1bde02b2efcec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375254"
---
# <a name="compiler-warning-level-1-c4656"></a>Advertencia del compilador (nivel 1) C4656

'símbolo': tipo de datos es nuevo o ha cambiado desde la última compilación o se define de forma distinta en otro lugar

El usuario agrega o cambia un tipo de datos, que se convierte en nuevo para el código fuente desde la última compilación correcta. La función Editar y continuar no admite cambios en los tipos de datos existentes.

Esta advertencia siempre irá seguida del [Error irrecuperable C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md). Para obtener más información, consulte [Cambios admitidos en el código](/visualstudio/debugger/supported-code-changes-cpp).

### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>Para quitar la advertencia sin terminar la sesión de depuración actual

1. Cambie el tipo de datos a su estado anterior al error.

1. En el menú **Depurar** , elija **Aplicar cambios en el código**.

### <a name="to-remove-this-error-without-changing-your-source-code"></a>Para quitar este error sin cambiar el código fuente

1. En el menú **Depurar** , elija **Detener depuración**.

1. En el menú **Compilar** , elija **Compilar**.