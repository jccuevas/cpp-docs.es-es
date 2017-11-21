---
title: "R6032 de Error de tiempo de ejecución de C | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6032
dev_langs: C++
helpviewer_keywords: R6032
ms.assetid: 52092a63-cc51-444a-bfc3-fad965a3558e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: afe6ba23315dfd00114e3d2b956a19cadf6342c3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="c-runtime-error-r6032"></a>R6032 de Error de tiempo de ejecución de C
No hay espacio suficiente para obtener información de configuración regional  
  
> [!NOTE]
>  Si aparece este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque tiene un problema de memoria interna. Hay varias razones posibles para este error, pero a menudo está provocada por una condición de muy poca memoria o a un error en el programa.  
>   
>  Puede intentar seguir estos pasos para corregir este error:  
>   
>  -   Cierre otras aplicaciones en ejecución o reinicie el equipo para liberar memoria.  
> -   Use la **aplicaciones y características** o **programas y características** página en el **el Panel de Control** para reparar o reinstalar el programa.  
> -   Comprobar **Windows Update** en el **el Panel de Control** las actualizaciones de software.  
> -   Busque una versión actualizada de la aplicación. Si el problema continúa, póngase en contacto con el proveedor de la aplicación.  
  
 **Información para programadores**  
  
 El tiempo de ejecución mantiene información acerca de la configuración regional de cada subproceso para que pueden procesar llamadas a funciones dependientes de la configuración regional. Si se produce un error en la asignación de memoria para esta información, el tiempo de ejecución es no puede continuar porque hay demasiados de sus funciones básicas dependen de él.