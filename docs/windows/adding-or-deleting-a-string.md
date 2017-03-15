---
title: "Adding or Deleting a String | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.string"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "strings [C++], adding to string tables"
  - "string tables, deleting strings"
  - "strings [C++], deleting in string tables"
  - "string tables, adding strings"
ms.assetid: 077077b4-0f4b-4633-92d6-60b321164cab
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Adding or Deleting a String
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El Editor de cadenas permite insertar con rapidez entradas nuevas en la tabla de cadenas.  Cada cadena nueva se sitúa al final de la tabla y recibe el siguiente identificador disponible.  A partir de entonces es posible editar las propiedades ID, Value o Caption en la [ventana Propiedades](../Topic/Properties%20Window.md) según sea necesario.  
  
 El Editor de cadenas se asegurará de que no se esté empleando un identificador que ya esté en uso.  Si se selecciona un identificador ya utilizado, el Editor de cadenas lo notificará y asignará un identificador genérico único \(por ejemplo, IDS\_STRING58113\).  
  
### Para agregar una entrada a la tabla de cadenas  
  
1.  Abra la tabla de cadenas haciendo doble clic en su icono en la [Vista de recursos](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Haga clic con el botón secundario del mouse en la tabla de cadenas y elija **Nueva cadena** en el menú contextual.  
  
3.  En el **Editor de cadenas**, seleccione un **ID** en la lista desplegable ID o escríbalo directamente en el lugar correspondiente.  
  
4.  Si es necesario, cambie **Value**.  
  
5.  Escriba una entrada para **Caption**.  
  
    > [!NOTE]
    >  Las cadenas nulas no están permitidas en las tablas de cadenas de Windows.  La creación de una entrada como cadena nula en la tabla de cadenas activará el mensaje "Especifique una cadena para esta entrada de tabla".  
  
### Para eliminar una entrada en la tabla de cadenas  
  
1.  Seleccione la entrada que desee eliminar.  
  
2.  En el menú **Edición**, haga clic en **Eliminar**.  
  
 \-O bien\-  
  
-   Haga clic con el botón secundario del mouse en la cadena que desee eliminar y elija **Eliminar** en el menú contextual.  
  
 \-O bien\-  
  
-   Presione la tecla **SUPRIMIR**.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados \(los orientados a Common Language Runtime\), vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 **Requisitos**  
  
 Win32  
  
## Vea también  
 [String Editor](../mfc/string-editor.md)   
 [Cadenas](_win32_Strings)   
 [Acerca de cadenas](_win32_About_Strings_cpp)