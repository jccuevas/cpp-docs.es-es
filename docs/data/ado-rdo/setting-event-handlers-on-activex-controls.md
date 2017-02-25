---
title: "Establecer controladores de eventos en controles ActiveX | Microsoft Docs"
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
  - "controles ActiveX [C++], eventos"
  - "eventos [C++], controles ActiveX"
ms.assetid: c076386f-c78b-4dc9-9201-a544252d5337
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Establecer controladores de eventos en controles ActiveX
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se puede programar los controles ActiveX para que respondan a eventos.  Puede utilizar **ControlEvents** en las propiedades para ver los eventos disponibles en un control y crear controladores de eventos.  Se suele utilizar el control de eventos para detectar cambios en la consulta del origen de datos.  Dichos cambios incluyen:  
  
-   Implementar una búsqueda.  Cuando un control \(como un cuadro DBCombo\) cambia de valor, se detecta el evento de cambio para actualizar una consulta del control de datos.  
  
-   Implementar una relación principal\-detalle.  Se agregan dos controles de datos a un cuadro de diálogo, uno para la parte principal y un segundo para la parte de detalle.  Siempre que cambie el primer origen de datos, se actualizará la consulta del segundo origen de datos mediante un controlador de eventos.  
  
-   Interceptar errores.  La mayoría de los controles tienen un evento de error que se puede utilizar para programar un controlador de errores \(vea [Interceptación de errores](../../data/ado-rdo/error-trapping.md)\).  
  
 Para obtener más información, vea [Asignar mensajes a funciones](../../mfc/reference/mapping-messages-to-functions.md).  
  
## Vea también  
 [Utilizar controles ActiveX](../../data/ado-rdo/using-activex-controls.md)