---
title: "Debugging and Error Reporting Global Functions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "funciones [ATL], informes de errores"
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# Debugging and Error Reporting Global Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Estas funciones proporcionan funciones útiles la depuración y traza.  
  
|||  
|-|-|  
|[AtlHresultFromLastError](../Topic/AtlHresultFromLastError.md)|Devuelve un código de error de `GetLastError` en forma de HRESULT.|  
|[AtlHresultFromWin32](../Topic/AtlHresultFromWin32.md)|convierte un código de error de Win32 en un HRESULT.|  
|[AtlReportError](../Topic/AtlReportError.md)|Colocan **IErrorInfo** para proporcionar los detalles del error a un cliente.|  
|[AtlThrow](../Topic/AtlThrow.md)|Produce una excepción `CAtlException`.|  
|[AtlThrowLastWin32](../Topic/AtlThrowLastWin32.md)|Llame a esta función para notificar un error en función del resultado de la función de Windows `GetLastError`.|  
|[AtlTraceLoadSettings](../../misc/atltraceloadsettings.md)|Llame a esta función para cargar valores de seguimiento de un archivo.|  
|[AtlTraceSaveSettings](../../misc/atltracesavesettings.md)|Llame a esta función para guardar la configuración de seguimiento actual de un archivo.|  
  
## Vea también  
 [Funciones](../../atl/reference/atl-functions.md)   
 [Debugging and Error Reporting Macros](../../atl/reference/debugging-and-error-reporting-macros.md)