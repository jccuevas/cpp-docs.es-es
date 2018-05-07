---
title: Error de tiempo de ejecución de C R6002 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6002
dev_langs:
- C++
helpviewer_keywords:
- R6002
ms.assetid: 8fbbe65a-9c43-459e-8342-e1f6d1cef7d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50a970ecea4fdd7d397c09672b0548be947cab1e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="c-runtime-error-r6002"></a>Error de tiempo de ejecución de C R6002
compatibilidad de punto flotante no cargado  
  
 No se ha vinculado la biblioteca de punto flotante es necesaria.  
  
> [!NOTE]
>  Si aparece este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque tiene un problema interno. Hay varias razones posibles para este error, pero normalmente se deriva de un defecto en el código de la aplicación o al intentar ejecutar una aplicación que no se creó para el procesador del equipo en particular.  
>   
>  Puede intentar seguir estos pasos para corregir este error:  
>   
>  -   Use la **aplicaciones y características** o **programas y características** página en el **el Panel de Control** para reparar o reinstalar el programa.  
> -   Comprobar **Windows Update** en el **el Panel de Control** las actualizaciones de software.  
> -   Busque una versión actualizada de la aplicación. Si el problema continúa, póngase en contacto con el proveedor de la aplicación.  
  
 **Información para programadores**  
  
 Este error puede producirse en la aplicación cuando no se ha vinculado la biblioteca de punto flotante. Busque una de estas causas:  
  
-   Una cadena de formato para un `printf_s` o `scanf_s` función contiene una especificación de formato de punto flotante y el programa no contiene los valores de punto flotante o variables. Para corregir este problema, utilice un argumento de punto flotante que corresponda a la especificación de formato de punto flotante o realizar una asignación de punto flotante en otra parte del programa. Esto hace que compatibilidad de punto flotante que se va a cargar.  
  
-   El compilador minimiza el tamaño de un programa cargando la compatibilidad de punto flotante solo cuando sea necesario. El compilador no puede detectar operaciones de punto flotante o las especificaciones de formato de punto flotante en cadenas de formato, por lo que no se carga las rutinas de punto flotante necesarias. Para corregir este problema, utilice una especificación de formato de punto flotante y proporcionar un argumento de punto flotante o realizar una asignación de punto flotante en otra parte del programa. Esto hace que compatibilidad de punto flotante que se va a cargar.  
  
-   En un programa de varios lenguajes, se especificó una biblioteca C antes de una biblioteca de FORTRAN cuando se vinculó el programa. Volver a vincular y especifique la biblioteca de C última.