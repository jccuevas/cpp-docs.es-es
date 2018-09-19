---
title: Compilador advertencia (nivel 1) C4655 | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4655
dev_langs:
- C++
helpviewer_keywords:
- C4655
ms.assetid: 540f2c7a-e4a1-49af-84b4-03eeea1bbf41
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9600c0fb9b4f03112ebd9cf430e3f833899c5f3c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209106"
---
# <a name="compiler-warning-level-1-c4655"></a>Advertencia del compilador (nivel 1) C4655

> '*símbolo*': tipo de variable es nuevo desde la última compilación o se define de forma distinta en otro lugar

## <a name="remarks"></a>Comentarios

Ha cambiado o agregado un nuevo tipo de datos desde la última compilación correcta. La función Editar y continuar no admite cambios en los tipos de datos existentes.

Esta advertencia va seguida de un [Error irrecuperable C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md). Para obtener más información, consulte [Cambios admitidos en el código](/visualstudio/debugger/supported-code-changes-cpp).

### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>Para quitar la advertencia sin terminar la sesión de depuración actual

1. Cambie el tipo de datos a su estado anterior al error.

2. En el menú **Depurar** , elija **Aplicar cambios en el código**.

### <a name="to-remove-this-warning-without-changing-your-source-code"></a>Para quitar la advertencia sin cambiar el código fuente

1. En el menú **Depurar** , elija **Detener depuración**.

2. En el menú **Compilar** , elija **Compilar**.