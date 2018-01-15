---
title: "Subprocesamiento múltiple con C y Win32 | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows API [C++], multithreading
- multithreading [C++], C and Win32
- Visual C, multithreading
- Win32 applications [C++], multithreading
- threading [C++], C and Win32
- Win32 [C++], multithreading
- threading [C]
ms.assetid: 67cdc99e-1ad9-452b-a042-ed246b70040e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 30c7833a4df80669b6223f1fe6b1ccceed0257cc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="multithreading-with-c-and-win32"></a>Subprocesamiento múltiple con C y Win32
Microsoft Visual C++ proporciona compatibilidad para crear aplicaciones multiproceso con Microsoft Windows: Windows XP, Windows 2000, Windows NT, Windows Millennium Edition y Windows 98. Considere la posibilidad de uso de más de un subproceso si la aplicación necesita administrar varias actividades, tales como simultánea teclado y mouse (ratón). Un subproceso puede procesar entradas mediante teclado, mientras que un segundo subproceso filtra las actividades del mouse. Un tercer subproceso puede actualizar la presentación en pantalla en función de los datos de los subprocesos del teclado y mouse (ratón). Al mismo tiempo, otros subprocesos pueden tener acceso a archivos de disco u obtener datos de un puerto de comunicaciones.  
  
 Con Visual C++, hay dos maneras de programar con múltiples subprocesos: utilizar la biblioteca (Microsoft Foundation Classes) o la biblioteca de tiempo de ejecución de C y la API de Win32. Para obtener información sobre cómo crear aplicaciones multiproceso con MFC, vea [Multithreading con C++ y MFC](../parallel/multithreading-with-cpp-and-mfc.md) después de leer los temas siguientes sobre multithreading en C.  
  
 Estos temas explican las características de Visual C++ que admiten la creación de programas multiproceso.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [¿Qué subprocesamiento múltiple es acerca de](../parallel/multithread-programs.md)  
  
-   [Compatibilidad de bibliotecas con subprocesamiento múltiple](../parallel/library-support-for-multithreading.md)  
  
-   [Archivos de inclusión para multithreading](../parallel/include-files-for-multithreading.md)  
  
-   [Funciones de la biblioteca de tiempo de ejecución de C para el control de subprocesos](../parallel/c-run-time-library-functions-for-thread-control.md)  
  
-   [Ejemplo de programa multiproceso en C](../parallel/sample-multithread-c-program.md)  
  
-   [Crear un programa Win32 multiproceso](../parallel/writing-a-multithreaded-win32-program.md)  
  
-   [Compilar y vincular programas multiproceso](../parallel/compiling-and-linking-multithread-programs.md)  
  
-   [Evitar áreas de riesgo en programas multiproceso](../parallel/avoiding-problem-areas-with-multithread-programs.md)  
  
-   [Almacenamiento local de subprocesos (TLS)](../parallel/thread-local-storage-tls.md)  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad del código antiguo con multithreading (Visual C++)](../parallel/multithreading-support-for-older-code-visual-cpp.md)