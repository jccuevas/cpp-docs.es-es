---
title: Crear menús emergentes | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- context menus, Menu Editor
- pop-up menus, creating
- menus, pop-up
- menus, creating
- shortcut menus, creating
- pop-up menus, displaying
ms.assetid: dff4dddf-2e8d-4c34-b755-90baae426b58
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 218ed28a8b44100beead46ab13e04ad07d86c7e5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="creating-pop-up-menus"></a>Crear menús emergentes
Los[menús emergentes](../mfc/menus-mfc.md) muestran comandos de pantalla que se utilizan con frecuencia. Pueden ser contextuales con respecto a la ubicación del puntero. Utilizar menús emergentes en la aplicación requiere compilar el menú y, a continuación, conectarlo al código de la aplicación.  
  
 Una vez creado el recurso de menú, el código de la aplicación debe cargar el recurso y usar [TrackPopupMenu](http://msdn.microsoft.com/library/windows/desktop/ms648002) para que aparezca el menú. Cuando el usuario descarte el menú emergente al hacer clic fuera de él o en un comando, se devolverá esa función. Si el usuario elige un comando, se enviará el mensaje de ese comando a la ventana cuyo controlador se ha pasado.  
  
### <a name="to-create-a-pop-up-menu"></a>Para crear un menú emergente  
  
1.  [Cree un menú](../windows/creating-a-menu.md) con un título vacío (no proporcione ningún **Título**).  
  
2.  [Agregue un comando de menú al menú nuevo](../windows/adding-commands-to-a-menu.md). Desplácese al primer comando de menú, bajo el título de menú en blanco (el título provisional dice Escriba aquí). Escriba un **Título** y cualquier otra información.  
  
     Repita este proceso para los demás comandos de menú del menú emergente.  
  
3.  Guarde el recurso de menú.  
  
    > [!TIP]
    >  Para obtener más información acerca de cómo ver el menú emergente, consulte [Ver un menú como menú emergente](../windows/viewing-a-menu-as-a-pop-up-menu.md).  
  

  
 **Requisitos**  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Conectar un menú emergente a una aplicación](../windows/connecting-a-pop-up-menu-to-your-application.md)   
 [Editor de menús](../windows/menu-editor.md)