---
title: Ver y editar recursos en un Editor de recursos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5fca755c46d3fc5628adc2c724b9307a346d1fe7
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014008"
---
# <a name="viewing-and-editing-resources-in-a-resource-editor"></a>Ver y editar recursos en un editor de recursos
Cada tipo de recurso tiene un **recursos** editor de ese tipo de recurso específico. Puede reorganizar, cambiar el tamaño, agregar controles y características o modificar otros aspectos de un recurso con el editor asociado. También puede editar un recurso en [formato de texto](../windows/how-to-open-a-resource-script-file-in-text-format.md) y [formato binario](../windows/opening-a-resource-for-binary-editing.md).  
  
 Algunos tipos de recursos son archivos individuales que se pueden importar y usar de diversas maneras; Estos incluyen los mapas de bits, iconos, cursores, barras de herramientas y los archivos html. Estos recursos tienen nombres de archivo, así como [identificadores de recursos](../windows/symbols-resource-identifiers.md). Otros, como cuadros de diálogo, menús y las tablas de cadenas en los proyectos de Win32, sólo existen como parte de un archivo de recursos (.rc) de la secuencia de comandos o el archivo de recursos (.rct) de la plantilla.  
  
> [!NOTE]
>  Propiedades de un recurso [puede modificarse mediante la ventana propiedades](../windows/changing-the-properties-of-a-resource.md).  
  
## <a name="win32-resources"></a>Recursos de Win32  
 Puede obtener acceso a los recursos de Win32 en el [vista de recursos](../windows/resource-view-window.md) panel.  
  
### <a name="to-view-a-win32-resource-in-a-resource-editor"></a>Para ver un recurso de Win32 en un editor de recursos  
  
1.  Seleccione **vista de recursos** desde el **vista** menú.  
  
2.  Si el **vista de recursos** ventana no es la ventana de nivel superior, haga clic en el **vista de recursos** tab para colocarlo en la parte superior.  
  
3.  Desde **vista de recursos**, expanda la carpeta del proyecto que contiene recursos que desea ver. Por ejemplo, si desea ver un recurso de cuadro de diálogo, expanda el **diálogo** carpeta.  
  
    > [!NOTE]
    >  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
4.  Haga doble clic en el recurso, por ejemplo, **IDD_ABOUTBOX**.  
  
     El recurso se abrirá en el editor correspondiente. Por ejemplo, para los recursos de cuadro de diálogo, el recurso se abrirá dentro de la **diálogo** editor.  
  
     También puede [ver recursos en un archivo .rc (script de recursos) sin tener un proyecto abierto](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).  
  
### <a name="to-delete-an-existing-win-32-resource"></a>Para eliminar un recurso existente de Win 32  
  
1.  En **vista de recursos**, expanda el nodo de un tipo de recurso.  
  
2.  Haga doble clic en el recurso que desea eliminar y elija **eliminar** en el menú contextual.  
  
    > [!NOTE]
    >  Puede eliminar un recurso mediante el comando del menú contextual cuando tenga el archivo .rc abierto en una ventana de documento fuera de un proyecto.  
  
## <a name="resources-in-managed-projects"></a>Recursos en proyectos administrados  
 Dado que los proyectos administrados no usan archivos de script de recursos, debe abrir los recursos desde **el Explorador de soluciones**. Se puede usar el [Editor de imágenes](../windows/image-editor-for-icons.md) y el [Editor binario](binary-editor.md) para trabajar con archivos de recursos en proyectos administrados. Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
### <a name="to-view-a-managed-resource-in-a-resource-editor"></a>Para ver un recurso administrado en un editor de recursos  
  
1.  En **el Explorador de soluciones**, haga doble clic en el recurso, por ejemplo, **Bitmap1.bmp**.  
  
     El recurso se abrirá en el editor correspondiente.  
  
### <a name="to-delete-an-existing-managed-resource"></a>Para eliminar un recurso administrado existente  
  
1.  En **el Explorador de soluciones**, haga clic en el recurso que desea eliminar y elija **eliminar** en el menú contextual.  
  
## <a name="requirements"></a>Requisitos  
 Ninguna  
  
## <a name="see-also"></a>Vea también  
 [Editores de recursos](../windows/resource-editors.md)