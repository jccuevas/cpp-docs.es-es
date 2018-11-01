---
title: Implementación de un administrador de cadenas personalizado (método básico)
ms.date: 11/04/2016
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: eac5d13e-cbb4-4e82-b01e-f5f2dbcb962a
ms.openlocfilehash: 4e3ffcdcd034fea81734aaeb87e4c33d81647f66
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537821"
---
# <a name="implementation-of-a-custom-string-manager-basic-method"></a>Implementación de un administrador de cadenas personalizado (método básico)

La manera más fácil de personalizar el esquema de asignación de memoria de datos de cadena están utilizar siempre ATL `CAtlStringMgr` clase pero proporcionar su propia memoria rutinas de asignación. El constructor de `CAtlStringMgr` toma un único parámetro: un puntero a un `IAtlMemMgr` objeto. `IAtlMemMgr` es una clase base abstracta que proporciona una interfaz genérica para un montón. Mediante el `IAtlMemMgr` interfaz, el `CAtlStringMgr` asigna, reasigna y libera la memoria usada para almacenar datos de cadena. Puede implementar la `IAtlMemMgr` interfaz usted mismo o usar uno de las cinco clases de administrador de memoria que proporciona ATL. Los administradores de memoria que proporciona ATL simplemente ajustan las instalaciones existentes de asignación de memoria:

- [CCRTHeap](../atl/reference/ccrtheap-class.md) ajusta las funciones del montón de CRT estándares ([malloc](../c-runtime-library/reference/malloc.md), [libre](../c-runtime-library/reference/free.md), y [realloc](../c-runtime-library/reference/realloc.md))

- [CWin32Heap](../atl/reference/cwin32heap-class.md) encapsula un montón de Win32 controlar, mediante [HeapAlloc](/windows/desktop/api/heapapi/nf-heapapi-heapalloc), [HeapFree](/windows/desktop/api/heapapi/nf-heapapi-heapfree), y [HeapRealloc](/windows/desktop/api/heapapi/nf-heapapi-heaprealloc)

- [CLocalHeap](../atl/reference/clocalheap-class.md) encapsula las API de Win32: [LocalAlloc](/windows/desktop/api/winbase/nf-winbase-localalloc), [LocalFree](/windows/desktop/api/winbase/nf-winbase-localfree), y [LocalRealloc](/windows/desktop/api/winbase/nf-winbase-localrealloc)

- [CGlobalHeap](../atl/reference/cglobalheap-class.md) encapsula las API de Win32: [GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc), [GlobalFree](/windows/desktop/api/winbase/nf-winbase-globalfree), y [GlobalRealloc](/windows/desktop/api/winbase/nf-winbase-globalrealloc).

- [CComHeap](../atl/reference/ccomheap-class.md) encapsula las API de asignador de tareas COM: [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc), [CoTaskMemFree](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemfree), y [CoTaskMemRealloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemrealloc)

Para simplificar la administración de memoria de cadena, la clase más útil es `CWin32Heap` porque permite crear múltiples montones independientes. Por ejemplo, si desea utilizar un montón aparte solo para cadenas, podría hacer lo siguiente:

[!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_1.cpp)]

Para usar este administrador de cadena privada para administrar la memoria para un `CString` variable, pase un puntero para el administrador como un parámetro a la `CString` constructor de la variable:

[!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_2.cpp)]

## <a name="see-also"></a>Vea también

[Administración de memoria con CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)

