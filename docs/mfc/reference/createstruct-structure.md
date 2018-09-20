---
title: CREATESTRUCT (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CREATESTRUCT
dev_langs:
- C++
helpviewer_keywords:
- CREATESTRUCT structure [MFC]
ms.assetid: 028c7b5e-4fdc-48da-a550-d3e4f9e6cc85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 880cbbde261caf804e16e9eb759abb213cb84f60
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422433"
---
# <a name="createstruct-structure"></a>CREATESTRUCT (Estructura)

El `CREATESTRUCT` estructura define los parámetros de inicialización pasados al procedimiento de ventana de una aplicación.

## <a name="syntax"></a>Sintaxis

```
typedef struct tagCREATESTRUCT {
    LPVOID lpCreateParams;
    HANDLE hInstance;
    HMENU hMenu;
    HWND hwndParent;
    int cy;
    int cx;
    int y;
    int x;
    LONG style;
    LPCSTR lpszName;
    LPCSTR lpszClass;
    DWORD dwExStyle;
} CREATESTRUCT;
```

#### <a name="parameters"></a>Parámetros

*lpCreateParams*<br/>
Puntos de datos que se usará para crear la ventana.

*hInstance*<br/>
Identifica el identificador de instancia de módulo del módulo que posee la ventana nueva.

*hMenu*<br/>
Identifica el menú que va a usar la nueva ventana. Si una ventana secundaria, contiene el identificador entero.

*hwndParent*<br/>
Identifica la ventana que posee la ventana nueva. Este miembro es NULL si la nueva ventana es una ventana de nivel superior.

*CY*<br/>
Especifica el alto de la nueva ventana.

*CX*<br/>
Especifica el ancho de la nueva ventana.

*y*<br/>
Especifica la coordenada y de la esquina superior izquierda de la nueva ventana. Las coordenadas son relativas a la ventana principal si la nueva ventana es una ventana secundaria; en caso contrario, las coordenadas son en relación con el origen de la pantalla.

*x*<br/>
Especifica la coordenada x de la esquina superior izquierda de la nueva ventana. Las coordenadas son relativas a la ventana principal si la nueva ventana es una ventana secundaria; en caso contrario, las coordenadas son en relación con el origen de la pantalla.

*Estilo*<br/>
Especifica la nueva ventana [estilo](../../mfc/reference/styles-used-by-mfc.md).

*lpszName*<br/>
Apunta a una cadena terminada en null que especifica el nombre de la ventana nueva.

*lpszClass*<br/>
Señala a una cadena terminada en null que especifica el nombre de la ventana nueva de la clase de Windows (un [WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576) estructura; para obtener más información, consulte el SDK de Windows).

*dwExStyle*<br/>
Especifica el [estilo extendido](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) para la nueva ventana.

## <a name="requirements"></a>Requisitos

**Encabezado:** winuser.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)


