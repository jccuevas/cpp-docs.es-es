---
title: R6031 de Error en tiempo de ejecución de C | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6031
dev_langs:
- C++
helpviewer_keywords:
- R6031
ms.assetid: 805d4cd1-cb2f-43fe-87e6-e7bd5b7329c5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66d75fb0095b1de0fe1572d8c946823a89791740
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33303951"
---
# <a name="c-runtime-error-r6031"></a>R6031 de Error en tiempo de ejecución de C
Intento de inicializar CRT más de una vez. Esto indica un error en la aplicación.  
  
> [!NOTE]
>  Si aparece este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque tiene un problema interno. Esto puede deberse errores en la aplicación o a un error en un complemento o una extensión que usa la aplicación.  
>   
>  Puede intentar seguir estos pasos para corregir este error:  
>   
>  -   Use la **aplicaciones y características** o **programas y características** página en el **el Panel de Control** para reparar o reinstalar el programa.  
> -   Use la **aplicaciones y características** o **programas y características** página en el **el Panel de Control** para quitar, reparar o reinstalar los programas de complemento o extensión utilizados por la aplicación.  
> -   Comprobar **Windows Update** en el **el Panel de Control** las actualizaciones de software.  
> -   Busque una versión actualizada de la aplicación. Si el problema continúa, póngase en contacto con el proveedor de la aplicación.  
  
 **Información para programadores**  
  
 Este diagnóstico indica que se estaban ejecutando instrucciones MSIL durante el bloqueo del cargador. Para obtener más información, consulte [inicialización de ensamblados mixtos](../../dotnet/initialization-of-mixed-assemblies.md).