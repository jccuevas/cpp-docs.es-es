---
title: Relación entre un objeto Window de C++ y un HWND | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- HWND
dev_langs:
- C++
helpviewer_keywords:
- Windows window [MFC]
- window objects [MFC], HWND and
- HWND [MFC]
- CWnd class [MFC], HWND
- HWND, window objects [MFC]
ms.assetid: f2e76340-6691-4ee6-9424-0345634a9469
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 844f62b110f54ba3e2c8909a78d58c9f2c01dcac
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392819"
---
# <a name="relationship-between-a-c-window-object-and-an-hwnd"></a>Relación entre un objeto Window de C++ y un HWND

La ventana *objeto* es un objeto de C++ `CWnd` clase (o una clase derivada) que el programa crea directamente. Y viene en respuesta a las llamadas de constructor y destructor del programa. El Windows *ventana*, por otro lado, es un identificador opaco a una estructura de datos interna de Windows que corresponde a una ventana y consume recursos del sistema cuando está presente. Una ventana de Windows se identifica mediante un "identificador de ventana" (`HWND`) y se crea después la `CWnd` objeto se crea mediante una llamada a la `Create` función miembro de clase `CWnd`. La ventana se puede destruir mediante una llamada de programa o una acción del usuario. El identificador de ventana se almacena en el objeto de ventana *m_hWnd* variable miembro. En la siguiente ilustración muestra la relación entre el objeto de ventana de C++ y la ventana de Windows. Creación de ventanas se describe en [crear Windows](../mfc/creating-windows.md). Destruir ventanas se describe en [destruir objetos Window](../mfc/destroying-window-objects.md).

![CWnd objeto de ventana y ventana resultante](../mfc/media/vc37fj1.gif "vc37fj1") objeto de ventana y ventana de Windows

## <a name="see-also"></a>Vea también

[Objetos de ventana](../mfc/window-objects.md)

