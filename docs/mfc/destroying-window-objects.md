---
title: Destruir objetos Window
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
ms.openlocfilehash: 22b483c1005931b229453ae229935c0e716ab726
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621860"
---
# <a name="destroying-window-objects"></a>Destruir objetos Window

Se debe tener cuidado con sus propias ventanas secundarias para destruir el objeto de ventana de C++ cuando el usuario finaliza con la ventana. Si estos objetos no se destruyen, la aplicación no recuperará su memoria. Afortunadamente, el marco de trabajo administra la destrucción de la ventana, así como la creación de ventanas de marco, vistas y cuadros de diálogo. Si crea ventanas adicionales, es el responsable de destruirlas.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Secuencia de destrucción de ventanas](window-destruction-sequence.md)

- [Asignar y desasignar memoria de ventana](allocating-and-deallocating-window-memory.md)

- [Desasociar CWnd de su HWND](detaching-a-cwnd-from-its-hwnd.md)

- [Secuencia de creación de ventanas general](general-window-creation-sequence.md)

- [Destrucción de ventanas de marco](destroying-frame-windows.md)

## <a name="see-also"></a>Consulte también

[Window (Objetos)](window-objects.md)
