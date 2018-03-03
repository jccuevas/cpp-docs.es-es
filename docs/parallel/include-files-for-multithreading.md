---
title: "Archivos de inclusión para Multithreading | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- threading [C++], include files
- include files, multithreading
- multithreading [C++], include files
ms.assetid: 98d764f9-71f4-4da5-8f3a-8d2d26e96799
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0f71b52bca5f636d80f2d55cc5e9ffc3e217d90a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="include-files-for-multithreading"></a>Archivos de inclusión para el subprocesamiento múltiple
Archivos de inclusión estándar declarar funciones de biblioteca en tiempo de ejecución de C tal y como se implementan en las bibliotecas. Si usas el [optimización completa](../build/reference/ox-full-optimization.md) (/ Ox) o [convención de llamada fastcall](../build/reference/gd-gr-gv-gz-calling-convention.md) (/ Gr), el compilador supone que todas las funciones se deberían llamar mediante la convención de llamada de registro. Las funciones de biblioteca en tiempo de ejecución se compilaron con la convención de llamada de C, y las declaraciones en los archivos de inclusión estándar indican al compilador que genera referencias externas correcta para estas funciones.  
  
## <a name="see-also"></a>Vea también  
 [Multithreading con C y Win32](../parallel/multithreading-with-c-and-win32.md)