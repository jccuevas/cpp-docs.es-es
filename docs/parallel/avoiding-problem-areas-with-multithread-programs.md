---
title: "Evitar áreas de riesgo en programas multiproceso | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- multithreading [C++], troubleshooting
- errors [C++], multithreaded programs
- threading [C++], troubleshooting
- troubleshooting [C++], multithreading
ms.assetid: 06cc231d-bb5a-409d-8bd3-676c9e2a8c5b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 546f5b5daa88578fc7dd062018257f0929bc0cff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="avoiding-problem-areas-with-multithread-programs"></a>Evitar áreas de riesgo en programas multiproceso
Hay varios problemas que pueden surgir al crear, vincular o ejecutar un programa multiproceso en C. Algunos de los problemas más comunes que se describen en la tabla siguiente. (Para obtener una discusión similar desde el punto de vista MFC, vea [subprocesamiento múltiple: sugerencias de programación](../parallel/multithreading-programming-tips.md).)  
  
|Problema|Causa probable|  
|-------------|--------------------|  
|Obtendrá un cuadro de mensaje que muestra que el programa ha provocado una infracción de la protección.|Muchos errores de programación de Win32 causan infracciones de protección. Una causa común de las infracciones de protección es la asignación indirecta de datos a punteros null. Debido a esto da como resultado el programa intenta obtener acceso a memoria que no pertenece a él, se emite una infracción de la protección.<br /><br /> Una manera sencilla de detectar la causa de una infracción de la protección es compilar el programa con información de depuración y, a continuación, ejecutarlo mediante el depurador en el entorno de Visual C++. Cuando se produce el error de protección, Windows transfiere el control al depurador y el cursor se coloca en la línea que produjo el problema.|  
|El programa genera numerosos errores de compilación y vinculación.|Puede eliminar muchos posibles problemas al establecer el nivel de advertencia del compilador con uno de sus valores más altos y tiene en cuenta los mensajes de advertencia. Mediante el nivel 3 o las opciones de nivel de advertencia de nivel 4, puede detectar conversiones de datos no intencionadas y prototipos de función que faltan, uso de características no es ANSI.|  
  
## <a name="see-also"></a>Vea también  
 [Multithreading con C y Win32](../parallel/multithreading-with-c-and-win32.md)