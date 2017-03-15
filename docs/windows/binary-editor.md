---
title: "Binary Editor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.binary.F1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "editors, Binary"
  - "resources [Visual Studio], editing"
  - "resource editors, Binary editor"
  - "Binary editor"
ms.assetid: 2483c48b-1252-4dbc-826b-82e6c1a0e9cb
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Binary Editor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!WARNING]
>  El Editor binario no está disponible en las ediciones Express.  
  
 El Editor binario permite editar cualquier recurso, a nivel binario, en formato ASCII o hexadecimal. También se puede utilizar el [comando Buscar](../Topic/Find%20Command.md) para buscar cadenas ASCII o bytes hexadecimales. Solo se debe utilizar el Editor binario cuando sea necesario ver o realizar pequeños cambios en recursos personalizados o en tipos de recursos no admitidos en el entorno de Visual Studio.  
  
 Para abrir el Editor binario, elija **Archivo &#124; New &#124; Archivo** en el menú principal, seleccione el archivo que desea editar, haga clic en la flecha desplegable situada junto al botón **Abrir** y elija **Abrir con &#124; Editor binario**.  
  
> [!CAUTION]
>  Es peligroso editar recursos como cuadros de diálogo, imágenes o menús en el Editor binario. Una edición incorrecta podría dañar el recurso y hacerlo ilegible en su editor nativo.  
  
> [!TIP]
>  Cuando se trabaja en el Editor binario, en muchos casos es posible hacer clic con el botón secundario para abrir un menú contextual de comandos específicos de un recurso. Los comandos disponibles dependen del objeto al que apunta el cursor. Por ejemplo, si se hace clic mientras se apunta al Editor binario teniendo seleccionados valores hexadecimales, el menú contextual muestra los comandos **Cortar**, **Copiar** y **Pegar**.  
  
 Con el Editor binario, se puede hacer lo siguiente:  
  
-   [Abrir un recurso para editarlo en modo binario](../mfc/opening-a-resource-for-binary-editing.md)  
  
-   [Editar datos binarios](../mfc/editing-binary-data.md)  
  
-   [Buscar datos binarios](../mfc/finding-binary-data.md)  
  
-   [Crear un nuevo recurso personalizado o de datos](../mfc/creating-a-new-custom-or-data-resource.md)  
  
## Recursos administrados  
 Se puede utilizar el [Editor de imágenes](../mfc/image-editor-for-icons.md) y el Editor binario para trabajar con archivos de recursos en proyectos administrados. Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, obtener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
### Requisitos  
 Ninguno  
  
## Vea también  
 [Resource Editors](../mfc/resource-editors.md)