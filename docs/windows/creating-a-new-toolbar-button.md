---
title: Crear un nuevo botón de barra de herramientas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.toolbar
dev_langs:
- C++
helpviewer_keywords:
- Toolbar editor, creating buttons
- toolbar buttons (in Toolbar editor), button image
- toolbar buttons (in Toolbar editor), creating
- toolbar buttons (in Toolbar editor)
ms.assetid: 46c120fe-4f2a-4887-a08f-bd1fea04b3f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d883fbb34fe45be2ad84860ea7564350346749f2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="creating-a-new-toolbar-button"></a>Crear un nuevo botón de la barra de herramientas
### <a name="to-create-a-new-toolbar-button"></a>Para crear un nuevo botón de barra de herramientas  
  
1.  En [vista de recursos](../windows/resource-view-window.md) expanda la carpeta del recurso (por ejemplo, Project1.rc).  
  
    > [!NOTE]
    >  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Expanda el **barra de herramientas** carpeta y seleccione una barra de herramientas para editar.  
  
3.  Asignar un identificador para el botón en blanco en el extremo derecho de la barra de herramientas. Puede hacerlo mediante la edición de la **identificador** propiedad en el [ventana propiedades](/visualstudio/ide/reference/properties-window). Por ejemplo, puede que desee proporcionar el mismo identificador como una opción de menú a un botón de barra de herramientas. En este caso, utilice el cuadro de lista desplegable para seleccionar la **ID** de la opción de menú.  
  
     -o bien-  
  
     Seleccione el botón en blanco en el extremo derecho de la barra de herramientas (en el panel de vista de la barra de herramientas) y empiece a dibujar. Se asigna un identificador de comando del botón predeterminado (ID\<n >).  
  
 También puede copiar y pegar una imagen en una barra de herramientas como un botón de nuevo.  
  
#### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>Para agregar una imagen a una barra de herramientas como un botón  
  
1.  En [vista de recursos](../windows/resource-view-window.md), abra la barra de herramientas haciendo doble clic en él.  
  
2.  A continuación, abra la imagen que le gustaría agregar a la barra de herramientas.  
  
    > [!NOTE]
    >  Si la imagen se abre en Visual Studio, se abrirá en el editor de imágenes. También puede abrir la imagen en otros programas de gráficos.  
  
3.  Desde el **editar** menú, elija **copia**.  
  
4.  Cambie a la barra de herramientas haciendo clic en la pestaña en la parte superior de la ventana de código fuente.  
  
5.  Desde el **editar** menú, elija **pegar**.  
  
     La imagen aparecerá en la barra de herramientas como un botón de nuevo.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
### <a name="requirements"></a>Requisitos  
 MFC o ATL  
  
## <a name="see-also"></a>Vea también  
 [Propiedades de botón de barra de herramientas](../windows/toolbar-button-properties.md)   
 [Crear, mover y editar botones de barra de herramientas](../windows/creating-moving-and-editing-toolbar-buttons.md)   
 [Editor de barras de herramientas](../windows/toolbar-editor.md)

