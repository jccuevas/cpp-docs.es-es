---
title: "R6028 de Error de tiempo de ejecución de C | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6028
dev_langs: C++
helpviewer_keywords: R6028
ms.assetid: 81e99079-4388-4244-a4f7-4641c508871c
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7d1d7260cd2416e9d157931b037cfd7fbe4c0081
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6028"></a>R6028 de Error de tiempo de ejecución de C
no puede inicializar el montón  
  
> [!NOTE]
>  Si aparece este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque tiene un problema de memoria interna. Hay muchas razones posibles para este error, pero a menudo se derivan de una condición de memoria muy baja, un error en el programa, como controladores de hardware defectuoso.  
>   
>  Puede intentar seguir estos pasos para corregir este error:  
>   
>  -   Cierre otras aplicaciones en ejecución o reinicie el equipo para liberar memoria.  
> -   Use la **aplicaciones y características** o **programas y características** página en el **el Panel de Control** para reparar o reinstalar el programa.  
> -   Si la aplicación estaba funcionando antes de una instalación reciente de otra aplicación o controlador, utilice la **aplicaciones y características** o **programas y características** página en el **el Panel de Control** para quitar el nueva aplicación o el controlador e inténtelo de nuevo la aplicación.  
> -   Compruebe el sitio Web de su proveedor de hardware o **Windows Update** en el **el Panel de Control** para las actualizaciones de software y los controladores.  
> -   Busque una versión actualizada de la aplicación. Si el problema continúa, póngase en contacto con el proveedor de la aplicación.  
  
 **Información para programadores**  
  
 Este error aparece cuando el sistema operativo no puede crear el almacén de memoria para la aplicación. Específicamente, la biblioteca en tiempo de ejecución de C (CRT) ha llamado a la función `HeapCreate` de Win32, que ha devuelto NULL, lo que indica un error.  
  
 Si este error se produce durante el inicio de la aplicación, es posible que el sistema no pueda atender las solicitudes de montón porque se carguen controladores defectuosos. Compruebe en Windows Update o en el sitio web del distribuidor de hardware si hay controladores actualizados.