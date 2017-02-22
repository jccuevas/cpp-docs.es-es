---
title: "Error PRJ0003 al compilar el proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0003"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0003"
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error PRJ0003 al compilar el proyecto
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Error al generar 'línea de comandos'.  
  
 Un comando, ***línea de comandos***, formado a partir de los datos proporcionados en el cuadro de diálogo **Páginas de propiedades**, devolvió un código de error, pero no se mostrará información en la Ventana de salida.  
  
 Causas posibles de este error:  
  
-   Su proyecto depende del servidor ATL.  A partir de [!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)], el servidor de ATL ya no se incluye como parte de Visual Studio, pero se ha publicado como un proyecto de código fuente compartido en CodePlex.  Para descargar el código fuente y las herramientas de servidor ATL, vaya a[http:\/\/go.microsoft.com\/fwlink\/?LinkID\=81979](http://go.microsoft.com/fwlink/?LinkID=81979).  
  
-   El sistema no tiene suficientes recursos.  Cierre algunas aplicaciones para solucionarlo.  
  
-   No tiene privilegios de seguridad suficientes.  Compruebe que tiene suficientes privilegios de seguridad.  
  
-   Las rutas de acceso a ejecutables especificadas en [Directorios de VC\+\+](http://msdn.microsoft.com/es-es/e027448b-c811-4c3d-8531-4325ad3f6e02) no incluyen la ruta de acceso para la herramienta que está intentando ejecutar.  
  
-   En proyectos de archivos MAKE, falta un comando para ejecutar en **Línea de comandos de compilación** o **Línea de comandos de recompilación**.  
  
## Vea también  
 [Errores y advertencias de compilación del proyecto \(PRJxxxx\)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)