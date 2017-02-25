---
title: "C&#243;mo: Depurar una versi&#243;n de lanzamiento | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "depurar [C++], versiones de lanzamiento"
  - "versiones de lanzamiento, depurar"
ms.assetid: d333e4d1-4e6c-4384-84a9-cb549702da25
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# C&#243;mo: Depurar una versi&#243;n de lanzamiento
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Puede depurar una versión de lanzamiento de una aplicación.  
  
### Para depurar una versión de lanzamiento  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el nodo **C\/C\+\+**.  Establezca **Formato de la información de depuración** en [Compatible con C7 \(\/Z7\)](../../build/reference/z7-zi-zi-debug-information-format.md) o **Base de datos de programa \(\/Zi\)**.  
  
3.  Expanda **Vinculador** y haga clic en el nodo **General**.  Establezca **Habilitar vinculación incremental** en [No \(\/INCREMENTAL:NO\)](../../build/reference/incremental-link-incrementally.md).  
  
4.  Seleccione el nodo **Depuración**.  Establezca **Generar información de depuración** en [Sí \(\/DEBUG\)](../../build/reference/debug-generate-debug-info.md).  
  
5.  Seleccione el nodo **Optimización**.  Establezca **Referencias** en [\/OPT:REF](../../build/reference/opt-optimizations.md) y **Habilitar plegamiento de COMDAT** en [\/OPT:ICF](../../build/reference/opt-optimizations.md).  
  
6.  Ahora ya puede depurar la aplicación de la versión de lanzamiento.  Para detectar un problema, examine el código \(o use la depuración Just\-In\-Time\) hasta que encuentre dónde se produce el error y, a continuación, identifique cuáles son los parámetros o el código incorrectos.  
  
     Si una aplicación funciona en una versión de depuración pero produce errores en una versión de lanzamiento, quizás alguna de las optimizaciones del compilador exponga un defecto en el código fuente.  Para aislar el problema, debe deshabilitar las optimizaciones seleccionadas de cada archivo de código fuente hasta encontrar el archivo y la optimización que provocan el problema. \(Para agilizar el proceso, puede dividir los archivos en dos grupos, deshabilitar la optimización en uno de ellos y, si encuentra un problema en un grupo, seguir dividiéndolo hasta que aísle el archivo con el problema\).  
  
     Puede usar [\/RTC](../../build/reference/rtc-run-time-error-checks.md) para tratar de exponer este tipo de errores en las versiones de depuración.  
  
     Para obtener más información, vea [Optimizar el código](../../build/reference/optimizing-your-code.md).  
  
## Vea también  
 [Solucionar problemas de versiones de lanzamiento](../../build/reference/fixing-release-build-problems.md)