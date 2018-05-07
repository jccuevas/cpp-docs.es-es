---
title: R6033 del Error en tiempo de ejecución de C | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6033
dev_langs:
- C++
helpviewer_keywords:
- R6033
ms.assetid: f9cffdc9-81bd-4a64-a698-02762cbd82c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed66dec4f4eb17378c9901439be2ad1449597a93
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="c-runtime-error-r6033"></a>R6033 del Error en tiempo de ejecución de C
Ha intentado usar el código MSIL de este ensamblado durante la inicialización del código nativo. Esto indica un error en la aplicación. Lo más probable es que es el resultado de una llamada a una compilación de MSIL (/ clr) función desde un constructor nativo o desde DllMain.  
  
> [!NOTE]
>  Si aparece este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque tiene un problema interno. Este error puede deberse a un error en la aplicación o a un error en un complemento o una extensión que utiliza.  
>   
>  Puede intentar seguir estos pasos para corregir este error:  
>   
>  -   Use la **aplicaciones y características** o **programas y características** página en el **el Panel de Control** para reparar o reinstalar el programa.  
> -   Use la **aplicaciones y características** o **programas y características** página en el **el Panel de Control** para quitar, reparar o reinstalar las extensiones o complementos.  
> -   Comprobar **Windows Update** en el **el Panel de Control** las actualizaciones de software.  
> -   Busque una versión actualizada de la aplicación. Si el problema continúa, póngase en contacto con el proveedor de la aplicación.  
  
 **Información para programadores**  
  
 Este diagnóstico indica que se estaban ejecutando instrucciones MSIL durante el bloqueo del cargador. Esto puede ocurrir si ha compilado C++ nativo mediante la marca/CLR. Use sólo el indicador/CLR en módulos que contienen código administrado. Para obtener más información, consulte [inicialización de ensamblados mixtos](../../dotnet/initialization-of-mixed-assemblies.md).