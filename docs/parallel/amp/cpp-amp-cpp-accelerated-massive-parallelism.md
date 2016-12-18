---
title: "C++ AMP (C++ Accelerated Massive Parallelism) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ Accelerated Massive Parallelism, introducción"
  - "C++ AMP (véase C++ Accelerated Massive Parallelism)"
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
caps.latest.revision: 22
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ AMP (C++ Accelerated Massive Parallelism)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El Paralelismo Masivo Acelerado C\+\+ \(AMP de C\+\+\) acelera la ejecución del código de C\+\+ aprovechando el hardware en paralelo de datos que normalmente aparece como una unidad de procesamiento gráfico \(GPU\) en una tarjeta de gráficos discretos.  El patrón de programación del AMP de C\+\+ incluye soporte para matrices multidimensionales, indexación, transferencia de memoria, y disposición en mosaicos.  También incluye una biblioteca de funciones matemáticas.  Se pueden utilizar extensiones de lenguaje de C\+\+ AMP para controlar cómo los datos se mueven del CPU al GPU y vuelven.  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Información general sobre C\+\+ AMP](../../parallel/amp/cpp-amp-overview.md)|Describe las principales características de AMP de C\+\+ y la biblioteca matemática.|  
|[Usar expresiones lambda, objetos de función y funciones restringidas](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|Describe cómo utilizar las expresiones lambda, objetos de función y funciones restringidas en llamadas al método [parallel\_for\_each](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md).|  
|[Usar mosaicos](../../parallel/amp/using-tiles.md)|Describe cómo utilizar los mosaicos y acelerar su código de AMP de C\+\+.|  
|[Usar objetos accelerator y accelerator\_view](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|Describe cómo utilizar los aceleradores para personalizar la ejecución del código en la GPU.|  
|[Usar C\+\+ AMP en aplicaciones de la Tienda Windows](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|Describe cómo utilizar C\+\+ AMP en aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] que usan tipos de Windows en tiempo de ejecución.|  
|[Gráficos \(C\+\+ AMP\)](../../parallel/amp/graphics-cpp-amp.md)|Describe cómo utilizar la biblioteca de gráficos del AMP de C\+\+.|  
|[Tutorial: Multiplicación de matrices](../../parallel/amp/walkthrough-matrix-multiplication.md)|Demuestra la multiplicación de matrices por medio del código del AMP de C\+\+ y la disposición en mosaico.|  
|[Tutorial: Depurar una aplicación de C\+\+ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|Explica cómo crear y depurar una aplicación que utilice la reducción paralela para resumir una matriz grande de enteros.|  
  
## Reference  
 [Referencia \(C\+\+ AMP\)](../../parallel/amp/reference/reference-cpp-amp.md)  
  
 [tile\_static \(Palabra clave\)](../../cpp/tile-static-keyword.md)  
  
 [restrict \(C\+\+ AMP\)](../../cpp/restrict-cpp-amp.md)  
  
## Otros recursos  
 [Programación paralela en el blog de código nativo](http://go.microsoft.com/fwlink/p/?LinkId=238472)  
  
 [Proyectos de ejemplo de C\+\+ AMP para la descarga](http://go.microsoft.com/fwlink/p/?LinkId=248508)  
  
 [Análisis de código C\+\+ AMP con el código con el Visualizador de simultaneidad](http://go.microsoft.com/fwlink/?LinkID=253987&clcid=0x409)