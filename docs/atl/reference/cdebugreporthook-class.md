---
title: "CDebugReportHook Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CDebugReportHook"
  - "CDebugReportHook"
  - "ATL::CDebugReportHook"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDebugReportHook class"
ms.assetid: 798076c3-6e63-4286-83b8-aa1bbcd0c20c
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CDebugReportHook Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Utilice esta clase para enviar informes de depuración a una canalización con nombre.  
  
## Sintaxis  
  
```  
  
class CDebugReportHook  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDebugReportHook::CDebugReportHook](../Topic/CDebugReportHook::CDebugReportHook.md)|llamadas [SetPipeName](../Topic/CDebugReportHook::SetPipeName.md), [SetTimeout](../Topic/CDebugReportHook::SetTimeout.md), y [SetHook](../Topic/CDebugReportHook::SetHook.md).|  
|[CDebugReportHook::~CDebugReportHook](../Topic/CDebugReportHook::~CDebugReportHook.md)|llamadas [CDebugReportHook:: RemoveHook](../Topic/CDebugReportHook::RemoveHook.md).|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDebugReportHook::CDebugReportHookProc](../Topic/CDebugReportHook::CDebugReportHookProc.md)|\(Estático\) función de supervisión personalizada a El que se enlaza en el proceso de informe de depuración en tiempo de ejecución de C.|  
|[CDebugReportHook::RemoveHook](../Topic/CDebugReportHook::RemoveHook.md)|Llame a este método para detener el envío de informes de la depuración a la canalización con nombre y restaurar el enlace anterior del informe.|  
|[CDebugReportHook::SetHook](../Topic/CDebugReportHook::SetHook.md)|Llame a este método para iniciar el envío de informes de la depuración a la canalización con nombre.|  
|[CDebugReportHook::SetPipeName](../Topic/CDebugReportHook::SetPipeName.md)|Llame a este método para establecer el equipo y el nombre de la canalización en la que los informes de depuración se enviará.|  
|[CDebugReportHook::SetTimeout](../Topic/CDebugReportHook::SetTimeout.md)|Llame a este método para establecer la hora en milisegundos que esta clase esperará la canalización con nombre esté disponible.|  
  
## Comentarios  
 Cree una instancia de esta clase en las versiones de depuración de los servicios o aplicaciones de enviar informes de depuración a una canalización con nombre.  Los informes de depuración se generan llamando a [\_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) o mediante un contenedor para esta función como macros de [ATLTRACE](../Topic/ATLTRACE%20\(ATL\).md) y de [ATLASSERT](../Topic/ATLASSERT.md) .  
  
 El uso de esta clase permite depurar interactivamente los componentes que se ejecutan en [estaciones de la ventana](http://msdn.microsoft.com/library/windows/desktop/ms687096)no interactivo.  
  
 Observe que los informes de depuración se enviados utilizando el contexto de seguridad subyacente del subproceso.  La suplantación se deshabilita temporalmente para ver informes de depuración en situaciones donde está teniendo lugar la suplantación de usuarios bajos de privilegios, por ejemplo en aplicaciones Web.  
  
## Requisitos  
 **encabezado:** atlutil.h  
  
## Vea también  
 [Clases](../../atl/reference/atl-classes.md)