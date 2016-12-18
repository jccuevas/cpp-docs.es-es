---
title: "Debugging and Error Reporting Macros | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "macros, informes de errores"
ms.assetid: 4da9b87f-ec5c-4a32-ab93-637780909b9d
caps.latest.revision: 18
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Debugging and Error Reporting Macros
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Estas macros proporcionan funciones útiles la depuración y traza.  
  
|||  
|-|-|  
|[\_ATL\_DEBUG\_INTERFACES](../Topic/_ATL_DEBUG_INTERFACES.md)|Escrituras, en la ventana de salida, cualquier escapes de interfaz se detectan que cuando se llama a `_Module.Term` .|  
|[\_ATL\_DEBUG\_QI](../Topic/_ATL_DEBUG_QI.md)|Escribe todas las llamadas a `QueryInterface` a la ventana de salida.|  
|[ATLASSERT](../Topic/ATLASSERT.md)|Realiza la misma funcionalidad que la macro de [\_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) encontrada en la biblioteca en tiempo de ejecución de C.|  
|[ATLENSURE](../Topic/ATLENSURE.md)|Realiza la validación de parámetros.  Llamada `AtlThrow` si es necesario|  
|[ATLTRACENOTIMPL](../Topic/ATLTRACENOTIMPL.md)|Envía un mensaje al dispositivo de volcado que la función especificada no está implementada.|  
|[ATLTRACE](../Topic/ATLTRACE%20\(ATL\).md)|Advertencias de los informes en un dispositivo de salida, como la ventana del depurador, según los marcadores y los niveles indicados.  Incluido por compatibilidad con versiones anteriores.|  
|[ATLTRA CE2](../Topic/ATLTRACE2.md)|Advertencias de los informes en un dispositivo de salida, como la ventana del depurador, según los marcadores y los niveles indicados.|  
  
## Vea también  
 [Macros](../../atl/reference/atl-macros.md)   
 [Debugging and Error Reporting Global Functions](../../atl/reference/debugging-and-error-reporting-global-functions.md)