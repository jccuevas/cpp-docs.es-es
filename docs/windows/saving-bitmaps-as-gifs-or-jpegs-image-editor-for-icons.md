---
title: Guardar mapas de bits, GIF o JPEG (Editar imágenes para iconos) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.editing
dev_langs:
- C++
helpviewer_keywords:
- .gif files, saving bitmaps as
- jpg files, saving bitmaps as
- jpeg files, saving bitmaps as
- .jpg files, saving bitmaps as
- Image editor [C++], converting image formats
- gif files, saving bitmaps as
- bitmaps [C++], converting formats
- .jpeg files, saving bitmaps as
- graphics [C++], converting formats
- images [C++], converting formats
ms.assetid: 115df69f-10fb-4e6f-906b-853c1e4a54af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: debb2b1e8435cc53ec82ab1f957710850d7b5de3
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010696"
---
# <a name="saving-bitmaps-as-gifs-or-jpegs-image-editor-for-icons"></a>Guardar un mapa de bits con formato GIF o JPEG (Editar imágenes para iconos)
Cuando se crea un mapa de bits, se crea la imagen en formato de mapa de bits (.bmp). Sin embargo, puede guardar la imagen como GIF o JPEG o en otros formatos de gráficos.  
  
> [!NOTE]
>  Este proceso no se aplica a los iconos y cursores.  
  
### <a name="to-create-and-save-a-bitmap-as-a-gif-or-jpeg"></a>Para crear y guardar un mapa de bits como un archivo .gif o .jpeg  
  
1.  Desde el **archivo** menú, elija **abierto**, a continuación, haga clic en **archivo**.  
  
2.  En el **cuadro de diálogo nuevo archivo**, haga clic en el **Visual C++** carpeta, a continuación, seleccione **el archivo de mapa de bits (.bmp)** en el **plantillas** cuadro y haga clic en  **Abra**.  
  
     El mapa de bits se abre en el **imagen** editor.  
  
3.  Realizar cambios en el nuevo mapa de bits, según sea necesario.  
  
4.  Con el mapa de bits sigue abierto en el **imagen** editor, haga clic en **guardar *filename*.bmp como** en el **archivo** menú.  
  
5.  En el **Guardar archivo como** diálogo cuadro, escriba el nombre que desea dar al archivo y la extensión que denota el formato de archivo que desee en el **nombre de archivo** cuadro. Por ejemplo, *miarchivo.gif*.  
  
     > [!NOTE]
     > Debe crear o abrir el mapa de bits fuera de su proyecto para poder guardarlo en otro formato de archivo. Si crea o abrirlo en el proyecto, el **Guardar como** comando dejará de estar disponible. Para obtener más información, consulte [ver recursos en un archivo de Script de recursos fuera de un proyecto (independiente)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).  
  
6.  Haga clic en **Guardar**.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="see-also"></a>Vea también  
 [Editar recursos gráficos](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Editor de imágenes para iconos](../windows/image-editor-for-icons.md)