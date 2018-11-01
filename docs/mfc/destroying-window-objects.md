---
title: Destruir objetos Window
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
ms.openlocfilehash: 363ff2a4cee48b1660de87714d73c93e795017cd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488817"
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

