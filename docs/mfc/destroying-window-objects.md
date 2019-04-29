---
title: Destruir objetos Window
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
ms.openlocfilehash: f50d198f9868a70d25370f6c1399b66efaa5490b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297247"
---
# <a name="destroying-window-objects"></a>Destruir objetos Window

Debe tener cuidado con sus propias ventanas secundarias para destruir el objeto de ventana de C++ cuando el usuario ha terminado con la ventana. Si no se destruyen estos objetos, la aplicación no recuperará su memoria. Afortunadamente, el marco de trabajo administra la destrucción de ventanas, así como la creación de ventanas de marco, vistas y cuadros de diálogo. Si crea ventanas adicionales, usted es responsable de destruirlas.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Secuencia de destrucción de ventanas](../mfc/window-destruction-sequence.md)

- [Asignación y desasignación de memoria de ventana](../mfc/allocating-and-deallocating-window-memory.md)

- [Desasociar CWnd de su HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)

- [Secuencia de creación de ventanas general](../mfc/general-window-creation-sequence.md)

- [Destruir ventanas de marco](../mfc/destroying-frame-windows.md)

## <a name="see-also"></a>Vea también

[Objetos de ventana](../mfc/window-objects.md)
