---
title: "Cómo: depurar una versión de lanzamiento | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], release builds
- release builds, debugging
ms.assetid: d333e4d1-4e6c-4384-84a9-cb549702da25
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 31113d9a5935536ac10b22c7b5f5af27b0d29970
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-debug-a-release-build"></a>Cómo: Depurar una versión de lanzamiento
Puede depurar una versión de lanzamiento de una aplicación.  
  
### <a name="to-debug-a-release-build"></a>Para depurar una versión de lanzamiento  
  
1.  Abra la **páginas de propiedades** cuadro de diálogo para el proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **C/C++** nodo. Establecer **formato de información de depuración** a [compatible con C7 (/ Z7)](../../build/reference/z7-zi-zi-debug-information-format.md) o **base de datos de programa (/Zi)**.  
  
3.  Expanda **vinculador** y haga clic en el **General** nodo. Establecer **habilitar vinculación Incremental** a [No (/ INCREMENTAL: NO)](../../build/reference/incremental-link-incrementally.md).  
  
4.  Seleccione el **depuración** nodo. Establecer **generar información de depuración** a [Sí (/Debug)](../../build/reference/debug-generate-debug-info.md).  
  
5.  Seleccione el **optimización** nodo. Establecer **referencias** a [/OPT: ref](../../build/reference/opt-optimizations.md) y **Habilitar plegamiento de COMDAT** a [/OPT: ICF](../../build/reference/opt-optimizations.md).  
  
6.  Ahora puede depurar la aplicación de compilación de versión. Para buscar un problema, paso a través del código (o la depuración Just-In-Time de uso) hasta que encuentre dónde se produce el error y, a continuación, determinar los parámetros incorrectos o código.  
  
     Si una aplicación funciona en una compilación de depuración, pero se produce un error en una versión de lanzamiento, una de las optimizaciones del compilador puede exponer un defecto en el código fuente. Para aislar el problema, deshabilite las optimizaciones seleccionadas de cada archivo de código fuente hasta encontrar el archivo y la optimización que está causando el problema. (Para acelerar el proceso, puede dividir los archivos en dos grupos, deshabilitar la optimización en un grupo y cuando encuentre un problema en un grupo, seguir dividiéndolo hasta que aísle el problema al archivo.)  
  
     Puede usar [/RTC](../../build/reference/rtc-run-time-error-checks.md) para tratar de exponer este tipo de errores en las compilaciones de depuración.  
  
     Para obtener más información, consulte [optimizar el código](../../build/reference/optimizing-your-code.md).  
  
## <a name="see-also"></a>Vea también  
 [Solucionar problemas de versiones de lanzamiento](../../build/reference/fixing-release-build-problems.md)