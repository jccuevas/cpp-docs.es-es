---
title: Administrar menús, barras de control y aceleradores
ms.date: 11/04/2016
helpviewer_keywords:
- MDI [MFC], frame windows
- control bars [MFC], updating in frame windows
- menus [MFC], updating as context changes
- user interface objects [MFC], updating
- accelerator tables [MFC]
- sharing menus [MFC]
- updating user-interface objects [MFC]
- frame windows [MFC], updating
- status bars [MFC], updating
ms.assetid: 97ca1997-06df-4373-b023-4f7ecd81047b
ms.openlocfilehash: 9945dc68ffd46bbf5e114a79467299e4b67e3659
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621329"
---
# <a name="managing-menus-control-bars-and-accelerators"></a>Administrar menús, barras de control y aceleradores

La ventana de marco administra la actualización de los objetos de la interfaz de usuario, incluidos los menús, los botones de la barra de herramientas, la barra de estado y los aceleradores. También administra el uso compartido de la barra de menús en aplicaciones MDI.

## <a name="managing-menus"></a>Administrar menús

La ventana de marco participa en la actualización de los elementos de la interfaz de usuario mediante el mecanismo ON_UPDATE_COMMAND_UI descrito en [How to update User-Interface Objects](how-to-update-user-interface-objects.md). Los botones de las barras de herramientas y otras barras de control se actualizan durante el bucle inactivo. Los elementos de menú de los menús desplegables de la barra de menús se actualizan justo antes de que el menú se despliega.

En el caso de las aplicaciones MDI, la ventana de marco MDI administra la barra de menús y el título. Una ventana de marco MDI posee un menú predeterminado que se utiliza como barra de menús cuando no hay ventanas secundarias MDI activas. Cuando hay elementos secundarios activos, la barra de menús de la ventana de marco MDI se toma en el menú de la ventana secundaria MDI activa. Si una aplicación MDI admite varios tipos de documentos, como documentos de gráfico y de hoja de cálculo, cada tipo coloca sus propios menús en la barra de menús y cambia el título de la ventana de marco principal.

[CMDIFrameWnd](reference/cmdiframewnd-class.md) proporciona implementaciones predeterminadas para los comandos estándar en el menú ventana que aparece para aplicaciones MDI. En concreto, el comando nueva ventana (ID_WINDOW_NEW) se implementa para crear una nueva ventana de marco y una vista en el documento actual. Debe invalidar estas implementaciones solo si necesita personalización avanzada.

Varias ventanas secundarias MDI del mismo tipo de documento comparten recursos de menú. Si varias ventanas secundarias MDI se crean mediante la misma plantilla de documento, todas pueden utilizar el mismo recurso de menú, guardando los recursos del sistema en Windows.

## <a name="managing-the-status-bar"></a>Administrar la barra de estado

La ventana marco también coloca la barra de estado dentro de su área cliente y administra los indicadores de la barra de estado. La ventana de marco borra y actualiza el área de mensajes en la barra de estado según sea necesario y muestra las cadenas de mensajes cuando el usuario selecciona elementos de menú o botones de la barra de herramientas, como se describe en [Cómo mostrar la información de comandos en la barra de estado](how-to-display-command-information-in-the-status-bar.md).

## <a name="managing-accelerators"></a>Administración de aceleradores

Cada ventana de marco mantiene una tabla de aceleradores opcional que realiza automáticamente la traducción del acelerador del teclado. Este mecanismo facilita la definición de teclas de aceleración (también denominadas teclas de método abreviado) que invocan comandos de menú.

## <a name="see-also"></a>Consulte también

[Usar ventanas de marco](using-frame-windows.md)
