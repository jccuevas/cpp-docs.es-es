---
title: "Crear una información sobre herramientas para un botón de barra de herramientas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- tool tips [C++], adding to toolbar buttons
- "\nin tool tip"
- toolbar buttons [C++], tool tips
- buttons [C++], tool tips
- Toolbar editor, creating tool tips
ms.assetid: 0af65342-fd78-4e78-8d0d-dc68f7fc462e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5b5bb25a14d68c01c25d9242df89c1183511ca83
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-tool-tip-for-a-toolbar-button"></a>Crear información sobre herramientas para un botón de la barra de herramientas
### <a name="to-create-a-tool-tip"></a>Para crear una información sobre herramientas  
  
1.  Seleccione el botón de barra de herramientas.  
  
2.  En el [ventana propiedades](/visualstudio/ide/reference/properties-window), en la **Prompt** campo de propiedades, agregue una descripción del botón de la barra de estado; después del mensaje, agregue \n y el nombre de la sugerencia de herramienta.  
  
 Un ejemplo común de una información sobre herramientas es el botón Imprimir de WordPad:  
  
 1. Abrir WordPad.  
  
 2. Mantenga el puntero del mouse sobre la **impresión** botón de barra de herramientas.  
  
 3. Tenga en cuenta que la palabra 'Imprimir' ahora está flotando en el puntero del mouse.  
  
 4. Buscar en la barra de estado (en la parte inferior de la ventana de WordPad): tenga en cuenta que ahora muestra el texto "Imprime el documento activo".  
  
 'Imprimir' en el paso 3 es el "nombre de información sobre la herramienta" y el 'imprime el documento activo ' del paso 4 es la "Descripción del botón de la barra de estado".  
  
 Si desea que este efecto mediante la **barra de herramientas** editor, establezca el **Prompt** propiedad **imprime el documento activo\nImprimir**.  
  
> [!NOTE]
>  Puede editar el texto del mensaje utilizando el [ventana propiedades](/visualstudio/ide/reference/properties-window).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Requisitos  
  
 MFC o ATL  
  
## <a name="see-also"></a>Vea también  
 [Crear, mover y editar botones de barra de herramientas](../windows/creating-moving-and-editing-toolbar-buttons.md)   
 [Editor de barras de herramientas](../windows/toolbar-editor.md)

