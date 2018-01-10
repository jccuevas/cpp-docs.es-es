---
title: -CGTHREADS (subprocesos compilador) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- /CGTHREADS linker option
- -CGTHREADS linker option
- CGTHREADS linker option
ms.assetid: 4b52cfdb-3702-470b-9580-fabeb1417488
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 542e35ecbb5e56ae0d13861b9885936f3b47c9da
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cgthreads-compiler-threads"></a>/CGTHREADS (Subprocesos compilador)
Establece el número de subprocesos cl.exe que se deben usar para la optimización y la generación de código cuando se especifica la generación de código en tiempo de vínculo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/CGTHREADS:[1-8]  
```  
  
## <a name="arguments"></a>Argumentos  
 número  
 El número máximo de subprocesos que debe usar cl.exe, en un intervalo de 1 a 8.  
  
## <a name="remarks"></a>Comentarios  
 El **/CGTHREADS** opción especifica el número máximo de subprocesos que usará cl.exe en paralelo para las fases de optimización y generación de código de la compilación al tiempo de vinculación de generación de código ([/LTCG](../../build/reference/ltcg-link-time-code-generation.md)) es especificado. De forma predeterminada, cl.exe utiliza cuatro subprocesos, como si **/CGTHREADS:4** se especificaron. Si hay más núcleos de procesador disponibles, al aumentar el valor `number`, se pueden mejorar los tiempos de compilación.  
  
 Se pueden especificar varios niveles de paralelismo para una compilación. El modificador de msbuild.exe **maxcpucount** especifica el número de procesos de MSBuild que se pueden ejecutar en paralelo. El [/MP (compilar con varios procesos)](../../build/reference/mp-build-with-multiple-processes.md) marca de compilador especifica el número de procesos de cl.exe que se compilan simultáneamente los archivos de origen. El [/cgthreads](../../build/reference/cgthreads-code-generation-threads.md) opción del compilador especifica el número de subprocesos utilizados por cada proceso de cl.exe. Dado que el procesador no puede ejecutar al mismo tiempo más subprocesos que núcleos de procesador hay, no resulta útil especificar valores mayores en todas estas opciones a la vez, y puede ser contraproducente. Para obtener más información acerca de cómo compilar proyectos en paralelo, vea [compilar varios proyectos en paralelo](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione el **propiedades de configuración**, **vinculador** carpeta.  
  
3.  Seleccione el **línea de comandos** página de propiedades.  
  
4.  Modificar el **opciones adicionales** propiedad para incluir **/CGTHREADS:**`number`, donde `number` es un valor entre 1 y 8 y, a continuación, elija **Aceptar**.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del vinculador](../../build/reference/linker-options.md)   
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)