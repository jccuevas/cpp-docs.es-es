---
title: Implementación de un administrador de cadenas personalizado (método básico)
ms.date: 11/04/2016
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: eac5d13e-cbb4-4e82-b01e-f5f2dbcb962a
ms.openlocfilehash: 92c1c46f5251980f9cefb55e052e9aff395e0e60
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491309"
---
# <a name="implementation-of-a-custom-string-manager-basic-method"></a>Implementación de un administrador de cadenas personalizado (método básico)

La manera más sencilla de personalizar el esquema de asignación de memoria para los datos de cadena es usar `CAtlStringMgr` la clase proporcionada por ATL, pero proporcionar sus propias rutinas de asignación de memoria. El constructor de `CAtlStringMgr` toma un parámetro único: un puntero a un `IAtlMemMgr` objeto. `IAtlMemMgr`es una clase base abstracta que proporciona una interfaz genérica a un montón. Mediante la `IAtlMemMgr` interfaz, el `CAtlStringMgr` asigna, reasigna y libera la memoria usada para almacenar los datos de cadena. Puede implementar la `IAtlMemMgr` interfaz usted mismo, o bien utilizar una de las cinco clases de administrador de memoria proporcionadas por ATL. Los administradores de memoria proporcionados por ATL simplemente ajustan las funciones de asignación de memoria existentes:

- [CCRTHeap](../atl/reference/ccrtheap-class.md) Incluye las funciones del montón estándar de CRT ([malloc](../c-runtime-library/reference/malloc.md), [Free](../c-runtime-library/reference/free.md)y [realloc](../c-runtime-library/reference/realloc.md))

- [CWin32Heap](../atl/reference/cwin32heap-class.md) Incluye un identificador de montón de Win32, con [HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc), [HeapFree](/windows/win32/api/heapapi/nf-heapapi-heapfree)y [HeapRealloc](/windows/win32/api/heapapi/nf-heapapi-heaprealloc)

- [CLocalHeap](../atl/reference/clocalheap-class.md) Incluye las API de Win32: [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc), [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree)y [LocalRealloc](/windows/win32/api/winbase/nf-winbase-localrealloc)

- [CGlobalHeap](../atl/reference/cglobalheap-class.md) Incluye las API de Win32: [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc), [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree)y [GlobalRealloc](/windows/win32/api/winbase/nf-winbase-globalrealloc).

- [CComHeap](../atl/reference/ccomheap-class.md) Incluye las API de asignador de tareas COM: [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc), [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree)y [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc)

En lo que respecta a la administración de memoria de cadenas, la `CWin32Heap` clase más útil es porque le permite crear varios montones independientes. Por ejemplo, si desea utilizar un montón independiente solo para las cadenas, puede hacer lo siguiente:

[!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_1.cpp)]

Para usar este administrador de cadenas privado para administrar la memoria `CString` de una variable, pase un puntero al administrador como parámetro al constructor `CString` de la variable:

[!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_2.cpp)]

## <a name="see-also"></a>Vea también

[Administración de memoria con CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)
