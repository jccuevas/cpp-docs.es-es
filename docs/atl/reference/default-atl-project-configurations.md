---
title: "Configuraciones predeterminadas de un proyecto ATL | Microsoft Docs"
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
  - "ATL projects, configuraciones predeterminadas"
ms.assetid: 7e272722-41af-4330-b965-a6d74ec16880
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Configuraciones predeterminadas de un proyecto ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este tema se comparan las configuraciones predeterminadas de un proyecto ATL en Visual C\+\+ .NET con sus equivalentes en Visual C\+\+ 6.0.  
  
## Configuraciones predeterminadas en Visual C\+\+ .NET  
 En Visual C\+\+ .NET, el Asistente para proyectos ATL crea dos configuraciones de proyecto de forma predeterminada.  
  
### Configuraciones en Visual C\+\+ .NET  
  
|Configuración.|Juego de caracteres|Uso de ATL|  
|--------------------|-------------------------|----------------|  
|Versión de lanzamiento|MBCS|Archivo DLL|  
|Depuración|MBCS|Archivo DLL|  
  
 Las configuraciones de **Juego de caracteres** y **Uso de ATL** se pueden cambiar en el cuadro de diálogo **Configuración del proyecto** de la ficha **General**.  También puede agregar sus propias configuraciones mediante el Administrador de configuración.  Para obtener más información, vea [Configuraciones de compilación](../Topic/Understanding%20Build%20Configurations.md).  
  
## Configuraciones predeterminadas en la versión 6.0  
 En Visual C\+\+ versión 6.0, el Asistente para aplicaciones COM ATL \(que ahora se denomina Asistente para proyectos ATL\) creaba seis configuraciones de proyecto de forma predeterminada.  Las configuraciones eran variaciones de las opciones Liberar, Depurar, Unicode y Uso de CRT y ATL.  Estas configuraciones se pueden duplicar en Visual C\+\+ .NET mediante el Administrador de configuración, si se desea.  
  
### Configuraciones de la versión 6.0  
  
|Configuración.|Juego de caracteres|Uso de ATL|  
|--------------------|-------------------------|----------------|  
|Depuración|MBCS|Static|  
|Depurar Unicode|UNICODE|Static|  
|Liberar dependencia mínima|MBCS|Static|  
|Liberar Unicode de dependencia mínima|UNICODE|Static|  
|Liberar tamaño mínimo|MBCS|Archivo DLL|  
|Liberar Unicode de tamaño mínimo|UNICODE|Archivo DLL|  
  
## Vea también  
 [Programar con ATL y código en tiempo de ejecución de C](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md)   
 [Configuration Manager Dialog Box](http://msdn.microsoft.com/es-es/fa182dca-282e-4ae5-bf37-e155344ca18b)   
 [Compilar aplicaciones en Visual Studio](../Topic/Compiling%20and%20Building%20in%20Visual%20Studio.md)