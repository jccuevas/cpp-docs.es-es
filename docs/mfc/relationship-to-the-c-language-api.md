---
title: Relación con la API del lenguaje C
ms.date: 11/04/2016
helpviewer_keywords:
- books [MFC], about MFC and Windows SDK
- books [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- Windows API [MFC], and MFC
ms.assetid: 334e8efc-f3cc-4018-bc2e-02908b2a39fe
ms.openlocfilehash: 1fbd4d332f5ade1cb9415448b138ac5bc838307d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372826"
---
# <a name="relationship-to-the-c-language-api"></a>Relación con la API del lenguaje C

La característica única que diferencia a la biblioteca de Microsoft Foundation Class (MFC) de otras bibliotecas de clases para Windows es la asignación muy cercana a la API de Windows escrita en el lenguaje C. Además, generalmente puede mezclar llamadas a la biblioteca de clases libremente con llamadas directas a la API de Windows. Sin embargo, este acceso directo no implica que las clases sean un reemplazo completo para esa API. Los desarrolladores todavía deben realizar ocasionalmente llamadas directas a algunas funciones de Windows, como [SetCursor](/windows/win32/api/winuser/nf-winuser-setcursor) y [GetSystemMetrics](/windows/win32/api/winuser/nf-winuser-getsystemmetrics), por ejemplo. Una función de Windows se ajusta mediante una función miembro de clase solo cuando hay una clara ventaja de hacerlo.

Dado que a veces necesita realizar llamadas a funciones nativas de Windows, debe tener acceso a la documentación de la API de Windows en lenguaje C. Esta documentación se incluye con Microsoft Visual C++.

> [!NOTE]
> Para obtener información general sobre cómo funciona el marco de trabajo de la biblioteca MFC, vea Uso de [las clases para escribir aplicaciones para Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).

## <a name="see-also"></a>Consulte también

[Filosofía general de diseño de clases](../mfc/general-class-design-philosophy.md)
