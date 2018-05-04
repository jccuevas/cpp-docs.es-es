---
title: Implementación de un administrador de cadenas personalizado (método básico) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: eac5d13e-cbb4-4e82-b01e-f5f2dbcb962a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 259f9533747b266f0be0a782cdc94c98f167d2d2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="implementation-of-a-custom-string-manager-basic-method"></a>Implementación de un administrador de cadenas personalizado (método básico)
La manera más fácil de personalizar el esquema de asignación de memoria de datos de cadena están utilizar siempre ATL **CAtlStringMgr** clase pero proporcionar su propia memoria rutinas de asignación. El constructor de **CAtlStringMgr** toma un único parámetro: un puntero a un `IAtlMemMgr` objeto. `IAtlMemMgr` es una clase base abstracta que proporciona una interfaz genérica para un montón. Mediante el `IAtlMemMgr` interfaz, el **CAtlStringMgr** asigna, reasigna y libera la memoria utilizada para almacenar datos de cadena. Puede bien implemente la `IAtlMemMgr` interfaz usted mismo o usar una de las cinco clases de administrador de memoria que proporciona ATL. Los administradores de memoria que proporciona ATL simplemente encapsulan las instalaciones existentes de asignación de memoria:  
  
-   [CCRTHeap](../atl/reference/ccrtheap-class.md) ajusta las funciones del montón de CRT estándares ([malloc](../c-runtime-library/reference/malloc.md), [libre](../c-runtime-library/reference/free.md), y [realloc](../c-runtime-library/reference/realloc.md))  
  
-   [CWin32Heap](../atl/reference/cwin32heap-class.md) encapsula un montón de Win32 controlar, mediante [HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597), [HeapFree](http://msdn.microsoft.com/library/windows/desktop/aa366701), y [HeapRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366704)  
  
-   [CLocalHeap](../atl/reference/clocalheap-class.md) encapsula las API de Win32: [LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723), [LocalFree](http://msdn.microsoft.com/library/windows/desktop/aa366730), y [LocalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366742)  
  
-   [CGlobalHeap](../atl/reference/cglobalheap-class.md) encapsula las API de Win32: [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574), [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579), y [GlobalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366590).  
  
-   [CComHeap](../atl/reference/ccomheap-class.md) contiene las API de asignador de tareas COM: [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727), [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722), y [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280)  
  
 Con fines de administración de memoria de cadena, la clase más útil es `CWin32Heap` porque permite crear múltiples montones independientes. Por ejemplo, si desea utilizar un montón aparte solo para cadenas, podría hacer lo siguiente:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_1.cpp)]  
  
 Para usar este administrador de cadenas privado para administrar la memoria para un `CString` variable, pase un puntero al administrador como un parámetro a la `CString` constructor de la variable:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_2.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Administración de memoria con CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)

