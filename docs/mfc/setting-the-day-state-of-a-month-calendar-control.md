---
title: "Establecer Day State en un control de calendario mensual | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MCN_GETDAYSTATE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMonthCalCtrl (clase), establecer información sobre Day State"
  - "MCN_GETDAYSTATE (notificación)"
  - "controles del calendario mensual, información sobre Day State"
ms.assetid: 435d1b11-ec0e-4121-9e25-aaa6af812a3c
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Establecer Day State en un control de calendario mensual
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Uno de los atributos de un control de calendario mensual es la capacidad de almacenar información, denominada el estado del día del control, para cada día del mes.  Esta información se utiliza para hacer hincapié en determinadas fechas del mes mostrado actualmente.  
  
> [!NOTE]
>  El objeto de `CMonthCalCtrl` debe tener el estilo de **MCS\_DAYSTATE** para mostrar información de estado del día.  
  
 La información de estado del día se expresa como un tipo de datos de 32 bits, **MONTHDAYSTATE**.  Cada bit en un campo de bits de **MONTHDAYSTATE** \(1 a 31\) representa el estado de un día de un mes.  Si un bit está activado, el día correspondiente aparecerá en negrita; si no se mostrará sin enfoque.  
  
 Existen dos métodos para establecer el estado del día del control de calendario mensual: explícitamente mediante una llamada a [CMonthCalCtrl::SetDayState](../Topic/CMonthCalCtrl::SetDayState.md) o controlando el mensaje de notificación de **MCN\_GETDAYSTATE** .  
  
## Administrar el mensaje de notificación de MCN\_GETDAYSTATE  
 El mensaje de **MCN\_GETDAYSTATE** es enviado por el control para determinar cómo los días de meses visible deben mostrarse.  
  
> [!NOTE]
>  Dado que el control almacena en memoria caché el anterior y meses de siguiente, por lo que se refiere al mes visible, recibirá esta notificación cada vez que se elige un nuevo mes.  
  
 Para controlar correctamente este mensaje, debe determinar por se solicita información de estado del día del número de meses, inicializa una matriz de estructuras de **MONTHDAYSTATE** con los valores adecuados, e inicializa el miembro de estructura relacionado con nueva información.  El procedimiento siguiente, detallando los pasos necesarios, se supone que tiene un objeto de `CMonthCalCtrl` denominado `m_monthcal` y una matriz de los objetos de **MONTHDAYSTATE** , `mdState`.  
  
#### Para controlar el mensaje de notificación de MCN\_GETDAYSTATE  
  
1.  Mediante la ventana Propiedades, agregue un controlador de notificación para el mensaje de **MCN\_GETDAYSTATE** al objeto de `m_monthcal` \(vea [Asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)\).  
  
2.  En el cuerpo del controlador, agregue el código siguiente:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/CPP/setting-the-day-state-of-a-month-calendar-control_1.cpp)]  
  
     El ejemplo convierte el puntero de `pNMHDR` el tipo correspondiente, determina cuántos meses de información se solicitan \(`pDayState->cDayState`\).  Para cada mes, el campo de bits actual \(`pDayState->prgDayState[i]`\) se inicializa en cero y después las fechas necesarias se establece en \(en este caso, el decimoquinto de cada mes\).  
  
## Vea también  
 [Usar CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [Controles](../mfc/controls-mfc.md)