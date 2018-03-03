---
title: "R6008 de Error de tiempo de ejecución de C | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- R6008
dev_langs:
- C++
helpviewer_keywords:
- R6008
ms.assetid: f0f304fc-709a-4843-bc7e-bad1ae0d1649
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 86b64f97768359b95d2c5e2003cfb5b95a2aac71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6008"></a>R6008 de Error de tiempo de ejecución de C
No hay espacio suficiente para los argumentos  
  
> [!NOTE]
>  Si aparece este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque tiene un problema de memoria interna. Hay varias razones posibles para este error, pero a menudo está provocada por una condición de memoria muy baja, demasiada memoria usada por las variables de entorno o un error en el programa.  
>   
>  Puede intentar seguir estos pasos para corregir este error:  
>   
>  -   Cierre otras aplicaciones en ejecución o reinicie el equipo para liberar memoria.  
> -   Reducir el número y tamaño de los argumentos de línea de comandos a la aplicación.  
> -   Use la **aplicaciones y características** o **programas y características** página en el **el Panel de Control** para reparar o reinstalar el programa.  
> -   Comprobar **Windows Update** en el **el Panel de Control** las actualizaciones de software.  
> -   Busque una versión actualizada de la aplicación. Si el problema continúa, póngase en contacto con el proveedor de la aplicación.  
  
 **Información para programadores**  
  
 Hubo memoria suficiente para cargar el programa pero no hay suficiente memoria para crear el **argv** matriz. Esto puede deberse a condiciones de muy poca memoria o extraordinariamente grandes líneas de comandos o el uso de variables de entorno. Considere una de las siguientes soluciones:  
  
-   Aumente la cantidad de memoria disponible para el programa.  
  
-   Reducir el número y tamaño de los argumentos de línea de comandos.  
  
-   Reducir el tamaño del entorno quitando variables innecesarias.