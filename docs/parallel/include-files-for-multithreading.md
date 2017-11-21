---
title: "Archivos de inclusión para Multithreading | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- threading [C++], include files
- include files, multithreading
- multithreading [C++], include files
ms.assetid: 98d764f9-71f4-4da5-8f3a-8d2d26e96799
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bcc8282680588585335eaa2c876128d2c2cf23a3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="include-files-for-multithreading"></a>Archivos de inclusión para el subprocesamiento múltiple
Archivos de inclusión estándar declarar funciones de biblioteca en tiempo de ejecución de C tal y como se implementan en las bibliotecas. Si usas el [optimización completa](../build/reference/ox-full-optimization.md) (/ Ox) o [convención de llamada fastcall](../build/reference/gd-gr-gv-gz-calling-convention.md) (/ Gr), el compilador supone que todas las funciones se deberían llamar mediante la convención de llamada de registro. Las funciones de biblioteca en tiempo de ejecución se compilaron con la convención de llamada de C, y las declaraciones en los archivos de inclusión estándar indican al compilador que genera referencias externas correcta para estas funciones.  
  
## <a name="see-also"></a>Vea también  
 [Multithreading con C y Win32](../parallel/multithreading-with-c-and-win32.md)