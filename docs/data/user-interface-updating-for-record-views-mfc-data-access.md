---
title: "Actualización de la interfaz de usuario para vistas de registros (acceso a datos MFC) | Documentos de Microsoft"
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
- user interfaces, updating
- menus, updating as context changes
- record views, user interface
ms.assetid: 2c7914b6-2dc3-40c3-b2f2-8371da2a4063
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 68b013f3b1211c42ffc7355df73f47f6520fac1d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="user-interface-updating-for-record-views--mfc-data-access"></a>Actualización de la interfaz de usuario para vistas de registros (acceso a datos MFC)
`CRecordView`proporciona controladores de actualización de la interfaz de usuario de valor predeterminado para los comandos de navegación. Estos controladores automatizan la habilitación y la deshabilitación de los objetos de la interfaz de usuario, como los elementos de menú y los botones de la barra de herramientas. El Asistente para aplicaciones proporciona menús estándar y, si elige la **barra de herramientas acoplable** opción, un conjunto de botones de barra de herramientas para los comandos. Si crea una clase de vista de registros con `CRecordView`, es posible que le interese agregar a la aplicación objetos de interfaz de usuario similares.  
  
### <a name="to-create-menu-resources-with-the-menu-editor"></a>Cómo crear recursos de menú con el editor de menús  
  
1.  Que hace referencia a la información sobre el uso de la [editor de menús](../windows/menu-editor.md), crear su propio menú con los mismos cuatro comandos.  
  
#### <a name="to-create-toolbar-buttons-with-the-graphics-editor"></a>Cómo crear botones de barra de herramientas con el editor de gráficos  
  
1.  Que hace referencia a la información sobre el uso de la [editor de la barra de herramientas](../windows/toolbar-editor.md), edite el recurso de barra de herramientas para agregar botones de barra de herramientas para los comandos de exploración de registros.  
  
## <a name="see-also"></a>Vea también  
 [Permitir la navegación en una vista de registros](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)   
 [Utilizar una vista de registros](../data/using-a-record-view-mfc-data-access.md)