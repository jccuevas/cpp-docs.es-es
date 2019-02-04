---
title: Crear menús emergentes (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- context menus [C++], Menu Editor
- pop-up menus [C++], creating
- menus [C++], pop-up
- menus [C++], creating
- shortcut menus [C++], creating
- pop-up menus [C++], displaying
- pop-up menus [C++], connecting to applications
- context menus [C++], connecting to applications
- shortcut menus [C++], connecting to applications
- pop-up menus
ms.assetid: dff4dddf-2e8d-4c34-b755-90baae426b58
ms.openlocfilehash: cf2e3578f49cb6b4af8797052273211f699a6b4f
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702835"
---
# <a name="creating-pop-up-menus-c"></a>Crear menús emergentes (C++)

Los[menús emergentes](../mfc/menus-mfc.md) muestran comandos de pantalla que se utilizan con frecuencia. Pueden ser contextuales con respecto a la ubicación del puntero. Utilizar menús emergentes en la aplicación requiere compilar el menú y, a continuación, conectarlo al código de la aplicación.

Una vez haya creado el recurso de menú, el código de aplicación debe cargar el recurso y usar [TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu) para que aparezca el menú. Una vez que el usuario descarte el menú emergente seleccionando fuera de él, o ha seleccionado un comando, se devolverá esa función. Si el usuario elige un comando, se enviará el mensaje de ese comando a la ventana cuyo controlador se ha pasado.

## <a name="to-create-a-pop-up-menu"></a>Para crear un menú emergente

1. [Cree un menú](../windows/creating-a-menu.md) con un título vacío (no proporcione ningún **Título**).

1. [Agregue un comando de menú al menú nuevo](../windows/adding-commands-to-a-menu.md). Mover al primer comando de menú debajo del título de menú en blanco (el título provisional dice `Type Here`). Escriba un **Título** y cualquier otra información.

   Repita este proceso para los demás comandos de menú del menú emergente.

1. Guarde el recurso de menú.

## <a name="to-connect-a-pop-up-menu-to-your-application"></a>Para conectar un menú emergente a una aplicación

1. Agregue un controlador de mensajes para WM_CONTEXTMENU (por ejemplo). Para obtener más información, consulte [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md).

1. Agregue el código siguiente al controlador de mensajes:

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > El [CPoint](../atl-mfc-shared/reference/cpoint-class.md) pasa por el mensaje de controlador está en coordenadas de pantalla.

   > [!NOTE]
   > Conectar un menú emergente a una aplicación requiere MFC.

## <a name="to-view-a-menu-resource-as-a-pop-up-menu"></a>Para ver un recurso de menú como menú emergente

Normalmente, cuando esté trabajando el **menú** editor, un recurso de menú se muestra como una barra de menús. Sin embargo, es posible que algunos recursos de menú se agreguen a la barra de menús de la aplicación mientras se ejecuta el programa.

El menú contextual y elija **ver como emergente** en el menú contextual.

   Esta opción es sólo una preferencia de visualización y no modificará su menú.

   > [!NOTE]
   > Para cambiar a la vista de la barra de menús, haga clic en **ver como emergente** nuevo (que quita la marca de verificación y devuelve la vista de la barra de menús).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de menús](../windows/menu-editor.md)
