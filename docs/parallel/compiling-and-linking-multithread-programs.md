---
title: Compilar y vincular programas multiproceso | Documentos de Microsoft
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
- compiling multithreaded programs
- multithreading [C++], linking programs
- threading [C++], linking programs
- multithreading [C++], compiled programs
- threading [C++], compiled programs
- compiling source code [C++], multithread programs
- linking [C++], multithread programs
ms.assetid: 27589afc-daf2-4f26-b868-a99de5c9dfec
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0145c480d74cb1978c1b6caef65489eae96501c2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiling-and-linking-multithread-programs"></a>Compilar y vincular programas multiproceso
El programa Bounce.c se incorporó en [Sample Multithread C Program](../parallel/sample-multithread-c-program.md).  
  
 Compilar programas multiproceso de forma predeterminada.  
  
#### <a name="to-compile-and-link-the-multithread-program-bouncec-from-within-the-development-environment"></a>Para compilar y vincular el programa multiproceso Bounce.c desde dentro del entorno de desarrollo  
  
1.  En el menú **Archivo** , haga clic en **Nuevo**y, a continuación, haga clic en **Proyecto**.  
  
2.  En el **tipos de proyecto** panel, haga clic en **Win32**.  
  
3.  En el **plantillas** panel, haga clic en **aplicación de consola Win32**y, a continuación, el nombre del proyecto.  
  
4.  Agregue el archivo que contiene el código fuente de C al proyecto.  
  
5.  En el **generar** menú, compile el proyecto, haga clic en el **generar** comando.  
  
#### <a name="to-compile-and-link-the-multithread-program-bouncec-from-the-command-line"></a>Para compilar y vincular el programa multiproceso Bounce.c desde la línea de comandos  
  
1.  Compile y vincule el programa:  
  
    ```  
    CL BOUNCE.C  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Multithreading con C y Win32](../parallel/multithreading-with-c-and-win32.md)