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
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289850"
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
