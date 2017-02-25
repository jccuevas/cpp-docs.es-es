---
title: "/GT (Admitir el almacenamiento local de subprocesos para fibra) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.EnableFiberSafeOptimizations"
  - "/gt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/GT (opción del compilador) [C++]"
  - "almacenamiento local de subprocesos seguro para fibras (opción del compilador de) [C++]"
  - "GT (opción del compilador) [C++]"
  - "-GT (opción del compilador) [C++]"
  - "almacenamiento local de subprocesos estáticos y seguridad para fibras"
  - "almacenamiento local de subprocesos"
ms.assetid: 071fec79-c701-432b-9970-457344133159
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /GT (Admitir el almacenamiento local de subprocesos para fibra)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Admite la seguridad de fibras para los datos asignados mediante almacenamiento local de subprocesos estáticos, es decir, datos asignados con `__declspec(thread)`.  
  
## Sintaxis  
  
```  
/GT  
```  
  
## Comentarios  
 Las referencias a los datos declarados con `__declspec(thread)` se realizan mediante una matriz TLS \(Thread\-Local Storage, Almacenamiento local de subprocesos\).  La matriz TLS contiene direcciones que el sistema mantiene para cada subproceso.  Cada dirección de la matriz suministra la ubicación de los datos de almacenamiento local de subprocesos.  
  
 Una fibra es un objeto de poca complejidad compuesto por una pila y un contexto de registros, y puede programarse en varios subprocesos.  Una fibra puede ejecutarse en cualquier subproceso.  Dado que una fibra se puede suspender y reiniciar más adelante en otro subproceso, la dirección de la matriz TLS no debe almacenarse en memoria caché ni optimizarse como una subexpresión común a través de una llamada de función \(vea la opción [\/Og \(optimizaciones globales\)](../../build/reference/og-global-optimizations.md) para obtener información detallada\).  **\/GT** impide esta clase de optimizaciones.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Optimización**.  
  
4.  Modifique la propiedad **Habilitar optimizaciones para fibra**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFiberSafeOptimizations%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)