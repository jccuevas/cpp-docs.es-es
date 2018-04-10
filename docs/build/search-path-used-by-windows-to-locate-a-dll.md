---
title: Ruta de acceso que Windows usa para encontrar un archivo DLL | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- searching [C++], DLLs
- DLLs [C++], Windows search path
- Windows [C++], DLL search path
- known DLL searches [C++]
- locating DLLs
- finding DLLs
- search paths [C++]
ms.assetid: 84bfb380-ad7b-4962-b2d0-51b19a45f1bb
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 53350ed473226c86dd4fefa93cff376a371dedf7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="search-path-used-by-windows-to-locate-a-dll"></a>Ruta de búsqueda de Windows para encontrar un archivo DLL
Tanto en la vinculación implícita como en la vinculación explícita, Windows busca primero "archivos DLL conocidos", como Kernel32.dll y User32.dll. Después, Windows busca los archivos DLL en el orden siguiente:  
  
1.  El directorio que contiene el módulo ejecutable para el proceso actual.  
  
2.  El directorio actual.  
  
3.  El directorio del sistema de Windows. El **GetSystemDirectory** función recupera la ruta de acceso de este directorio.  
  
4.  El directorio de Windows. El **GetWindowsDirectory** función recupera la ruta de acceso de este directorio.  
  
5.  Los directorios mostrados en la variable de entorno PATH.  
  
    > [!NOTE]
    >  La variable de entorno LIBPATH no se utiliza.  
  
## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?  
  
-   [Cómo vincular implícitamente a un archivo DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)  
  
-   [Cómo vincular explícitamente a un archivo DLL](../build/linking-an-executable-to-a-dll.md#linking-explicitly)  
  
-   [Determinar qué método de vinculación para usar](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
## <a name="see-also"></a>Vea también  
 [Archivos DLL en Visual C++](../build/dlls-in-visual-cpp.md)