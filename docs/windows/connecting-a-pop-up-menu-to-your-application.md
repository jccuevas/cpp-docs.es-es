---
title: Conectar un menú emergente a una aplicación de C++
ms.date: 11/04/2016
helpviewer_keywords:
- pop-up menus [C++], connecting to applications
- context menus [C++], connecting to applications
- menus [C++], pop-up
- shortcut menus [C++], connecting to applications
ms.assetid: 295cbf0e-6416-478e-bc3d-472fb98e0e52
ms.openlocfilehash: 8a0cb64caaa58b464b0d5abb52093350c5e3cfeb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556499"
---
# <a name="connecting-a-pop-up-menu-to-your-c-application"></a>Conectar un menú emergente a una aplicación de C++

### <a name="to-connect-a-pop-up-menu-to-your-application"></a>Para conectar un menú emergente a una aplicación

1. Agregue un controlador de mensajes para WM_CONTEXTMENU (por ejemplo). Para obtener más información, consulte [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md).

2. Agregue el código siguiente al controlador de mensajes:

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > El [CPoint](../atl-mfc-shared/reference/cpoint-class.md) pasa por el mensaje de controlador está en coordenadas de pantalla.

## <a name="requirements"></a>Requisitos

MFC

## <a name="see-also"></a>Vea también

[Creación de menús emergentes](../windows/creating-pop-up-menus.md)<br/>
[Editor de menús](../windows/menu-editor.md)