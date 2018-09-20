---
title: Multithreading con C y Win32 | Microsoft Docs
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
ms.openlocfilehash: 09397b5a60dcc2cbe2b3e6265f6080f3c5c1e212
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428101"
---
# <a name="multithreading-with-c-and-win32"></a>Subprocesamiento múltiple con C y Win32

Microsoft Visual C++ proporciona compatibilidad para crear aplicaciones multiproceso. Debe considerar el uso de más de un subproceso si la aplicación necesita realizar operaciones costosas que provocarían la interfaz de usuario deje de responder.

Con Visual C++, hay dos maneras de programar con múltiples subprocesos: utilizar la biblioteca Microsoft Foundation Class (MFC) o la biblioteca de tiempo de ejecución de C y la API de Win32. Para obtener información sobre cómo crear aplicaciones multiproceso con MFC, vea [Multithreading con C++ y MFC](multithreading-with-cpp-and-mfc.md) después de leer los temas siguientes sobre multithreading en C.

Estos temas explican las características de Visual C++ que admiten la creación de programas multiproceso.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [¿Qué multithreading consiste en](multithread-programs.md)

- [Compatibilidad de bibliotecas con multithreading](library-support-for-multithreading.md)

- [Archivos de inclusión para multithreading](include-files-for-multithreading.md)

- [Funciones de la biblioteca de tiempo de ejecución de C para control de subprocesos](c-run-time-library-functions-for-thread-control.md)

- [Ejemplo de programa multiproceso en C](sample-multithread-c-program.md)

- [Crear un programa Win32 multiproceso](writing-a-multithreaded-win32-program.md)

- [Compilar y vincular programas multiproceso](compiling-and-linking-multithread-programs.md)

- [Evitar áreas de riesgo en programas multiproceso](avoiding-problem-areas-with-multithread-programs.md)

- [Almacenamiento local de subprocesos (TLS)](thread-local-storage-tls.md)

## <a name="see-also"></a>Vea también

[Compatibilidad del código antiguo con multithreading (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)