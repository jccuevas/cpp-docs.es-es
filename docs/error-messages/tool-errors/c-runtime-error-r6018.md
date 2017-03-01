---
title: "R6018 de Error de tiempo de ejecución de C | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- R6018
dev_langs:
- C++
helpviewer_keywords:
- R6018
ms.assetid: f6dd40d1-a119-4d8b-b39e-97350ea23349
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 6cad5222fb0d97594d5b13b5cf8903eb2934ee88
ms.openlocfilehash: 07aa2d06b990f0eed1f089b677e55c4d2e78a01e
ms.lasthandoff: 02/24/2017

---
# <a name="c-runtime-error-r6018"></a>R6018 de Error de tiempo de ejecución de C
error inesperado en el montón  
  
> [!NOTE]
>  Si aparece este mensaje de error al ejecutar una aplicación, la aplicación se cerró porque tiene un problema interno. Hay varias razones posibles para este error, pero a menudo se debe a un defecto en el código de la aplicación.  
>   
>  Puede intentar seguir estos pasos para corregir este error:  
>   
>  -   Utilice la **las aplicaciones y características** o **programas y características** página en el **Panel de Control** para reparar o reinstalar el programa.  
> -   Comprobar **Windows Update** en el **Panel de Control** las actualizaciones de software.  
> -   Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.  
  
 **Información para programadores**  
  
 El sistema encontró un error inesperado mientras se realiza una operación de administración de memoria.  
  
 Este error suele producirse si el programa modifica sin darse cuenta los datos del montón de tiempo de ejecución. Sin embargo, también puede deberse a un error interno en el tiempo de ejecución o el código del sistema operativo.  
  
 Para corregir este problema, busque errores de daños del montón en el código. Para obtener más información y ejemplos, vea [detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details). A continuación, compruebe que está utilizando los redistribuibles más recientes para la implementación de la aplicación. Para obtener información, consulte [implementación en Visual C++](../../ide/deployment-in-visual-cpp.md).
