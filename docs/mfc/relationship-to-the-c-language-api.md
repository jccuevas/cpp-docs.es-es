---
title: Relación con la API del lenguaje C
ms.date: 11/04/2016
f1_keywords:
- vc.classes.mfc
helpviewer_keywords:
- books [MFC], about MFC and Windows SDK
- books [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- Windows API [MFC], and MFC
ms.assetid: 334e8efc-f3cc-4018-bc2e-02908b2a39fe
ms.openlocfilehash: 8601dd034dbd73ac035084ad57c51f62e333fd32
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511853"
---
# <a name="relationship-to-the-c-language-api"></a>Relación con la API del lenguaje C

La única característica que establece la biblioteca de Microsoft Foundation Class (MFC) además de otras bibliotecas de clases para Windows es la asignación muy cercana a la API de Windows escrita en el lenguaje C. Además, normalmente puede mezclar llamadas a la biblioteca de clases libremente con llamadas directas a la API de Windows. Sin embargo, este acceso directo implica que las clases son un reemplazo completo de la API. En ocasiones, los desarrolladores deben realizar llamadas directas a algunas funciones de Windows, como [setCursor](/windows/win32/api/winuser/nf-winuser-setcursor) y [GetSystemMetrics](/windows/win32/api/winuser/nf-winuser-getsystemmetrics), por ejemplo. Una función de miembro de clase se ajusta mediante una función de miembro de clase solo cuando hay una ventaja clara de hacerlo.

Dado que a veces es necesario realizar llamadas a funciones nativas de Windows, debe tener acceso a la documentación de la API de Windows de lenguaje C. Esta documentación se incluye con Microsoft Visual C++.

> [!NOTE]
>  Para obtener información general sobre cómo funciona el marco de trabajo de la biblioteca MFC, vea [usar las clases para escribir aplicaciones para Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).

## <a name="see-also"></a>Vea también

[Filosofía general de diseño de clases](../mfc/general-class-design-philosophy.md)
