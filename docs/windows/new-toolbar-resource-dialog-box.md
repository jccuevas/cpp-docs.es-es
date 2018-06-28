---
title: Nuevo cuadro de diálogo de recurso de barra de herramientas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.newtoolbarresource
dev_langs:
- C++
helpviewer_keywords:
- New Toolbar Resource dialog box
ms.assetid: 52dd01ad-e748-4ab2-b3eb-59f5df990ca6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6662fcfab3c9bb1d805e39147bd2838e6bbce5b2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877545"
---
# <a name="new-toolbar-resource-dialog-box"></a>Nuevo recurso de la barra de herramientas (cuadro de diálogo)
El cuadro de diálogo nuevo recurso de barra de herramientas permite especificar el ancho y alto de los botones que se va a agregar a un recurso de barra de herramientas. El valor predeterminado es 16 x 15 píxeles.  
  
 Un mapa de bits que se utiliza para crear una barra de herramientas tiene un ancho máximo de 2048. Por tanto, si establece la **botón ancho** en 512, solo puede tener cuatro botones. Si se establece el ancho en 513, sólo puede tener tres botones.  
  
 **Ancho del botón**  
 Proporciona un espacio para que escriba el ancho de los botones de barra de herramientas que se va a convertir en un recurso de mapa de bits en un recurso de barra de herramientas. Las imágenes se recortan al ancho y alto que se especificó, y los colores se ajustan para usar colores de la barra de herramientas estándar (16 colores).  
  
 **Alto de botón**  
 Proporciona un espacio especificar el alto de los botones de barra de herramientas que se va a convertir en un recurso de mapa de bits en un recurso de barra de herramientas. Las imágenes se recortan al ancho y alto que se especificó, y los colores se ajustan para usar colores de la barra de herramientas estándar (16 colores).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Requisitos  
 MFC o ATL  
  
## <a name="see-also"></a>Vea también  
 [Propiedades de botón de barra de herramientas](../windows/toolbar-button-properties.md)   
 [Convertir mapas de bits en barras de herramientas](../windows/converting-bitmaps-to-toolbars.md)   
 [Editor de barras de herramientas](../windows/toolbar-editor.md)

