---
title: "R6018 de Error de tiempo de ejecución de C | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- R6018
dev_langs:
- C++
helpviewer_keywords:
- R6018
ms.assetid: f6dd40d1-a119-4d8b-b39e-97350ea23349
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0102739bb4fa8961e089d348e1ff93f62fdde6b6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6018"></a>R6018 de Error de tiempo de ejecución de C
error inesperado en el montón  
  
> [!NOTE]
>  Si aparece este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque tiene un problema interno. Hay varias razones posibles para este error, pero normalmente se deriva de un defecto en el código de la aplicación.  
>   
>  Puede intentar seguir estos pasos para corregir este error:  
>   
>  -   Use la **aplicaciones y características** o **programas y características** página en el **el Panel de Control** para reparar o reinstalar el programa.  
> -   Comprobar **Windows Update** en el **el Panel de Control** las actualizaciones de software.  
> -   Busque una versión actualizada de la aplicación. Si el problema continúa, póngase en contacto con el proveedor de la aplicación.  
  
 **Información para programadores**  
  
 El programa encontró un error inesperado mientras se realiza una operación de administración de memoria.  
  
 Este error suele producirse si el programa modifica sin darse cuenta los datos del montón de tiempo de ejecución. Sin embargo, también puede deberse a un error interno en el tiempo de ejecución o el código de sistema operativo.  
  
 Para corregir este problema, busque errores de daños del montón en el código. Para obtener más información y ejemplos, vea [detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details). A continuación, compruebe que está usando los redistribuibles más recientes para su implementación de aplicación. Para obtener información, consulte [implementación en Visual C++](../../ide/deployment-in-visual-cpp.md).