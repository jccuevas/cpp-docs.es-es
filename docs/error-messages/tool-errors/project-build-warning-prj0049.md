---
title: "Advertencia PRJ0049 al compilar el proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0049"
ms.assetid: 8b38afa1-e080-4efd-ae89-776cfd044413
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia PRJ0049 al compilar el proyecto
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Referencia\>' de destino '\<hace referencia requiere .NET Framework \<MinFrameworkVersion\> y no podrá para ejecutarse en el marco de destino de este proyecto  
  
 Las aplicaciones creadas con [!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)] pueden especificar a qué versión de [!INCLUDE[dnprdnshort](../../error-messages/tool-errors/includes/dnprdnshort_md.md)] deben estar destinadas.  Si agrega una referencia a un ensamblado o proyecto que depende de una versión de [!INCLUDE[dnprdnshort](../../error-messages/tool-errors/includes/dnprdnshort_md.md)] posterior a la versión de destino, obtendrá esta advertencia en tiempo de compilación.  
  
### Para corregir esta advertencia  
  
1.  Elija una de las siguientes opciones:  
  
    -   Cambie la versión de .NET Framework de destino en el cuadro de diálogo **Páginas de propiedades** del proyecto para que sea posterior o igual a la versión mínima del marco de trabajo de todos los ensamblados y proyectos a los que se hace referencia.  Para obtener más información, vea [Agregar referencias](../../ide/adding-references-in-visual-cpp-projects.md).  
  
    -   Quite la referencia al ensamblado o proyecto con una versión mínima de .NET Framework posterior a la de la versión de .NET Framework de destino.  Estos elementos se marcarán con un icono de advertencia en las **Páginas de propiedades** del proyecto.  
  
## Vea también  
 [Errores y advertencias de compilación del proyecto \(PRJxxxx\)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)