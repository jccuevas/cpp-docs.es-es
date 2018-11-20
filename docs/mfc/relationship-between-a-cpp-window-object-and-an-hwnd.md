---
title: Relación entre un objeto Window de C++ y un HWND
ms.date: 11/19/2018
f1_keywords:
- HWND
helpviewer_keywords:
- Windows window [MFC]
- window objects [MFC], HWND and
- HWND [MFC]
- CWnd class [MFC], HWND
- HWND, window objects [MFC]
ms.assetid: f2e76340-6691-4ee6-9424-0345634a9469
ms.openlocfilehash: fcd885fbaf7e81d68bcd51edc4b74c553f70578b
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176866"
---
# <a name="relationship-between-a-c-window-object-and-an-hwnd"></a>Relación entre un objeto Window de C++ y un HWND

La ventana *objeto* es un objeto de C++ `CWnd` clase (o una clase derivada) que el programa crea directamente. Y viene en respuesta a las llamadas de constructor y destructor del programa. El Windows *ventana*, por otro lado, es un identificador opaco a una estructura de datos interna de Windows que corresponde a una ventana y consume recursos del sistema cuando está presente. Una ventana de Windows se identifica mediante un "identificador de ventana" (`HWND`) y se crea después la `CWnd` objeto se crea mediante una llamada a la `Create` función miembro de clase `CWnd`. La ventana se puede destruir mediante una llamada de programa o una acción del usuario. El identificador de ventana se almacena en el objeto de ventana *m_hWnd* variable miembro. En la siguiente ilustración muestra la relación entre el objeto de ventana de C++ y la ventana de Windows. Creación de ventanas se describe en [crear Windows](../mfc/creating-windows.md). Destruir ventanas se describe en [destruir objetos Window](../mfc/destroying-window-objects.md).

![CWnd objeto de ventana y ventana resultante](../mfc/media/vc37fj1.gif "CWnd objeto de ventana y ventana resultante") <br/>
Objeto de ventana y ventana de Windows

## <a name="see-also"></a>Vea también

[Objetos de ventana](../mfc/window-objects.md)
