---
title: "Proyecto de compilación Advertencia PRJ0049 al | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- PRJ0049
ms.assetid: 8b38afa1-e080-4efd-ae89-776cfd044413
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9f87bc7e26fd7cc50defbc086594c92a3ea339ef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-warning-prj0049"></a>Advertencia PRJ0049 al compilar el proyecto
Destino que se hace referencia '\<referencia >' requiere .NET Framework \<MinFrameworkVersion > y no se puede ejecutar en .NET framework de destino de este proyecto  
  
 Las aplicaciones creadas con Visual Studio 2008 pueden especificar qué versión de la [!INCLUDE[dnprdnshort](../../error-messages/tool-errors/includes/dnprdnshort_md.md)] deben tener como destino. Si agrega una referencia a un ensamblado o proyecto que depende de una versión de la [!INCLUDE[dnprdnshort](../../error-messages/tool-errors/includes/dnprdnshort_md.md)] posterior a la versión de destino, se producirá esta advertencia en tiempo de compilación.  
  
### <a name="to-correct-this-warning"></a>Para corregir esta advertencia  
  
1.  Elija una de las siguientes opciones:  
  
    -   Cambiar el marco de destino en el proyecto **páginas de propiedades** cuadro de diálogo para que sea posterior o igual a la versión mínima de marco de trabajo de todos los ensamblados y proyectos. Para obtener más información, consulte [agregar referencias](../../ide/adding-references-in-visual-cpp-projects.md).  
  
    -   Quite la referencia al ensamblado o proyecto que tiene una versión de framework mínima que superen el .NET framework de destino. Estos elementos se marcarán con un icono de advertencia en el proyecto **páginas de propiedades**.  
  
## <a name="see-also"></a>Vea también  
 [Errores y advertencias de compilación del proyecto (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)