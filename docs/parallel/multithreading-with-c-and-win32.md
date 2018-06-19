---
title: Subprocesamiento múltiple con C y Win32 | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2018
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows API [C++], multithreading
- multithreading [C++], C and Win32
- Visual C, multithreading
- Win32 applications [C++], multithreading
- threading [C++], C and Win32
- Win32 [C++], multithreading
- threading [C]
ms.assetid: 67cdc99e-1ad9-452b-a042-ed246b70040e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 993bee92c9dacc831a8bbc8fc000ec982025a399
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687548"
---
# <a name="multithreading-with-c-and-win32"></a>Subprocesamiento múltiple con C y Win32
Microsoft Visual C++ proporciona compatibilidad para crear aplicaciones multiproceso. Considere la posibilidad de uso de más de un subproceso si la aplicación necesita realizar operaciones costosas que puede provocar que la interfaz de usuario deje de responder.  
  
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