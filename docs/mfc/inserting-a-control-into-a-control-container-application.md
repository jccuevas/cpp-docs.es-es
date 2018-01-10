---
title: "Contenedores de controles ActiveX: Insertar un Control en una aplicación de contenedor de Control | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ActiveX control containers [MFC], inserting controls
- ActiveX controls [MFC], adding to projects
ms.assetid: bbb617ff-872f-43d8-b4d6-c49adb16b148
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a1eaaf0426726f252fc4990f06faa73b0598cfbb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="activex-control-containers-inserting-a-control-into-a-control-container-application"></a>Contenedores de controles ActiveX: Insertar un control en una aplicación de contenedor de controles
Antes de que puede tener acceso a un control ActiveX desde una aplicación de contenedor de controles ActiveX, debe agregar el control ActiveX a la aplicación de contenedor mediante el [insertar ActiveX Control](../windows/insert-activex-control-dialog-box.md) cuadro de diálogo.  
  
 Para agregar un control ActiveX para el proyecto de contenedor de controles ActiveX, vea [ver y agregar controles ActiveX a un cuadro de diálogo](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).  
  
 Una vez que agregue el control, debe agregar una variable miembro (del tipo de control ActiveX) a la clase de cuadro de diálogo. Para obtener más información acerca de este procedimiento, consulte [agregar una Variable miembro](../ide/adding-a-member-variable-visual-cpp.md).  
  
 Cuando haya agregado la variable miembro una clase, que se conoce como una clase contenedora, se genera automáticamente y se agrega al proyecto. Esta clase se utiliza como una interfaz entre el contenedor del control y el control incrustado.  
  
## <a name="see-also"></a>Vea también  
 [Contenedores de controles ActiveX](../mfc/activex-control-containers.md)

