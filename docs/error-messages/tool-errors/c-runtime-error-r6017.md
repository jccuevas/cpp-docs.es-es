---
title: "R6017 de Error de tiempo de ejecución de C | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- R6017
dev_langs:
- C++
helpviewer_keywords:
- R6017
ms.assetid: df3ec5f5-6771-4648-ba06-0e26c6a1cc6a
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
ms.openlocfilehash: 903d440dbedbe704ae28be643337619ca1e09c69
ms.lasthandoff: 02/24/2017

---
# <a name="c-runtime-error-r6017"></a>R6017 de Error de tiempo de ejecución de C
error inesperado de bloqueo de multiproceso  
  
> [!NOTE]
>  Si aparece este mensaje de error al ejecutar una aplicación, la aplicación se cerró porque tiene un problema interno. Hay varias razones posibles para este error, pero a menudo se debe a un defecto en el código de la aplicación.  
>   
>  Puede intentar seguir estos pasos para corregir este error:  
>   
>  -   Utilice la **las aplicaciones y características** o **programas y características** página en el **Panel de Control** para reparar o reinstalar el programa.  
> -   Comprobar **Windows Update** en el **Panel de Control** las actualizaciones de software.  
> -   Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.  
  
 **Información para programadores**  
  
 El proceso ha recibido un error inesperado al intentar obtener acceso a un bloqueo de multiproceso de C en tiempo de ejecución en un recurso del sistema. Este error suele producirse si el proceso modifica sin darse cuenta los datos del montón en tiempo de ejecución. Sin embargo, también puede deberse a un error interno en la biblioteca de tiempo de ejecución o el código del sistema operativo.  
  
 Para corregir este problema, busque errores de daños del montón en el código. Para obtener más información y ejemplos, vea [detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details). A continuación, compruebe que está utilizando los redistribuibles más recientes para la implementación de la aplicación. Para obtener información, consulte [implementación en Visual C++](../../ide/deployment-in-visual-cpp.md).
