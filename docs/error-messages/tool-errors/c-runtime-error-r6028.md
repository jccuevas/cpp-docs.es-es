---
title: R6028 de Error de tiempo de ejecución de C | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6028
dev_langs:
- C++
helpviewer_keywords:
- R6028
ms.assetid: 81e99079-4388-4244-a4f7-4641c508871c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b978d1d9165fd48be9d0ce31aa72092fc660dbd9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297828"
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