---
title: "R6027 de Error de tiempo de ejecución de C | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- R6027
dev_langs:
- C++
helpviewer_keywords:
- R6027
ms.assetid: c06a62b3-08d9-4bf5-bcad-8340ec552f69
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 080b5cdf2e68889e7d11fe14f20524f9cced03c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6027"></a>R6027 de Error de tiempo de ejecución de C
No hay espacio suficiente para la inicialización de lowio  
  
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
  
 Este error se produce cuando no hay suficiente memoria libre disponible para inicializar la compatibilidad de E/S de bajo nivel en el tiempo de ejecución de C. Este error suele producirse al iniciar la aplicación. Compruebe que la aplicación y los controladores y los archivos DLL que carga no esté dañado el montón en el inicio.