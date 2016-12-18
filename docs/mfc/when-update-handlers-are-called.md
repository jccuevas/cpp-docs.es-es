---
title: "Cu&#225;ndo se llama a los controladores actualizados | Microsoft Docs"
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
  - "enrutamiento de comandos, comandos de actualización"
  - "enrutamiento de comandos, controladores de actualización"
  - "deshabilitar elementos de menú"
  - "deshabilitar botones de barra de herramientas"
  - "elementos de menú, habilitar"
  - "menús [C++], inicializar"
  - "menús [C++], actualizar cuando el contexto cambia"
  - "botones de barra de herramientas [C++], habilitar"
  - "controles de barra de herramientas [MFC], actualizar durante el método OnIdle"
  - "barras de herramientas [C++], actualizar"
  - "controladores de actualización"
  - "controladores de actualización, llamar"
  - "actualizar objetos de la interfaz de usuario"
ms.assetid: 7359f6b1-4669-477d-bd99-690affed08d9
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Cu&#225;ndo se llama a los controladores actualizados
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Suponga que el usuario hace clic en el menú archivo, que genera un mensaje de `WM_INITMENUPOPUP` .  El mecanismo de actualización de marco de trabajo actualiza colectivamente todos los elementos del menú archivo antes de que el menú interrumpa abajo para que el usuario puede verlo.  
  
 Para ello, las rutas de marco actualizan los comandos para todos los elementos de menú del menú emergente a lo largo de enrutamiento estándar del comando.  Los destinos de comando en el enrutamiento tienen la oportunidad de actualizar los elementos de menú haciendo coincidir el comando de actualización con una entrada adecuada del mensaje\- mapa \(del formulario `ON_UPDATE_COMMAND_UI`\) y llamando a “una función controladora de actualización”.  Por tanto, para un menú con seis elementos de menú, envían a seis comandos actualizados.  Si un controlador de actualización existe para el identificador del elemento de menú, se llama a para hacer actualizar.  Si no, las comprobaciones de marco la existencia de un controlador para este identificador de comando y habilitan o deshabilitan el elemento de menú según corresponda.  
  
 Si el marco no encuentra una entrada de `ON_UPDATE_COMMAND_UI` durante el enrutamiento de comandos, habilita automáticamente el objeto de la interfaz de usuario si hay una entrada de `ON_COMMAND` en alguna parte con el mismo identificador de comando  Si no, deshabilita el objeto de la interfaz de usuario.  Por consiguiente, para asegurarse de que un objeto de la interfaz de usuario está habilitado, proporcione un controlador para el comando que el objeto genera o proporcione un controlador de actualización para él.  Vea la ilustración del tema [Objeto de la interfaz de usuario y id. de comando](../mfc/user-interface-objects-and-command-ids.md).  
  
 Es posible deshabilitar deshabilitar predeterminado de los objetos de la interfaz de usuario.  Para obtener más información, vea el miembro de [m\_bAutoMenuEnable](../Topic/CFrameWnd::m_bAutoMenuEnable.md) de la clase `CFrameWnd` en *la referencia de MFC*.  
  
 La inicialización de menú es automática en el marco, produciendo cuando la aplicación recibe un mensaje de `WM_INITMENUPOPUP` .  Durante el bucle inactivo, el marco busca el enrutamiento de comandos para los controladores de actualización del botón de la misma forma que hace de los menús.  
  
## Vea también  
 [Cómo: Actualizar objetos de la interfaz de usuario](../mfc/how-to-update-user-interface-objects.md)