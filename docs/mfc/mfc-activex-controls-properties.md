---
title: "Controles ActiveX MFC: Propiedades | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles ActiveX en MFC, propiedades"
  - "propiedades [MFC]"
  - "propiedades [MFC], controles ActiveX"
ms.assetid: b678a53c-0d9e-476f-8aa0-23b80baaba46
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Controles ActiveX MFC: Propiedades
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un control ActiveX desencadena eventos para comunicarse con el contenedor del control.  El contenedor, en cambio, utiliza métodos y propiedades para comunicarse con el control.  Los métodos y propiedades están en uso similar y propósito, respectivamente, a las funciones miembro y variables miembro de la clase en cuestión.  Las propiedades son miembros de datos del control ActiveX que se exponen a cualquier contenedor.  Las propiedades proporcionan una interfaz para las aplicaciones que contienen controles ActiveX, como clientes de automatización y contenedores de controles ActiveX.  
  
 Las propiedades también se denominan los atributos.  
  
 Para obtener más información sobre los métodos de control ActiveX, vea el artículo [Controles ActiveX de MFC: Métodos](../mfc/mfc-activex-controls-methods.md).  
  
 Los controles ActiveX pueden implementar ambos métodos y propiedades estándar y personalizados.  La clase `COleControl` proporciona una implementación de las propiedades comunes. \(Para obtener una lista completa de propiedades comunes, vea el artículo [Controles ActiveX de MFC: Agregar propiedades estándar](../mfc/mfc-activex-controls-adding-stock-properties.md).\) Propiedades personalizadas, definidas por el desarrollador, agregan capacidades especializadas un control ActiveX.  Para obtener más información, vea [Controles ActiveX de MFC: Agregar propiedades personalizadas](../mfc/mfc-activex-controls-adding-custom-properties.md).  
  
 Las propiedades personalizadas y la acción, como métodos, admite un mecanismo que consta de un envío asignado que controle propiedades y métodos y funciones existentes del miembro de la clase de `COleControl` .  Además, estas propiedades pueden tener parámetros que el desarrollador utilice para pasar información adicional al control.  
  
 Los casos siguientes describen propiedades de controles ActiveX con más detalle:  
  
-   [Controles ActiveX de MFC: Agregar propiedades estándar](../mfc/mfc-activex-controls-adding-stock-properties.md)  
  
-   [Controles ActiveX de MFC: Agregar propiedades personalizadas](../mfc/mfc-activex-controls-adding-custom-properties.md)  
  
-   [Controles ActiveX de MFC: Implementación avanzada de propiedad](../mfc/mfc-activex-controls-advanced-property-implementation.md)  
  
-   [Controles ActiveX de MFC: Propiedades de ambiente de acceso](../mfc/mfc-activex-controls-accessing-ambient-properties.md)  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)