---
title: Crear nuevas barras de herramientas | Documentos de Microsoft
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
- toolbars [C++], creating
- Toolbar editor, creating new toolbars
- Insert Resource
ms.assetid: 1b28264b-0718-4df8-9f65-979805d2efef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b61d1c530272ecaba2cbeb36c21e158bd5a6b401
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33888085"
---
# <a name="creating-new-toolbars"></a>Crear nuevas barras de herramientas
### <a name="to-create-a-new-toolbar"></a>Para crear una nueva barra de herramientas  
  
1.  En **recursos** ver, haga clic en el archivo .rc y, a continuación, elija **Agregar recurso** en el menú contextual. (Si tiene una barra de herramientas existente en el archivo .rc, puede hacer simplemente clic el **barra de herramientas** carpeta y seleccione **insertar Toolbar** en el menú contextual.)  
  
     **Nota** Si el proyecto no contiene un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  En el **Agregar recurso** cuadro de diálogo, seleccione **barra de herramientas** en el **tipo de recurso** lista, a continuación, haga clic en **nuevo**.  
  
     Si un signo más (+) aparece junto a la **barra de herramientas** tipo de recurso, significa que están disponibles plantillas de barra de herramientas. Haga clic en el signo más para expandir la lista de plantillas, seleccione una plantilla y haga clic en **nuevo**.  
  
     \- o -  
  
3.  [Convertir un mapa de bits existente en una barra de herramientas](../windows/converting-bitmaps-to-toolbars.md).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Requisitos  
  
 MFC o ATL  
  
## <a name="see-also"></a>Vea también  
 [Editor de barras de herramientas](../windows/toolbar-editor.md)

