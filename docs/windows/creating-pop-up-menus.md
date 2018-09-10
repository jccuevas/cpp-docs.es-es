---
title: Crear menús emergentes (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- context menus [C++], Menu Editor
- pop-up menus [C++], creating
- menus [C++], pop-up
- menus [C++], creating
- shortcut menus [C++], creating
- pop-up menus [C++], displaying
ms.assetid: dff4dddf-2e8d-4c34-b755-90baae426b58
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3fd2fcc5fc8603f265fa2d213325227baecd7f5d
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313773"
---
# <a name="creating-pop-up-menus-c"></a>Crear menús emergentes (C++)

Los[menús emergentes](../mfc/menus-mfc.md) muestran comandos de pantalla que se utilizan con frecuencia. Pueden ser contextuales con respecto a la ubicación del puntero. Utilizar menús emergentes en la aplicación requiere compilar el menú y, a continuación, conectarlo al código de la aplicación.

Una vez haya creado el recurso de menú, el código de aplicación debe cargar el recurso y usar [TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu) para que aparezca el menú. Cuando el usuario descarte el menú emergente al hacer clic fuera de él o en un comando, se devolverá esa función. Si el usuario elige un comando, se enviará el mensaje de ese comando a la ventana cuyo controlador se ha pasado.

### <a name="to-create-a-pop-up-menu"></a>Para crear un menú emergente

1. [Cree un menú](../windows/creating-a-menu.md) con un título vacío (no proporcione ningún **Título**).

2. [Agregue un comando de menú al menú nuevo](../windows/adding-commands-to-a-menu.md). Mover al primer comando de menú debajo del título de menú en blanco (el título provisional dice `Type Here`). Escriba un **Título** y cualquier otra información.

   Repita este proceso para los demás comandos de menú del menú emergente.

3. Guarde el recurso de menú.

   > [!TIP]
   > Para obtener más información acerca de cómo ver el menú emergente, consulte [Ver un menú como menú emergente](../windows/viewing-a-menu-as-a-pop-up-menu.md).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Conexión de un menú emergente a la aplicación](../windows/connecting-a-pop-up-menu-to-your-application.md)  
[Editor de menús](../windows/menu-editor.md)