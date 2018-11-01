---
title: Uso de una ventana (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- CWindow class, about CWindow class
- windows [C++], ATL
ms.assetid: b3b9cc8e-4287-486b-b080-38852bc2943a
ms.openlocfilehash: 7446196e9eec4b9d9236d4ab55afd9fcf859254b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568667"
---
# <a name="using-a-window"></a>Uso de una ventana

Clase [CWindow](../atl/reference/cwindow-class.md) le permite usar una ventana. Una vez que se adjunta una ventana para un `CWindow` objeto, a continuación, puede llamar a `CWindow` métodos para manipular la ventana. `CWindow` También contiene un operador HWND para convertir un `CWindow` objeto en un HWND. Por lo tanto puede pasar un `CWindow` objeto a cualquier función que requiere un identificador a una ventana. Puede mezclar fácilmente `CWindow` llamadas a métodos y las llamadas de función de Win32, sin crear ningún objeto temporal.

Dado que `CWindow` tiene solo dos miembros de datos (un identificador de ventana y las dimensiones predeterminadas), no se impone una sobrecarga en el código. Además, muchos de los `CWindow` métodos simplemente encapsulan las funciones de API de Win32 correspondientes. Mediante el uso de `CWindow`, el miembro HWND se pasa automáticamente a la función de Win32.

Además de utilizar `CWindow` directamente, también puede derivar de ella para agregar datos o código a la clase. ATL deriva tres clases de `CWindow`: [CWindowImpl](../atl/implementing-a-window.md), [CDialogImpl](../atl/implementing-a-dialog-box.md), y [CContainedWindowT](../atl/using-contained-windows.md).

## <a name="see-also"></a>Vea también

[Clases de ventana](../atl/atl-window-classes.md)

