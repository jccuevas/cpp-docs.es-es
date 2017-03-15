---
title: "Error de BSCMAKE BK1517 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "BK1517"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BK1517"
ms.assetid: 24391f42-0a3e-40a9-9991-c8b9a6a7b1c7
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error de BSCMAKE BK1517
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

archivo de código fuente para 'archivo\_sbr' compilado con \/Yc y con \/Yu  
  
 El archivo .sbr hace referencia a sí mismo.  Probablemente se volvió a compilar mediante \/Yu después de compilarse con \/Yc.  Restablezca la opción del compilador para el archivo de código fuente en \/Yc y, a continuación, seleccione **Recompilar** para generar nuevos archivos .sbr.  No vuelva a compilar el archivo de código fuente con \/Yu.