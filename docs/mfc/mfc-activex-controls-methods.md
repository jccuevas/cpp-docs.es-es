---
title: "Controles ActiveX MFC: M&#233;todos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles ActiveX en MFC, métodos"
ms.assetid: e20271de-6ffa-4ba0-848b-bafe6c9e510c
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Controles ActiveX MFC: M&#233;todos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un control ActiveX desencadena eventos para comunicarse entre sí mismo y su contenedor del control.  Un contenedor también puede comunicarse con un control mediante métodos y propiedades.  Los métodos también se denominan funciones.  
  
 Los métodos y las propiedades proporcionan una interfaz exportada para uso de otras aplicaciones, como clientes de automatización y contenedores de controles ActiveX.  Para obtener más información sobre propiedades de controles ActiveX, vea el artículo [Controles ActiveX de MFC: Propiedades](../mfc/mfc-activex-controls-properties.md).  
  
 Los métodos se utilizan similar y propósito a las funciones miembro de clases de c\+\+.  Hay dos tipos de métodos que el control puede implementar: acción y personalizado.  Similar a eventos comunes, los métodos comunes son los métodos para los que [COleControl](../mfc/reference/colecontrol-class.md) proporciona una implementación.  Para obtener más información sobre los métodos comunes, vea el artículo [Controles ActiveX de MFC: Agregar métodos comunes](../mfc/mfc-activex-controls-adding-stock-methods.md).  Los métodos personalizados, definidos por el desarrollador, permiten la personalización adicional del control.  Para obtener más información, vea el artículo [Controles ActiveX de MFC: Métodos de personalizadas de suma](../mfc/mfc-activex-controls-adding-custom-methods.md).  
  
 La biblioteca Microsoft Foundation Class \(MFC\) implementa un mecanismo que permite que el control admita los métodos comunes y personalizados.  La primera parte es clase `COleControl`.  Derivado de `CWnd`, métodos de acción de compatibilidad con las funciones miembro de `COleControl` que son comunes a todos los controles ActiveX.  La segunda parte de este mecanismo es el mapa de envío.  Un mapa de distribución es similar a un mapa de mensajes; sin embargo, en lugar de asignar una función a un identificador de mensaje de Windows, un miembro virtual de los mapas de asignación send funciona a identificadores de IDispatch.  
  
 Para que un control admite varios métodos correctamente, la clase debe declarar un mapa de envío.  Esto se realiza mediante la siguiente línea de código encuentra en encabezado de clase control \(. H\) archivo:  
  
 [!code-cpp[NVC_MFC_AxUI#13](../mfc/codesnippet/CPP/mfc-activex-controls-methods_1.h)]  
  
 La finalidad principal de mapa de distribución es establecer la relación entre los nombres de método utilizados por un llamador externo \(como el contenedor\) y las funciones miembro de clases de controles que implementan los métodos.  Una vez declarado el mapa send, debe definirse en el archivo de implementación del control \(.CPP\).  Las siguientes líneas de código definen el envío asignado:  
  
 [!code-cpp[NVC_MFC_AxUI#14](../mfc/codesnippet/CPP/mfc-activex-controls-methods_2.cpp)]  
[!code-cpp[NVC_MFC_AxUI#15](../mfc/codesnippet/CPP/mfc-activex-controls-methods_3.cpp)]  
  
 Si utilizó [Asistente para controles ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md) para crear el proyecto, estas se agregaron líneas automáticamente.  Si no se utiliza el asistente para controles ActiveX MFC, debe agregar estas líneas manualmente.  
  
 Los artículos siguientes explican métodos con detalle:  
  
-   [Controles ActiveX de MFC: Agregar métodos comunes](../mfc/mfc-activex-controls-adding-stock-methods.md)  
  
-   [Controles ActiveX de MFC: Métodos de personalizadas de suma](../mfc/mfc-activex-controls-adding-custom-methods.md)  
  
-   [Controles ActiveX de MFC: Devuelve los códigos de error De un método](../mfc/mfc-activex-controls-returning-error-codes-from-a-method.md)  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)