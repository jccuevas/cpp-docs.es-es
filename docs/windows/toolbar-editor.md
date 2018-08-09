---
title: Editor de la barra de herramientas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.toolbar.F1
dev_langs:
- C++
helpviewer_keywords:
- resource editors, Toolbar editor
- editors, toolbars
- toolbars [C++], editing
- Toolbar editor
ms.assetid: aa9f0adf-60f6-4f79-ab05-bc330f15ec43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 505b97d1b3883568fc85795898f16f9821d8b930
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011733"
---
# <a name="toolbar-editor"></a>Editor de barras de herramientas
El **barra de herramientas** editor le permite crear recursos de la barra de herramientas y convertir mapas de bits en recursos de la barra de herramientas. El **barra de herramientas** editor usa una presentación gráfica para mostrar una barra de herramientas y botones que se parecen mucho al aspecto que tendrán en una aplicación acabada.  
  
 Con el **barra de herramientas** editor, puede:  
  
-   [Crear nuevos botones y barras de herramientas](../windows/creating-new-toolbars.md)  
  
-   [Convertir mapas de bits a recursos de la barra de herramientas](../windows/converting-bitmaps-to-toolbars.md)  
  
-   [Crear, mover y editar botones de la barra de herramientas](../windows/creating-moving-and-editing-toolbar-buttons.md)  
  
-   [Crear información sobre herramientas](../windows/creating-a-tool-tip-for-a-toolbar-button.md)  
  
 El **barra de herramientas** ventana del editor muestra dos vistas de una imagen del botón, igual que la ventana del editor de imágenes. Una barra de división separa los dos paneles. Se puede arrastrar dicha barra a uno u otro lado para cambiar el tamaño relativo de los paneles. El panel activo muestra un borde de selección. Por encima de las dos vistas de la imagen se encuentra la barra de herramientas del asunto.  
  
 ![Editor de la barra de herramientas](../mfc/media/vctoolbareditor.gif "vcToolbarEditor")  
Editor de barras de herramientas  
  
 El **barra de herramientas** editor es similar a la **imagen** editor en la funcionalidad. Los elementos de menú, las herramientas gráficas y cuadrícula de mapa de bits son los mismos que los de la **imagen** editor. Hay un comando de menú en el **imagen** menú para que pueda cambiar entre el **barra de herramientas** editor y la **imagen** editor. Para obtener más información sobre el uso de la **gráficos** barra de herramientas, **colores** paleta, o **imagen** menú, vea [Editor de imágenes](../windows/image-editor-for-icons.md).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Requisitos  
 MFC o ATL  
  
## <a name="see-also"></a>Vea también  
 [Editores de recursos](../windows/resource-editors.md)   
 [Menús y otros recursos](http://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)