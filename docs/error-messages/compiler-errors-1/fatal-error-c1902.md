---
title: "Error irrecuperable C1902 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1902"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1902"
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1902
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El administrador de base de datos de programa no coincide; compruebe la instalación  
  
 Un archivo de base de datos de programa \(.pdb\) se creó con una versión más reciente de mspdb*XX*.dll que el compilador encontrada en el sistema.  Este error suele indicar que mspdbsrv.exe o mspdbcore.dll faltan o tienen versiones distintas el mspdb*XX*.dll. \(El marcador de posición del *XX* de nombre de archivo de*XX*.dll de mspdb con cada versión del producto.  Por ejemplo, en [!INCLUDE[vsprvslong](../../error-messages/compiler-errors-1/includes/vsprvslong_md.md)], el nombre de archivo es mspdb80.dll.\)  
  
 Asegúrese de que las versiones coincidentes de mspdbsrv.exe, mspdbcore.dll, y el mspdb*XX*.dll está instalado en el sistema.  Asegúrese de que no se hayan copiado versiones no coincidentes en el directorio que contiene el compilador y las herramientas de vinculación para su plataforma de destino.  Por ejemplo, podría haber copiado los archivos para poder invocar al compilador o herramienta de vinculación desde el símbolo del sistema sin establecer la variable de entorno **PATH** en consecuencia.