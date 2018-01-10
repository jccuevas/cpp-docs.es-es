---
title: "Propiedades de botón de barra de herramientas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- size, toolbar buttons
- toolbar buttons (in Toolbar editor), setting properties
- Toolbar editor, toolbar button properties
- status bars, active toolbar button text
- command IDs, toolbar buttons
- width, toolbar buttons
ms.assetid: b2705814-7c5d-4f24-8f77-07559b0cdda2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5e179cd400b0b8bcc621a7c69a4814eab098fbaa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="toolbar-button-properties"></a>Propiedades de los botones de barra de herramientas
Las propiedades de un botón de barra de herramientas son:  
  
|Property|Descripción|  
|--------------|-----------------|  
|**ID**|Define el identificador para el botón. En la lista desplegable proporciona comunes **identificador** nombres.|  
|**Ancho**|Establece el ancho del botón. se recomienda 16 píxeles.|  
|**Alto**|Establece el alto del botón. Tenga en cuenta que el alto de un botón cambia el alto de todos los botones de la barra de herramientas. se recomienda 15 píxeles.|  
|**Preguntar**|Define el mensaje que se muestra en la barra de estado. Agrega \n y un nombre, agrega una información sobre herramientas para ese botón de barra de herramientas. Para obtener más información, consulte [crear una información sobre herramientas](../windows/creating-a-tool-tip-for-a-toolbar-button.md).|  
  
 **Ancho** y **alto** se aplican a todos los botones. Un mapa de bits que se utiliza para crear una barra de herramientas tiene un ancho máximo de 2048. Por lo tanto, si se establece el ancho de botón en 512, solo puede tener cuatro botones y si se establece el ancho en 513, sólo puede tener tres botones.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Requisitos  
 MFC o ATL  
  
## <a name="see-also"></a>Vea también  
 [Cambiar las propiedades de un botón de barra de herramientas](../windows/changing-the-properties-of-a-toolbar-button.md)   
 [Editor de barras de herramientas](../windows/toolbar-editor.md)

