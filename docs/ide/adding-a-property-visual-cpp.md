---
title: "Agregar una propiedad (Visual C++) | Microsoft Docs"
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
  - "interfaces, agregar propiedades"
  - "propiedades [C++], agregar a interfaces"
ms.assetid: 37bd4db7-efd3-4faa-87ad-64902ed16a36
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Agregar una propiedad (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede utilizar el [Asistente para agregar propiedades](../ide/names-add-property-wizard.md) con el fin de agregar una propiedad a una interfaz del proyecto.  
  
### Para agregar una propiedad al objeto  
  
1.  En [Vista de clases](http://msdn.microsoft.com/es-es/8d7430a9-3e33-454c-a9e1-a85e3d2db925), haga clic con el botón secundario en el nombre de la interfaz en la que desee agregar la propiedad.  
  
    > [!NOTE]
    >  También puede agregar propiedades a dispinterfaces, las cuales, a menos que el proyecto tenga atributos, se anidarán en el nodo de biblioteca.  
  
2.  En el menú contextual, haga clic en **Agregar** y, después, en **Agregar propiedad**.  
  
3.  En el [Asistente para agregar métodos](../ide/names-add-property-wizard.md), especifique la información necesaria para crear la propiedad.  
  
4.  Especifique la configuración de lenguaje de definición de interfaz \(IDL\) de la propiedad en la página [Atributos IDL](../ide/idl-attributes-add-property-wizard.md) del asistente.  
  
5.  Haga clic en **Finalizar** para agregar la propiedad.  
  
 Los métodos **Get** y `Put` de la propiedad aparecerán como dos iconos en Vista de clases, bajo la interfaz donde se haya definido la propiedad.  Puede hacer doble clic en cualquiera de los iconos para ver la declaración de propiedades del archivo .idl.  
  
-   Con las interfaces ATL, las funciones **Get** y **Put** se agregan al archivo .cpp, mientras que las referencias a estas funciones se agregan al archivo .h.  
  
-   Con las interfaces dispinterfaces de MFC, si se selecciona **Variable miembro** como tipo de implementación, se agregarán un método y una variable a la clase que la implemente.  Si se selecciona **Métodos Get\/Set** como tipo de implementación, se agregarán dos métodos a la clase que los implementa.  
  
## Vea también  
 [Crear una interfaz COM](../ide/creating-a-com-interface-visual-cpp.md)   
 [Editar una interfaz COM](../ide/editing-a-com-interface.md)   
 [Modelo de objetos componentes](http://msdn.microsoft.com/library/windows/desktop/ms694363)   
 [Punteros de interfaz e interfaces](http://msdn.microsoft.com/library/windows/desktop/ms688484)