---
title: R6026 de Error de tiempo de ejecución de C | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6026
dev_langs:
- C++
helpviewer_keywords:
- R6026
ms.assetid: 7ea751f8-fc20-46ab-99ef-84c95ca0b6b4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7c8bea41b946db67ce24a52393d87873926f3f8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="c-runtime-error-r6026"></a>R6026 de Error de tiempo de ejecución de C
No hay espacio suficiente para la inicialización de stdio  
  
> [!NOTE]
>  Si aparece este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque tiene un problema de memoria interna. Hay varias razones posibles para este error, pero normalmente está provocada por una condición de muy poca memoria. También puede deberse a un error en la aplicación, por daños en las bibliotecas de Visual C++ que utiliza o por un controlador.  
>   
>  Puede intentar seguir estos pasos para corregir este error:  
>   
>  -   Cierre otras aplicaciones en ejecución o reinicie el equipo para liberar memoria.  
> -   Use la **aplicaciones y características** o **programas y características** página en el **el Panel de Control** para reparar o reinstalar el programa.  
> -   Si la aplicación estaba funcionando antes de una instalación reciente de otra aplicación o controlador, utilice la **aplicaciones y características** o **programas y características** página en el **el Panel de Control** para quitar el nueva aplicación o el controlador e inténtelo de nuevo la aplicación.  
> -   Use la **aplicaciones y características** o **programas y características** página en el **el Panel de Control** para reparar o reinstalar todas las copias de Microsoft Visual C++ Redistributable.  
> -   Comprobar **Windows Update** en el **el Panel de Control** las actualizaciones de software.  
> -   Busque una versión actualizada de la aplicación. Si el problema continúa, póngase en contacto con el proveedor de la aplicación.  
  
 **Información para programadores**  
  
 Este error se produce cuando no hay suficiente memoria libre disponible para inicializar la compatibilidad de E/S estándar en el tiempo de ejecución de C. Este error suele producirse al iniciar la aplicación. Compruebe que la aplicación y los controladores y los archivos DLL que carga no esté dañado el montón en el inicio.