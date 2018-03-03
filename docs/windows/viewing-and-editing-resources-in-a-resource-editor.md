---
title: Ver y editar recursos en un Editor de recursos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.resourceview
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], viewing
- rc files, viewing resources
- Resource View pane
- layouts, previewing resource
- code, viewing resources
- resource editors, viewing resources
- .rc files, viewing resources
- resources [Visual Studio], editing
ms.assetid: ba8bdc07-3f60-43c7-aa5c-d5dd11f0966e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 980264ab1857af214dcd24703980b8efa9a4d2dd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="viewing-and-editing-resources-in-a-resource-editor"></a>Ver y editar recursos en un editor de recursos
Cada tipo de recurso tiene un editor de recursos específico para ese tipo de recurso. Puede reorganizar, cambiar el tamaño, agregar controles y características o modificar otros aspectos de un recurso con el editor asociado. También puede editar un recurso en [formato de texto](../windows/how-to-open-a-resource-script-file-in-text-format.md) y [formato binario](../windows/opening-a-resource-for-binary-editing.md).  
  
 Algunos tipos de recursos son archivos individuales que se pueden importar y usar de varias maneras; Estos incluyen mapas de bits, iconos, cursores, barras de herramientas y archivos html. Estos recursos tienen nombres de archivo como [identificadores de recursos](../windows/symbols-resource-identifiers.md). Otros, como cuadros de diálogo, menús y las tablas de cadenas en los proyectos de Win32, sólo existen como parte de un archivo de recursos (.rc) de la secuencia de comandos o el archivo de recursos (.rct) de la plantilla.  
  
> [!NOTE]
>  Propiedades de un recurso [puede modificarse mediante la ventana propiedades](../windows/changing-the-properties-of-a-resource.md).  
  
## <a name="win32-resources"></a>Recursos de Win32  
 Puede tener acceso a recursos de Win32 en el [vista de recursos](../windows/resource-view-window.md) panel.  
  
#### <a name="to-view-a-win32-resource-in-a-resource-editor"></a>Para ver un recurso de Win32 en un editor de recursos  
  
1.  Seleccione **vista de recursos** desde el **vista** menú.  
  
2.  Si la ventana Vista de recursos no es la ventana de nivel superior, haga clic en el **vista de recursos** ficha para volver a ponerlo en la parte superior.  
  
3.  Vista de recursos, expanda la carpeta del proyecto que contiene los recursos que desea ver. Por ejemplo, si desea ver un recurso de cuadro de diálogo, expanda la carpeta del cuadro de diálogo.  
  
    > [!NOTE]
    >  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
4.  Haga doble clic en el recurso, por ejemplo, IDD_ABOUTBOX tienen.  
  
     El recurso se abrirá en el editor correspondiente. Por ejemplo, para los recursos de cuadro de diálogo, el recurso se abrirá en el editor de cuadro de diálogo.  
  
     También puede [ver recursos en un archivo .rc (secuencia de comandos de recursos) sin tener un proyecto abierto](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).  
  
#### <a name="to-delete-an-existing-win-32-resource"></a>Para eliminar un recurso de Win32 existente  
  
1.  En la vista de recursos, expanda el nodo para un tipo de recurso.  
  
2.  Haga doble clic en el recurso que desea eliminar y elija **eliminar** en el menú contextual.  
  
    > [!NOTE]
    >  Puede eliminar un recurso con el mismo comando del menú contextual cuando tenga el archivo .rc abrir en una ventana de documento fuera de un proyecto.  
  
## <a name="resources-in-managed-projects"></a>Recursos en proyectos administrados  
 Dado que los proyectos administrados no utilizan archivos de script de recursos, debe abrir los recursos desde **el Explorador de soluciones**. Se puede usar el [Editor de imágenes](../windows/image-editor-for-icons.md) y el [Editor binario](binary-editor.md) para trabajar con archivos de recursos en proyectos administrados. Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
#### <a name="to-view-a-managed-resource-in-a-resource-editor"></a>Para ver un recurso administrado en un editor de recursos  
  
1.  En el Explorador de soluciones, haga doble clic en el recurso, por ejemplo, Bitmap1.bmp.  
  
     El recurso se abrirá en el editor correspondiente.  
  
#### <a name="to-delete-an-existing-managed-resource"></a>Para eliminar un recurso administrado existente  
  
1.  En el Explorador de soluciones, haga clic en el recurso que desea eliminar y elija **eliminar** en el menú contextual.  
  
### <a name="requirements"></a>Requisitos  
 Ninguna  
  
## <a name="see-also"></a>Vea también  
 [Editores de recursos](../windows/resource-editors.md)

