---
title: "Error en tiempo de ejecuci&#243;n de C R6028 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "R6028"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6028"
ms.assetid: 81e99079-4388-4244-a4f7-4641c508871c
caps.latest.revision: 9
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error en tiempo de ejecuci&#243;n de C R6028
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no puede inicializar el montón  
  
 Este error aparece cuando el sistema operativo no puede crear el almacén de memoria para la aplicación.  Específicamente, la biblioteca en tiempo de ejecución de C \(CRT\) ha llamado a la función `HeapCreate` de Win32, que ha devuelto NULL, lo que indica un error.  
  
 Si este error se produce durante el inicio de la aplicación, es posible que el sistema no pueda atender las solicitudes de montón porque se carguen controladores defectuosos.  Compruebe en Windows Update o en el sitio web del distribuidor de hardware si hay controladores actualizados.