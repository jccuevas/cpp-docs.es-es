---
title: "R6024 de Error de tiempo de ejecución de C | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- R6024
dev_langs:
- C++
helpviewer_keywords:
- R6024
ms.assetid: 0fb11c0f-9b81-4cab-81bd-4785742946a5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 98d52a7d143a1c65caee3fe68902e3a25b3a5f4c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6024"></a>R6024 de Error de tiempo de ejecución de C
No hay suficiente espacio para la tabla _onexit/atexit  
  
> [!NOTE]
>  Si aparece este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque tiene un problema de memoria interna. Este error ocurre normalmente por una condición de memoria muy baja, en contadas ocasiones, por un error en el programa o por daños en las bibliotecas de Visual C++ que utiliza.  
>   
>  Puede intentar seguir estos pasos para corregir este error:  
>   
>  -   Cierre otras aplicaciones en ejecución o reinicie el equipo para liberar memoria.  
> -   Use la **aplicaciones y características** o **programas y características** página en el **el Panel de Control** para reparar o reinstalar el programa.  
> -   Use la **aplicaciones y características** o **programas y características** página en el **el Panel de Control** para reparar o reinstalar todas las copias de Microsoft Visual C++ Redistributable.  
> -   Comprobar **Windows Update** en el **el Panel de Control** las actualizaciones de software.  
> -   Busque una versión actualizada de la aplicación. Si el problema continúa, póngase en contacto con el proveedor de la aplicación.  
  
 **Información para programadores**  
  
 Este error se produce porque no había ninguna memoria disponible para la `_onexit` o `atexit` (función). Este error aparece cuando una condición de memoria insuficiente. Puede considerar búferes asignar previamente al iniciar la aplicación para ayudar a guardar los datos de usuario y la realización de una aplicación limpia salir en condiciones de memoria insuficiente.