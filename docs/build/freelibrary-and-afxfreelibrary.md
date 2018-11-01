---
title: FreeLibrary y AfxFreeLibrary
ms.date: 11/04/2016
f1_keywords:
- FreeLibrary
- AfxFreeLibrary
helpviewer_keywords:
- extension DLLs [C++], unloading
- AfxFreeLibrary method
- unloading DLLs
- FreeLibrary method
- DLLs [C++], linking
- explicit linking [C++]
- DLLs [C++], unloading
ms.assetid: 4a48d290-3971-43e9-8e97-ba656cd0c8f8
ms.openlocfilehash: ce52eb43fa8f371b68d836f01163003f056f34c7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530239"
---
# <a name="freelibrary-and-afxfreelibrary"></a>FreeLibrary y AfxFreeLibrary

Los procesos que se vinculan explícitamente a una llamada a la DLL del [FreeLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-freelibrary) funcionar cuando ya no se necesita el módulo de DLL. Esta función reduce recuento de referencias del módulo y, si el recuento de referencias es cero, elimina la asignación del espacio de direcciones del proceso.

En una aplicación MFC, utilice [AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary) en lugar de `FreeLibrary` para descargar un archivo DLL de extensión MFC. La interfaz (prototipo de función) para `AfxFreeLibrary` es el mismo que `FreeLibrary`.

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Cómo vincular implícitamente a un archivo DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)

- [Determinar qué método de vinculación para usar](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [LoadLibrary y AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)

- [GetProcAddress](../build/getprocaddress.md)

## <a name="see-also"></a>Vea también

[Archivos DLL en Visual C++](../build/dlls-in-visual-cpp.md)<br/>
[FreeLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-freelibrary)
[AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)