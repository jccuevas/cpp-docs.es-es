---
title: Compilador advertencia (nivel 1) C4656 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4656
dev_langs:
- C++
helpviewer_keywords:
- C4656
ms.assetid: b5aaef74-2320-4345-a6ae-b813881a491c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f342887bc91a48e9446f1403f1722c40b989546d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4656"></a>Advertencia del compilador (nivel 1) C4656
'símbolo': tipo de datos es nueva o ha cambiado desde la última compilación o se define de forma diferente en otra ubicación  
  
 El usuario agrega o cambia un tipo de datos, que se convierte en nuevo para el código fuente desde la última compilación correcta. La función Editar y continuar no admite cambios en los tipos de datos existentes.  
  
 Esta advertencia siempre irá seguida del [Error irrecuperable C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md). Para obtener más información, consulte [Cambios admitidos en el código](/visualstudio/debugger/supported-code-changes-cpp).  
  
### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>Para quitar la advertencia sin terminar la sesión de depuración actual  
  
1.  Cambie el tipo de datos a su estado anterior al error.  
  
2.  En el menú **Depurar** , elija **Aplicar cambios en el código**.  
  
### <a name="to-remove-this-error-without-changing-your-source-code"></a>Para quitar este error sin cambiar el código fuente  
  
1.  En el menú **Depurar** , elija **Detener depuración**.  
  
2.  En el menú **Compilar** , elija **Compilar**.