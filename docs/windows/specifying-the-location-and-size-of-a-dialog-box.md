---
title: "Especificar la ubicación y el tamaño de un cuadro de diálogo | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- dialog boxes, size
- dialog boxes, positioning
ms.assetid: 2b7c495e-6595-4cfb-9664-80b2826d0851
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 03c4c6d6afb13a0e4ed8801838356ff0d1e851f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="specifying-the-location-and-size-of-a-dialog-box"></a>Especificar la ubicación y el tamaño de un cuadro de diálogo
La ubicación y el tamaño de un cuadro de diálogo, así como la ubicación y tamaño de los controles en él, se miden en unidades de cuadro de diálogo. Los valores de los controles individuales y el cuadro de diálogo aparecen en la esquina inferior derecha de la barra cuando se selecciona de estado de Visual Studio.  
  
 Hay tres propiedades que se pueden establecer en el [ventana propiedades](/visualstudio/ide/reference/properties-window) para especificar dónde aparecerá un cuadro de diálogo en la pantalla. La propiedad Center es un valor booleano; Si establece el valor en True, el cuadro de diálogo siempre aparecerá en el centro de la pantalla. Si se establece en False, a continuación, puede establecer las propiedades XPos y YPos para indicar explícitamente que en la pantalla que aparecerá el cuadro de diálogo. Las propiedades de posición son valores de desplazamiento desde la esquina superior izquierda del área de visualización, que se define como {X = 0, Y = 0}. La posición también se basa en el **Absolute Align** propiedad: si es True, las coordenadas son relativas a la pantalla; si es False, las coordenadas son relativas a la ventana del propietario del cuadro de diálogo.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Requisitos  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)   
 [Controles](../mfc/controls-mfc.md)

