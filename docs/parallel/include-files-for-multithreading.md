---
title: Archivos de inclusión para el subprocesamiento múltiple
ms.date: 11/04/2016
helpviewer_keywords:
- threading [C++], include files
- include files, multithreading
- multithreading [C++], include files
ms.assetid: 98d764f9-71f4-4da5-8f3a-8d2d26e96799
ms.openlocfilehash: 79b5c56eecfaf28743eec4ba6b4cee56156d6e2c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257429"
---
# <a name="include-files-for-multithreading"></a>Archivos de inclusión para el subprocesamiento múltiple

Archivos de inclusión estándar declaran las funciones de biblioteca en tiempo de ejecución de C como se implementan en las bibliotecas de. Si usas el [optimización completa](../build/reference/ox-full-optimization.md) (/ Ox) o [convención de llamada fastcall](../build/reference/gd-gr-gv-gz-calling-convention.md) (/ Gr), el compilador supone que todas las funciones deben llamarse mediante la convención de llamada de registro. Las funciones de biblioteca de tiempo de ejecución se compilaron con la convención de llamada de C y las declaraciones de los archivos de inclusión estándar indican al compilador que genera referencias externas correctas para estas funciones.

## <a name="see-also"></a>Vea también

[Multithreading con C y Win32](multithreading-with-c-and-win32.md)
