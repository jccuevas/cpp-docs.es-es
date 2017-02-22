---
title: "Portapapeles: Usar el Portapapeles de Windows | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Portapapeles [C++], comandos"
  - "Portapapeles [C++], API del Portapapeles de Windows"
  - "comandos del Portapapeles"
  - "comandos del Portapapeles, implementar"
  - "comandos [C++], implementar Edición"
  - "funciones del controlador para el comando Cortar/Copiar y pegar"
  - "funciones controladoras, comandos Cortar/Copiar y pegar"
  - "Portapapeles de Windows [C++]"
ms.assetid: 24415b42-9301-4a70-b69a-44c97918319f
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Portapapeles: Usar el Portapapeles de Windows
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema se describe cómo utilizar el Portapapeles de Windows estándar API dentro de la aplicación MFC.  
  
 La mayoría de las aplicaciones para cortar o copiar datos en el Portapapeles de Windows y pegar de soporte de Windows datos del portapapeles.  Los formatos de datos del portapapeles varían entre aplicaciones.  El marco solo admite un número limitado de formatos del Portapapeles para un número limitado de clases.  Implementará normalmente los comandos Portapapeles\- relacionados — cortar, copiar, pegar y — en el menú Edición de la vista.  La biblioteca de clases define los id. de comando para estos comandos: **ID\_EDIT\_CUT**, **ID\_EDIT\_COPY**, y **ID\_EDIT\_PASTE**.  Los marcadores de la línea de mensajes también se definen.  
  
 [Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md) explica cómo controlar los comandos de menú de la aplicación asignando el comando de menú en una función de controlador.  Mientras la aplicación no defina las funciones controladoras para los comandos del portapapeles en el menú Edición, permanecen deshabilitadas.  Para escribir funciones controladoras para los comandos cortar y de copia, implemente la selección en la aplicación.  Para escribir una función controladora para el comando pegar, vea el portapapeles para ver si contiene datos en un formato que la aplicación puede aceptar.  Por ejemplo, para habilitar el comando de copia, puede escribir a controlador algo parecido a:  
  
 [!code-cpp[NVC_MFCListView#2](../mfc/codesnippet/CPP/clipboard-using-the-windows-clipboard_1.cpp)]  
  
 Los comandos cortar, copy, y pegar solo son significativos en ciertos contextos.  Los comandos cortar y de copia deben estar habilitados cuando algo está seleccionado, y el comando pegar cuando algo está en el portapapeles.  Puede proporcionar este comportamiento definiendo las funciones de controlador de actualización que habilitan o deshabilitan estos comandos dependiendo del contexto.  Para obtener más información, vea [Cómo actualizar objetos de la Usuario\-interfaz](../mfc/how-to-update-user-interface-objects.md).  
  
 La biblioteca Microsoft Foundation Class proporciona compatibilidad del portapapeles para la modificación de texto con las clases de `CEdit` y de `CEditView` .  Las clases VIEJAS también simplifican implementar las operaciones del portapapeles que implican elementos de OLE.  Para obtener más información sobre las clases VIEJAS, vea [Portapapeles: Utilizar el portapapeles OLE Mechanism](../mfc/clipboard-using-the-ole-clipboard-mechanism.md).  
  
 Implementar otros comandos de menú de edición, como undo \(**ID\_EDIT\_UNDO**\) y rehacer \(**ID\_EDIT\_REDO**\), también se permite se.  Si la aplicación no admite estos comandos, es fácil eliminarlos del archivo de recursos mediante los editores de recursos de Visual C\+\+.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Copiando y pegando datos](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [Mediante el mecanismo OLE del portapapeles](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)  
  
## Vea también  
 [Portapapeles](../mfc/clipboard.md)