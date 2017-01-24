---
title: "Administrar men&#250;s, barras de control y aceleradores | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tablas de aceleradores [C++]"
  - "barras de control, actualizar en ventanas de marco"
  - "ventanas de marco, actualizar"
  - "MDI, ventanas de marco"
  - "menús, actualizar cuando el contexto cambia"
  - "compartir menús"
  - "barras de estado, actualizar"
  - "actualizar objetos de la interfaz de usuario"
  - "objetos de interfaz de usuario, actualizar"
ms.assetid: 97ca1997-06df-4373-b023-4f7ecd81047b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Administrar men&#250;s, barras de control y aceleradores
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La ventana de marco administra actualizar objetos de interfaz de usuario, como menús, botones de la barra de herramientas, la barra de estado, y los aceleradores.  También administra compartir la barra de menús en las aplicaciones MDI.  
  
## Administrar menús  
 La ventana de marco participa en actualizar los elementos de la interfaz de usuario utilizando el mecanismo de `ON_UPDATE_COMMAND_UI` descrito en [Cómo actualizar objetos de la Usuario\-interfaz](../mfc/how-to-update-user-interface-objects.md).  Los botones de las barras de herramientas y otras barras de control se actualizan durante el bucle inactivo.  Los elementos de menú en menús desplegables en la barra de menús se actualizan justo antes del menú afectan a continuación.  
  
 Para las aplicaciones MDI, la ventana de marco MDI administra la barra de menús y la leyenda.  Una ventana de marco MDI posee un menú predeterminado que se utiliza como la barra de menús cuando no hay ventanas secundarias MDI activo.  Cuando hay elementos secundarios activos, la barra de menús de MDI de la ventana de marco es asumida el control mediante el menú de la ventana secundaria MDI activo.  Si una aplicación MDI admite tipos de documento múltiples, como documentos de gráfico y de hoja de cálculo, cada tipo colocar sus propios menús en la barra de menús y cambia la leyenda de la ventana de marco principal.  
  
 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) proporciona implementaciones predeterminadas para los comandos estándar del menú Ventana que aparece para las aplicaciones MDI.  En particular, implementan el comando nueva ventana \(**ID\_WINDOW\_NEW**\) para crear una nueva ventana y vista de marco en el documento actual.  Necesita reemplazar estas implementaciones sólo si necesita la personalización avanzada.  
  
 Las ventanas secundarias de MDI del mismo tipo de documento comparten recursos de menú.  Si varias ventanas secundarias MDI son creadas por la misma plantilla de documento, pueden todas usan el mismo recurso de menú, guardando en recursos del sistema de Windows.  
  
## Administrar la barra de estado  
 En el cuadro de la ventana las posiciones también la barra de estado dentro del área cliente y administran los indicadores de barra de estado.  La ventana de marco borra y actualiza el área de mensajes de la barra de estado según sea necesario y cadenas de mensajes de se muestra como el usuario selecciona elementos de menú o los botones de la barra de herramientas, como se describe en [Cómo mostrar la información del comando en la barra de estado](../mfc/how-to-display-command-information-in-the-status-bar.md).  
  
## Administrar los Aceleradores  
 Cada ventana de marco mantiene una tabla opcional de aceleradores que haga la traducción de aceleradores de teclado automáticamente.  Este mecanismo facilita definir teclas de aceleración \(también denominadas teclas de método abreviado\) que invocan comandos de menú.  
  
## Vea también  
 [Usar ventanas de marco](../mfc/using-frame-windows.md)