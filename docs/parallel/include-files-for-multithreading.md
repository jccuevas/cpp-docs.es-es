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
ms.openlocfilehash: 64ba6ec639151ca659e3bd075f691176ef4edbdd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422329"
---
# <a name="include-files-for-multithreading"></a>Archivos de inclusión para el subprocesamiento múltiple

Archivos de inclusión estándar declaran las funciones de biblioteca en tiempo de ejecución de C como se implementan en las bibliotecas de. Si usas el [optimización completa](../build/reference/ox-full-optimization.md) (/ Ox) o [convención de llamada fastcall](../build/reference/gd-gr-gv-gz-calling-convention.md) (/ Gr), el compilador supone que todas las funciones deben llamarse mediante la convención de llamada de registro. Las funciones de biblioteca de tiempo de ejecución se compilaron con la convención de llamada de C y las declaraciones de los archivos de inclusión estándar indican al compilador que genera referencias externas correctas para estas funciones.

## <a name="see-also"></a>Vea también

[Multithreading con C y Win32](multithreading-with-c-and-win32.md)