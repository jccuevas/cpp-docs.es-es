---
title: "Elegir un fondo transparente u opaco (Editor de imágenes para iconos) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- opaque backgrounds
- background colors, images
- colors [C++], image
- Image editor [C++], transparent or opague backgrounds
- background images
- images [C++], transparency
- images [C++], opaque background
- transparent backgrounds
- transparency, background
- transparent backgrounds, images
ms.assetid: 61b743d9-c86b-405d-9a81-0806431b4363
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4e73ac7122b31ab6880d7d27387937113dee70f9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="choosing-a-transparent-or-opaque-background-image-editor-for-icons"></a>Elegir un fondo transparente u opaco (Editor de imágenes para iconos)
Al mover o copiar una selección de una imagen, los píxeles de la selección que coinciden con el color de fondo actual son, de forma predeterminada, transparente; no ocultan los píxeles de la ubicación de destino.  
  
 Puede alternar entre un fondo transparente (valor predeterminado) y un fondo opaco y volver. Cuando se usa una herramienta de selección, el **fondo transparente** y **fondo opaco** opciones que aparecen en el selector de opciones en la **Editor de imágenes** barra de herramientas (como se muestra a continuación).  
  
 ![Opciones &#45; en segundo plano opaco o transparente](../windows/media/vcimageeditoropaqtranspback.gif "vcImageEditorOpaqTranspBack")  
Opciones transparentes y opacos en la barra de herramientas del Editor de imágenes  
  
### <a name="to-switch-between-a-transparent-and-opaque-background"></a>Para alternar entre un fondo transparente y opaco  
  
1.  En el **Editor de imágenes** barra de herramientas, haga clic en el **opción** selector y, a continuación, haga clic en el icono correspondiente:  
  
    -   **Fondo opaco (O)**: imagen existente se oculta todas las partes de la selección.  
  
    -   **Fondo transparente (T)**: imagen existente se muestra en las partes de la selección que coinciden con el color de fondo actual.  
  
 \- o -  
  
-   En el **imagen** menú, active o desactive **dibujar opaco**.  
  
 Puede cambiar el color de fondo mientras una selección ya está en vigor para cambiar qué partes de la imagen son transparentes.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Requisitos  
  
 Ninguna  
  
## <a name="see-also"></a>Vea también  
 [Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Trabajar con colores](../windows/working-with-color-image-editor-for-icons.md)