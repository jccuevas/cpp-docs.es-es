---
title: Compilador advertencia (nivel 1) C4655 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 6011bf3a2a3bf1718fc15823f2541f49306857c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283268"
---
# <a name="compiler-warning-level-1-c4655"></a>Advertencia del compilador (nivel 1) C4655
**'**   
 ***símbolo de* ': tipo de variable es nuevo desde la última compilación o se define de forma diferente en otra ubicación**  
  
 Ha cambiado o agregado un nuevo tipo de datos desde la última compilación correcta. La función Editar y continuar no admite cambios en los tipos de datos existentes.  
  
 Esta advertencia va seguida de un [Error irrecuperable C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md). Para obtener más información, consulte [Cambios admitidos en el código](/visualstudio/debugger/supported-code-changes-cpp).  
  
### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>Para quitar la advertencia sin terminar la sesión de depuración actual  
  
1.  Cambie el tipo de datos a su estado anterior al error.  
  
2.  En el menú **Depurar** , elija **Aplicar cambios en el código**.  
  
### <a name="to-remove-this-warning-without-changing-your-source-code"></a>Para quitar la advertencia sin cambiar el código fuente  
  
1.  En el menú **Depurar** , elija **Detener depuración**.  
  
2.  En el menú **Compilar** , elija **Compilar**.