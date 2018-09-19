---
title: Archivos de inclusión para Multithreading | Microsoft Docs
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
ms.openlocfilehash: ec531c2c0eeac14a617a3e0e3b450cf467808165
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2018
ms.locfileid: "43130773"
---
# <a name="include-files-for-multithreading"></a>Archivos de inclusión para el subprocesamiento múltiple
Archivos de inclusión estándar declaran las funciones de biblioteca en tiempo de ejecución de C como se implementan en las bibliotecas de. Si usas el [optimización completa](../build/reference/ox-full-optimization.md) (/ Ox) o [convención de llamada fastcall](../build/reference/gd-gr-gv-gz-calling-convention.md) (/ Gr), el compilador supone que todas las funciones deben llamarse mediante la convención de llamada de registro. Las funciones de biblioteca de tiempo de ejecución se compilaron con la convención de llamada de C y las declaraciones de los archivos de inclusión estándar indican al compilador que genera referencias externas correctas para estas funciones.  
  
## <a name="see-also"></a>Vea también  

[Multithreading con C y Win32](multithreading-with-c-and-win32.md)