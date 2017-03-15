---
title: "Changing the Properties of Multiple Accelerator Keys | Microsoft Docs"
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
  - "keyboard shortcuts [C++], property changing"
  - "accelerator tables [C++], changing properties"
ms.assetid: b55c9bd6-b430-48bb-b942-0e6f21d7abf9
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Changing the Properties of Multiple Accelerator Keys
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### Para cambiar las propiedades de varias teclas de aceleración  
  
1.  Abra la tabla de aceleradores haciendo doble clic en su icono en la [Vista de recursos](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Seleccione las teclas de aceleración que desee cambiar manteniendo presionada la tecla **CTRL** mientras hace clic en ellas.  
  
3.  Vaya a la [ventana Propiedades](../Topic/Properties%20Window.md) y escriba los valores que deban compartir todos los aceleradores seleccionados.  
  
    > [!NOTE]
    >  Los valores de los modificadores se muestran como propiedades de tipo Boolean en la ventana Propiedades.  Si cambia el valor de un modificador \([Modifier](../windows/accelerator-modifier-property.md)\) en la ventana Propiedades, la tabla de aceleradores tratará al nuevo modificador como una adición a los modificadores que previamente contenía.  A causa de esto, si desea definir el valor de otros modificadores, deberá definir el de todos ellos para asegurarse de que todos los aceleradores compartan la misma configuración de modificador \(Modifier\).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 **Requisitos**  
  
 Win32  
  
## Vea también  
 [Editing Accelerator Tables](../windows/editing-accelerator-tables.md)   
 [Accelerator Editor](../mfc/accelerator-editor.md)