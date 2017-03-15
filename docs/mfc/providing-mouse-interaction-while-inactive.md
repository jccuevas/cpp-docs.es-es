---
title: "Proporcionar interacci&#243;n con el mouse mientras est&#225; inactivo | Microsoft Docs"
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
  - "controles ActiveX en MFC, interacción del mouse"
ms.assetid: b09106bf-44c7-4b9b-a6d9-0d624f16f5b3
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Proporcionar interacci&#243;n con el mouse mientras est&#225; inactivo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si el control inmediatamente no se activa, puede aún desee procesar `WM_SETCURSOR` y los mensajes de `WM_MOUSEMOVE` , aunque el control no tiene ninguna ventana propios.  Esto se puede lograr que permite la implementación de `COleControl` de la interfaz de `IPointerInactive` , que está deshabilitada de forma predeterminada. \(Vea *ActiveX SDK* para obtener una descripción de esta interfaz.\) Para habilitarla, incluya la marca de `pointerInactive` en el conjunto de indicadores devueltos por [COleControl::GetControlFlags](../Topic/COleControl::GetControlFlags.md):  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/CPP/providing-mouse-interaction-while-inactive_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#10](../mfc/codesnippet/CPP/providing-mouse-interaction-while-inactive_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/CPP/providing-mouse-interaction-while-inactive_3.cpp)]  
  
 El código para incluir este marcador se genera automáticamente si selecciona la opción de **Mouse Pointer Notifications When Inactive** en la página de [Configuración del control](../mfc/reference/control-settings-mfc-activex-control-wizard.md) al crear el control con **Asistente para controles ActiveX MFC**.  
  
 Cuando se habilita la interfaz de `IPointerInactive` , el contenedor delega `WM_SETCURSOR` y los mensajes de `WM_MOUSEMOVE` al.  la implementación de`COleControl` de `IPointerInactive` envía los mensajes a través de mensajes del control asignado después de ajustar las coordenadas del mouse correctamente.  Puede procesar los mensajes como mensajes normales de la ventana agregando las entradas correspondientes al mapa de mensajes.  En los controladores para estos mensajes, evite utilizar la variable miembro de `m_hWnd` \(o cualquier función miembro que lo utilice\) sin comprobar primero que su valor no es **nulo**.  
  
 Puede que también desee un control inactivo para ser el destino de una operación de arrastrar y colocar de OLE.  Esto requiere generar el control en el momento en que el usuario arrastra un objeto encima, para poder registrar la ventana de control como destino.  Para hacer la activación para producir durante una operación de arrastrar, reemplace [COleControl::GetActivationPolicy](../Topic/COleControl::GetActivationPolicy.md), y devuelve el mensaje de **POINTERINACTIVE\_ACTIVATEONDRAG** :  
  
 [!code-cpp[NVC_MFC_AxOpt#11](../mfc/codesnippet/CPP/providing-mouse-interaction-while-inactive_4.cpp)]  
  
 Habilitar la interfaz de `IPointerInactive` significa normalmente que desea que el control sea capaz de mensajes del mouse de procesamiento siempre.  Para obtener este comportamiento en un contenedor que no admite la interfaz de `IPointerInactive` , debe tener el control se genera cuando está visible, que significa que el control debe incluir la marca de **OLEMISC\_ACTIVATEWHENVISIBLE** entre los marcadores diferentes.  Sin embargo, para evitar que este marcador surta efecto en un contenedor que admite `IPointerInactive`, también puede especificar la marca de **OLEMISC\_IGNOREACTIVATEWHENVISIBLE** :  
  
 [!code-cpp[NVC_MFC_AxOpt#12](../mfc/codesnippet/CPP/providing-mouse-interaction-while-inactive_5.cpp)]  
  
## Vea también  
 [Controles ActiveX MFC: Optimización](../mfc/mfc-activex-controls-optimization.md)