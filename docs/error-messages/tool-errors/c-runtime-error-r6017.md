---
title: R6017 de Error de tiempo de ejecución de C | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6017
dev_langs:
- C++
helpviewer_keywords:
- R6017
ms.assetid: df3ec5f5-6771-4648-ba06-0e26c6a1cc6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f726f1e01acc20899085f8f1b84f74265843bbd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302729"
---
# <a name="c-runtime-error-r6017"></a>R6017 de Error de tiempo de ejecución de C
error inesperado de bloqueo multiproceso  
  
> [!NOTE]
>  Si aparece este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque tiene un problema interno. Hay varias razones posibles para este error, pero normalmente se deriva de un defecto en el código de la aplicación.  
>   
>  Puede intentar seguir estos pasos para corregir este error:  
>   
>  -   Use la **aplicaciones y características** o **programas y características** página en el **el Panel de Control** para reparar o reinstalar el programa.  
> -   Comprobar **Windows Update** en el **el Panel de Control** las actualizaciones de software.  
> -   Busque una versión actualizada de la aplicación. Si el problema continúa, póngase en contacto con el proveedor de la aplicación.  
  
 **Información para programadores**  
  
 El proceso ha recibido un error inesperado al intentar obtener acceso a un bloqueo de multiproceso de C en tiempo de ejecución en un recurso del sistema. Este error suele producirse si el proceso modifica sin darse cuenta los datos del montón en tiempo de ejecución. Sin embargo, también puede deberse a un error interno en la biblioteca de tiempo de ejecución o el código del sistema operativo.  
  
 Para corregir este problema, busque errores de daños del montón en el código. Para obtener más información y ejemplos, vea [detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details). A continuación, compruebe que está usando los redistribuibles más recientes para su implementación de aplicación. Para obtener información, consulte [implementación en Visual C++](../../ide/deployment-in-visual-cpp.md).