---
title: "Custom Controls in the Dialog Editor | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Custom Control"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controls [C++], templates"
  - "custom controls [Visual Studio], dialog boxes"
  - "custom controls [Visual Studio]"
  - "dialog box controls, custom (user) controls"
  - "Dialog editor, custom controls"
ms.assetid: f494b314-4000-4bbe-bbd0-4b18fb71ede1
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Custom Controls in the Dialog Editor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El Editor de cuadros de diálogo permite utilizar controles existentes "personalizados" o "del usuario" en una plantilla de cuadro de diálogo.  
  
> [!NOTE]
>  A este respecto, los controles personalizados no deben confundirse con los controles ActiveX,  que a veces reciben la denominación de controles personalizados OLE.  Asimismo, no se deben confundir estos controles con los controles de Windows dibujados por el propietario.  
  
 Esta funcionalidad está diseñada para permitir el uso de controles distintos de los suministrados con Windows.  En tiempo de ejecución, el control se asocia a una clase de ventana \(que no es lo mismo que una clase de C\+\+\).  Un medio más corriente para lograr el mismo resultado consiste en instalar en el cuadro de diálogo un control cualquiera, por ejemplo, un control estático.  Después, en tiempo de ejecución, en la función [OnInitDialog](../Topic/CDialog::OnInitDialog.md), se quita el control y se reemplaza con un control personalizado propio.  
  
 Esta técnica está anticuada.  Hoy día, en casi todos los casos se aconseja escribir un control ActiveX o una subclase de un control común de Windows.  
  
 Con estos controles personalizados, sólo puede hacerse lo siguiente:  
  
-   Establecer la ubicación en el cuadro de diálogo.  
  
-   Escribir un título.  
  
-   Identificar el nombre de la clase de Windows del control \(el código de la aplicación debe registrar el control por su nombre\).  
  
-   Escribir un valor hexadecimal de 32 bits que establezca el estilo del control.  
  
-   Establecer el estilo extendido.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
## Requisitos  
 Win32  
  
## Vea también  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [Controles](../mfc/controls-mfc.md)