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
ms.openlocfilehash: 709e4fdbc24d6fbbac44944e686a6fecf8c9b8db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274045"
---
# <a name="freelibrary-and-afxfreelibrary"></a>FreeLibrary y AfxFreeLibrary

Los procesos que se vinculan explícitamente a una llamada a la DLL del [FreeLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-freelibrary) funcionar cuando ya no se necesita el módulo de DLL. Esta función reduce recuento de referencias del módulo y, si el recuento de referencias es cero, elimina la asignación del espacio de direcciones del proceso.

En una aplicación MFC, utilice [AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary) en lugar de `FreeLibrary` para descargar un archivo DLL de extensión MFC. La interfaz (prototipo de función) para `AfxFreeLibrary` es el mismo que `FreeLibrary`.

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Vincular un ejecutable a un archivo DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [Vincular un ejecutable a un archivo DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [LoadLibrary y AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>Vea también

[Archivos DLL en Visual C++](dlls-in-visual-cpp.md)<br/>
[FreeLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-freelibrary)
[AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)
