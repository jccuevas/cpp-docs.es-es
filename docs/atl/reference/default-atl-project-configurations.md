---
title: Configuraciones de proyectos ATL predeterminadas | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, default configurations
ms.assetid: 7e272722-41af-4330-b965-a6d74ec16880
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6cad5222fb0d97594d5b13b5cf8903eb2934ee88
ms.openlocfilehash: 41ab65c411bef478d063e5165d3167f58ace37d7
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="default-atl-project-configurations"></a>Configuraciones predeterminadas de proyecto ATL
Este tema comparan las configuraciones de proyecto ATL de forma predeterminada en Visual C++ .NET con las configuraciones de proyecto predeterminadas en Visual C++ 6.0.  
  
## <a name="visual-c-net-default-configurations"></a>Configuraciones predeterminadas en Visual C++ .NET  
 En Visual C++. NET, el Asistente para proyectos ATL crea dos configuraciones de proyecto de forma predeterminada.  
  
### <a name="visual-c-net-configurations"></a>Configuraciones en Visual C++ .NET  
  
|Configuración|Juego de caracteres|Uso de ATL|  
|-------------------|-------------------|----------------|  
|Versión|MBCS|Archivo DLL|  
|Depurar|MBCS|Archivo DLL|  
  
 **Juego de caracteres**, **uso de ATL** y puede cambiarse en el **configuración del proyecto** cuadro de diálogo en el **General** ficha. También puede agregar sus propias configuraciones mediante el Administrador de configuración. Para obtener más información, consulte [las configuraciones de compilación](/visualstudio/ide/understanding-build-configurations).  
  
## <a name="version-60-default-configurations"></a>Configuraciones predeterminadas de la versión 6.0  
 En Visual C++ versión 6.0, el Asistente para aplicaciones COM ATL (que ahora se llama al Asistente para proyectos ATL) creaba seis configuraciones de proyecto de forma predeterminada. Las configuraciones eran variaciones de lanzamiento, depurar, Unicode y uso de CRT y ATL. Todas estas configuraciones se pueden duplicar en Visual C++ .NET mediante el Administrador de configuración, si así lo desea.  
  
### <a name="version-60-configurations"></a>Configuraciones de la versión 6.0  
  
|Configuración|Juego de caracteres|Uso de ATL|  
|-------------------|-------------------|----------------|  
|Depurar|MBCS|Estático|  
|Depurar Unicode|UNICODE|Estático|  
|Liberar dependencia mínima|MBCS|Estático|  
|Liberar Unicode de dependencia mínima|UNICODE|Estático|  
|Tamaño mínimo de versión|MBCS|Archivo DLL|  
|Liberar Unicode de tamaño mínimo|UNICODE|Archivo DLL|  
  
## <a name="see-also"></a>Vea también  
 [Programar con ATL y el código de tiempo de ejecución de C](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Trabajar con propiedades de proyecto](../../ide/working-with-project-properties.md)   
 [Cuadro de diálogo Administrador de configuración](http://msdn.microsoft.com/en-us/fa182dca-282e-4ae5-bf37-e155344ca18b)   
 [Compilar y generar en Visual Studio](/visualstudio/ide/compiling-and-building-in-visual-studio)


