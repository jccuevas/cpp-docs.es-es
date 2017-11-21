---
title: 'Contenedores de controles ActiveX: Ver y modificar propiedades de Control | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- properties [MFC], viewing and modifying
- ActiveX control containers [MFC], viewing and modifying properties
- resource editors, viewing and modifying ActiveX controls
- ActiveX controls [MFC], properties
- controls [MFC], properties
ms.assetid: 14ce5152-742b-4e0d-a9ab-c7b456e32918
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 90e866d1a3be4600b3b98e542caff6ed793f4226
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="activex-control-containers-viewing-and-modifying-control-properties"></a>Contenedores de controles ActiveX: Ver y modificar propiedades de los controles
Al insertar un control ActiveX en un proyecto, es útil ver y cambiar las propiedades admitidas por el control ActiveX. Este artículo describe cómo usar el editor de recursos de Visual C++ para hacerlo.  
  
 Si la aplicación de contenedor del control ActiveX utiliza controles incrustados, puede ver y modificar las propiedades del control en el editor de recursos. También puede usar el editor de recursos para establecer valores de propiedad en tiempo de diseño. A continuación, el editor de recursos guarda automáticamente estos valores en el archivo de recursos del proyecto. Cualquier instancia del control tendrán sus propiedades inicializadas con estos valores.  
  
 Este procedimiento se supone que ha insertado un control en el proyecto. Para obtener información, consulte [contenedores de controles ActiveX: insertar un Control en una aplicación contenedora](../mfc/inserting-a-control-into-a-control-container-application.md).  
  
 Es el primer paso para ver las propiedades del control agregar una instancia del control a la plantilla de cuadro de diálogo del proyecto.  
  
### <a name="to-view-the-properties-of-a-control"></a>Para ver las propiedades de un control  
  
1.  En la vista de recursos, abra el **diálogo** carpeta.  
  
2.  Abra la plantilla de cuadro de diálogo principal.  
  
3.  Insertar un control ActiveX mediante la **insertar ActiveX Control** cuadro de diálogo. Para obtener más información, consulte [ver y agregar controles ActiveX a un cuadro de diálogo](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).  
  
4.  Seleccione el control ActiveX en el cuadro de diálogo.  
  
5.  En la ventana Propiedades, haga clic en el **propiedades** botón.  
  
 Use la **propiedades** cuadro de diálogo para modificar y probar las nuevas propiedades inmediatamente.  
  
## <a name="see-also"></a>Vea también  
 [Contenedores de controles ActiveX](../mfc/activex-control-containers.md)

