---
title: "Creating a Menu | Microsoft Docs"
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
  - "vc.editors.menu"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mnemonics, associating menu items"
  - "menus, associating commands with mnemonic keys"
  - "menus, creating"
ms.assetid: 66f94448-9b97-4b73-bf97-10d4bf87cc65
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating a Menu
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  La ventana de recursos no está disponible en las ediciones Express.  
  
### Para crear un menú estándar  
  
1.  En el menú **Ver**, haga clic en **Vista de recursos** y, a continuación, haga clic con el botón secundario en el encabezado **Menú** y elija **Agregar recurso**. Elija **Menú**.  
  
2.  Seleccione el cuadro **Nuevo elemento** \(el rectángulo que contiene "Escriba aquí"\) en la barra de menús.  
  
     ![Cuadro Nuevo elemento del editor de menús](../windows/media/vcmenueditornewitembox.png "vcMenuEditorNewItemBox")  
Cuadro Nuevo elemento  
  
3.  Escriba un nombre para el nuevo menú, por ejemplo, "Archivo".  
  
     El texto que escriba aparecerá en el **Editor de menús** y en el cuadro **Leyenda** de la [ventana Propiedades](../Topic/Properties%20Window.md). Puede editar las propiedades del nuevo menú en uno u otro componente.  
  
     Tras asignar un nombre al nuevo menú en la barra de menús, el cuadro de nuevo elemento se desplaza hacia la derecha \(para permitir agregar otro menú\) y se abre otro cuadro de nuevo elemento debajo del primer menú, donde pueden agregarse otros comandos de menú.  
  
     ![Cuadro Nuevo elemento expandido](../windows/media/vcmenueditornewitemboxexpanded.png "vcMenuEditorNewItemBoxExpanded")  
Cuadro Nuevo elemento con el foco desplazado al escribir el nombre del nuevo menú  
  
    > [!NOTE]
    >  Para crear un menú de un solo elemento en la barra de menús, establezca la propiedad Popup en False.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, obtener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 **Requisitos**  
  
 Win32  
  
## Vea también  
 [Menu Editor](../mfc/menu-editor.md)