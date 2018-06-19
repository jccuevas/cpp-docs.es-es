---
title: Archivos de inclusión para Multithreading | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- threading [C++], include files
- include files, multithreading
- multithreading [C++], include files
ms.assetid: 98d764f9-71f4-4da5-8f3a-8d2d26e96799
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 62b94f4a7a394b78cb7c6f23275709e4aeacc774
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33685806"
---
# <a name="include-files-for-multithreading"></a>Archivos de inclusión para el subprocesamiento múltiple
Archivos de inclusión estándar declarar funciones de biblioteca en tiempo de ejecución de C tal y como se implementan en las bibliotecas. Si usas el [optimización completa](../build/reference/ox-full-optimization.md) (/ Ox) o [convención de llamada fastcall](../build/reference/gd-gr-gv-gz-calling-convention.md) (/ Gr), el compilador supone que todas las funciones se deberían llamar mediante la convención de llamada de registro. Las funciones de biblioteca en tiempo de ejecución se compilaron con la convención de llamada de C, y las declaraciones en los archivos de inclusión estándar indican al compilador que genera referencias externas correcta para estas funciones.  
  
## <a name="see-also"></a>Vea también  
 [Multithreading con C y Win32](../parallel/multithreading-with-c-and-win32.md)