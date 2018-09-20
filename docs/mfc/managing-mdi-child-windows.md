---
title: Administración de Windows de secundarios MDI | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MDICLIENT
dev_langs:
- C++
helpviewer_keywords:
- MDI [MFC], child windows
- child windows [MFC], and MDICLIENT window
- MDICLIENT window [MFC]
- windows [MFC], MDI
- frame windows [MFC], MDI child windows
- child windows [MFC]
- MDI [MFC], frame windows
ms.assetid: 1828d96e-a561-48ae-a661-ba9701de6bee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45989b7c07d27db1d7b2cda68751bd6165ee5382
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428283"
---
# <a name="managing-mdi-child-windows"></a>Administrar ventanas secundarias MDI

Ventanas de marco principal MDI (una por aplicación) contienen una ventana secundaria especial denominada ventana MDICLIENT. La ventana MDICLIENT administra el área cliente de la ventana de marco principal y tiene ventanas secundarias: las ventanas de documento, que se deriva de `CMDIChildWnd`. Dado que las ventanas de documento son ventanas de marco a sí mismos (ventanas secundarias de MDI), también pueden tener sus propios elementos secundarios. En todos estos casos, la ventana primaria administra sus ventanas secundarias y envía algunos comandos.

En una ventana de marco MDI, la ventana de marco administra la ventana MDICLIENT, cambiar la posición junto con las barras de control. La ventana MDICLIENT, a su vez, administra todas las ventanas de marco secundarias MDI. En la siguiente ilustración muestra la relación entre una ventana marco MDI, su ventana MDICLIENT y sus ventanas de marco de documento secundarias.

![Ventanas secundarias en una ventana marco MDI](../mfc/media/vc37gb1.gif "vc37gb1") Windows de marco MDI y elementos secundarios.

Una ventana marco MDI también funciona junto con la ventana secundaria MDI actual, si hay alguno. La ventana de marco MDI delega los mensajes de comando al formulario secundario MDI antes de intentar controlar propio.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Crear ventanas de marco de documento](../mfc/creating-document-frame-windows.md)

- [Estilos de ventana de marco](../mfc/frame-window-styles-cpp.md)

## <a name="see-also"></a>Vea también

[Uso de ventanas de marco](../mfc/using-frame-windows.md)

