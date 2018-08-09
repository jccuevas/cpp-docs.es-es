---
title: Elegir un fondo transparente u opaco (Editor de imágenes para iconos) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7c8a809e7cd7ed7a461149707cc9e0b2a4a62158
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649525"
---
# <a name="choosing-a-transparent-or-opaque-background-image-editor-for-icons"></a>Elegir un fondo transparente u opaco (Editor de imágenes para iconos)
Al mover o copiar una selección de una imagen, son los píxeles de la selección que coinciden con el color de fondo actual, de forma predeterminada, transparente; no ocultan los píxeles en la ubicación de destino.  
  
 Puede cambiar de un fondo transparente (valor predeterminado) a un fondo opaco y viceversa. Cuando se usa una herramienta de selección, el **fondo transparente** y **fondo opaco** opciones aparecen en la **opción** selector en la **delEditordeimágenes** barra de herramientas (como se muestra a continuación).  
  
 ![Opciones de fondo &#45; opaca o transparente](../windows/media/vcimageeditoropaqtranspback.gif "vcImageEditorOpaqTranspBack")  
**Opciones transparentes y opacas** en el **barra de herramientas del Editor de imágenes**  
  
### <a name="to-switch-between-a-transparent-and-opaque-background"></a>Para cambiar entre un fondo transparente y opaco  
  
1.  En el **Editor de imágenes** barra de herramientas, haga clic en el **opción** selector y, a continuación, haga clic en el fondo correspondiente:  
  
    -   `Opaque Background (O)`: Imagen existente está oculto por todas las partes de la selección.  
  
    -   `Transparent Background (T)`: Imagen existente se muestra en las partes de la selección que coinciden con el color de fondo actual.  
  
 \- o -  
  
-   En el **imagen** menú, active o desactive **dibujar figuras opacas**.  
  
 Puede cambiar el color de fondo mientras una selección ya está en vigor para cambiar qué partes de la imagen son transparentes.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Requisitos  
 Ninguna  
  
## <a name="see-also"></a>Vea también  
 [Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Trabajar con colores](../windows/working-with-color-image-editor-for-icons.md)