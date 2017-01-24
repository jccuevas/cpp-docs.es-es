---
title: "1.1 Scope | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: a8570a3c-1dd6-4c3d-b368-a10fcb3534a6
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 1.1 Scope
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta especificación se cubre solo la paralelización usuario\-dirigida, donde el usuario especifica explícitamente las acciones que se realizarán por el compilador y el sistema en tiempo de ejecución para ejecutar el programa en paralelo.  Las implementaciones de OpenMP c y C\+\+ no es necesario comprobar si hay dependencias, conflictos, interbloqueos, condiciones de carrera, u otros problemas que den lugar a la ejecución del programa incorrecta.  El usuario es responsable de garantizar que la aplicación utilizando las construcciones de OpenMP c y C\+\+ API se ejecuta correctamente.  la paralelización y directivas automáticas Compilador\-generadas al compilador para ayudar a tal paralelización no se cubren en este documento.