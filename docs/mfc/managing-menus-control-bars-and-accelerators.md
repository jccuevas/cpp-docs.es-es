---
title: "Administrar menús, barras de Control y aceleradores | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 74b026f273eec0bc689cc6959890b07beb570893
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="managing-menus-control-bars-and-accelerators"></a>Administrar menús, barras de control y aceleradores
La ventana de marco administra la actualización de los objetos de interfaz de usuario, incluidos los menús, botones de barra de herramientas, la barra de estado y aceleradores. También administra el uso compartido de la barra de menús en aplicaciones MDI.  
  
## <a name="managing-menus"></a>Administrar menús  
 La ventana de marco participa en la actualización de elementos de interfaz de usuario mediante la `ON_UPDATE_COMMAND_UI` mecanismo se describe en [cómo actualizar objetos de interfaz de usuario](../mfc/how-to-update-user-interface-objects.md). Botones de barras de herramientas y otras barras de control se actualizan durante el bucle de inactividad. Elementos de menú en los menús de lista desplegable en la barra de menús se actualizan justo antes de que el menú se despliega hacia abajo.  
  
 Para las aplicaciones MDI, la ventana de marco MDI administra la barra de menús y el título. Una ventana de marco MDI posee un menú predeterminado que se utiliza como la barra de menús cuando no hay ningún activas ventanas secundarias MDI. Cuando hay secundarias activas, barra de menús de la ventana de marco MDI se traspasa al menú para la ventana secundaria MDI activa. Si una aplicación MDI admite varios tipos de documentos, como los documentos de gráfico y la hoja de cálculo, cada tipo incluye sus propios menús en la barra de menús y cambia el título de la ventana de marco principal.  
  
 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) proporciona implementaciones predeterminadas para los comandos estándares del menú Ventana que aparece para las aplicaciones MDI. En particular, el comando nueva ventana (**ID_WINDOW_NEW**) se implementa para crear una nueva ventana de marco y la vista en el documento actual. Debe invalidar estas implementaciones sólo si necesita personalización avanzada.  
  
 Las ventanas secundarias MDI del mismo tipo de documento comparten recursos de menú. Si varias ventanas secundarias MDI se crean mediante la misma plantilla de documento, todas pueden utilizar el mismo recurso de menú, ahorrando recursos de sistema de Windows.  
  
## <a name="managing-the-status-bar"></a>Administración de la barra de estado  
 La ventana de marco también coloca la barra de estado dentro de su área cliente y administra el estado de los indicadores de la barra. La ventana de marco borra el área de mensajes en la barra de estado se actualiza según sea necesario y muestra cadenas de mensajes, como el usuario selecciona elementos de menú o botones de barra de herramientas, como se describe en [cómo mostrar información de comandos en la barra de estado](../mfc/how-to-display-command-information-in-the-status-bar.md).  
  
## <a name="managing-accelerators"></a>Administración de aceleradores  
 Cada ventana de marco mantiene una tabla de aceleradores opcional que teclado traducción de acelerador en su lugar automáticamente. Este mecanismo resulta muy sencillo definir teclas de aceleración (también denominadas teclas de método abreviado) que invocación comandos de menú.  
  
## <a name="see-also"></a>Vea también  
 [Uso de ventanas de marco](../mfc/using-frame-windows.md)

