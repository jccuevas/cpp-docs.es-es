---
title: "Accelerator Editor | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.accelerator.F1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "accelerator tables [C++], editing"
  - "tables [Visual Studio], accelerator key"
  - "accelerator keys"
  - "resource editors, Accelerator editor"
  - "keyboard shortcuts [C++], Accelerator editor"
  - "Accelerator editor"
ms.assetid: 013c30b6-5d61-4f1c-acef-8bd15bed7060
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Accelerator Editor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una tabla de aceleradores es un recurso de Windows que contiene una lista de teclas de aceleración \(también conocidas como teclas de método abreviado\) y los identificadores de comandos asociados con ellas. Un programa puede tener más de una tabla de aceleradores.  
  
 Normalmente, los aceleradores se usan como métodos abreviados de teclado para comandos de programa que también están disponibles en un menú o una barra de herramientas. Sin embargo, puede usar la tabla de aceleradores para definir las combinaciones de teclas para los comandos que no tienen asociado un objeto de interfaz de usuario.  
  
 Puede usar la [Vista de clases](http://msdn.microsoft.com/es-es/8d7430a9-3e33-454c-a9e1-a85e3d2db925) para enlazar comandos de teclas de aceleración al código.  
  
 Con el editor de aceleradores, puede:  
  
-   [Establecer propiedades de acelerador](../windows/setting-accelerator-properties.md)  
  
-   [Asociar una tecla de aceleración a un elemento de menú](../windows/associating-an-accelerator-key-with-a-menu-item.md)  
  
-   [Editar tablas de aceleradores](../windows/editing-accelerator-tables.md)  
  
-   [Usar teclas de aceleración predefinidas](../windows/predefined-accelerator-keys.md)  
  
    > [!TIP]
    >  Al usar el Editor de aceleradores, puede hacer clic con el botón secundario para mostrar un menú contextual de los comandos usados con mayor frecuencia. Los comandos disponibles dependen del objeto al que apunta el puntero.  
  
    > [!NOTE]
    >  Windows no permite crear tablas de aceleradores vacías. Si crea una tabla de aceleradores sin entradas, se elimina automáticamente al guardar la tabla.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, obtener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
## Requisitos  
 Win32  
  
## Vea también  
 [Resource Editors](../mfc/resource-editors.md)