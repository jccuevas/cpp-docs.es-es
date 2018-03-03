---
title: 'Controles ActiveX MFC: Propiedades | Documentos de Microsoft'
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
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
- properties [MFC]
ms.assetid: b678a53c-0d9e-476f-8aa0-23b80baaba46
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eea42401255f0aa99dd7a42b8e9b69e45dfe7b5b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-properties"></a>Controles ActiveX MFC: Propiedades
Un control ActiveX activa eventos para comunicarse con su contenedor de control. El contenedor, en respuesta, utiliza métodos y propiedades para comunicarse con el control. Métodos y propiedades son similares en uso y propósito, respectivamente, para las funciones miembro y variables de miembro de una clase de C++. Propiedades son miembros de datos del control ActiveX que están expuestos a cualquier contenedor. Propiedades proporcionan una interfaz para aplicaciones que contienen controles ActiveX, como los clientes de automatización y contenedores de controles ActiveX.  
  
 Las propiedades también se denominan atributos.  
  
 Para obtener más información sobre los métodos del control ActiveX, vea el artículo [controles ActiveX MFC: métodos](../mfc/mfc-activex-controls-methods.md).  
  
 Controles ActiveX pueden implementar las existencias y métodos y propiedades personalizados. Clase `COleControl` proporciona una implementación de propiedades estándar. (Para obtener una lista completa de propiedades estándar, vea el artículo [controles ActiveX de MFC: agregar propiedades estándar](../mfc/mfc-activex-controls-adding-stock-properties.md).) Propiedades personalizadas, definidas por el programador, agregan capacidades especializadas a un control ActiveX. Para obtener más información, consulte [controles ActiveX de MFC: agregar propiedades personalizadas](../mfc/mfc-activex-controls-adding-custom-properties.md).  
  
 Propiedades estándar y personalizadas, como los métodos, son compatibles con un mecanismo que consta de un mapa de envíos que controla propiedades y métodos y las funciones de miembro existente de la `COleControl` clase. Además, estas propiedades pueden tener parámetros que el programador utiliza para pasar información adicional al control.  
  
 Los artículos siguientes describen propiedades del control ActiveX con más detalle:  
  
-   [Controles ActiveX MFC: Agregar propiedades estándar](../mfc/mfc-activex-controls-adding-stock-properties.md)  
  
-   [Controles ActiveX MFC: Agregar propiedades personalizadas](../mfc/mfc-activex-controls-adding-custom-properties.md)  
  
-   [Controles ActiveX MFC: Implementación de propiedades avanzadas](../mfc/mfc-activex-controls-advanced-property-implementation.md)  
  
-   [Controles ActiveX MFC: Acceso a las propiedades de ambiente](../mfc/mfc-activex-controls-accessing-ambient-properties.md)  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

