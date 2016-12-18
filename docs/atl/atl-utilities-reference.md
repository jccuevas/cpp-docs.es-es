---
title: "Referencia de utilidades de ATL | Microsoft Docs"
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
ms.assetid: dd8a2888-34f4-461e-9bf4-834218f9b95b
caps.latest.revision: 8
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Referencia de utilidades de ATL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL proporciona el código para las rutas y las direcciones URL de manipulación en forma de [CPathT](../atl/reference/cpatht-class.md) y [rizo](../atl/reference/curl-class.md).  Un grupo de subprocesos, [CThreadPool](../atl/reference/cthreadpool-class.md), se puede utilizar en las aplicaciones.  Este código se encuentra en atlpath.h y atlutil.h.  
  
### Clases  
  
|||  
|-|-|  
|[clase de CPathT](../atl/reference/cpatht-class.md)|esta clase representa una ruta.|  
|[clase de CDebugReportHook](../atl/reference/cdebugreporthook-class.md)|Utilice esta clase para enviar informes de depuración a una canalización con nombre.|  
|[clase de CNonStatelessWorker](../atl/reference/cnonstatelessworker-class.md)|Recibe solicitudes de un grupo de subprocesos y las pasa en un objeto worker que se cree y se destruya en cada solicitud.|  
|[clase de CNoWorkerThread](../atl/reference/cnoworkerthread-class.md)|Utilice esta clase como el argumento para que el parámetro de plantilla de `MonitorClass` almacene en caché clases si desea deshabilitar mantenimiento dinámico de caché.|  
|[Clase CThreadPool](../atl/reference/cthreadpool-class.md)|Esta clase proporciona un grupo de subprocesos de trabajo que procesen una cola de elementos de trabajo.|  
|[Clase de rizo](../atl/reference/curl-class.md)|Esta clase representa una dirección URL.  Permite manipular cada elemento de la dirección URL independientemente de los demás si analiza una cadena existente de la dirección URL o compila una cadena desde el principio.|  
|[clase de CWorkerThread](../atl/reference/cworkerthread-class.md)|Esta clase crea un subproceso de trabajo o utiliza existente, espera en uno o más controladores de objeto de kernel, y ejecuta una función especificada del cliente a uno de los identificadores se señala.|  
  
### Typedefs  
  
|||  
|-|-|  
|[CPath](../Topic/CPath.md)|Una especialización de [CPathT](../atl/reference/cpatht-class.md) mediante `CString`.|  
|[CPathA](../Topic/CPathA.md)|Una especialización de [CPathT](../atl/reference/cpatht-class.md) mediante `CStringA`.|  
|[CPathW](../Topic/CPathW.md)|Una especialización de [CPathT](../atl/reference/cpatht-class.md) mediante `CStringW`.|  
|[ATL\_URL\_PORT](../Topic/ATL_URL_PORT.md)|el tipo utilizado por [rizo](../atl/reference/curl-class.md) para especificar un número de puerto.|  
  
### Enumeraciones  
  
|||  
|-|-|  
|[ATL\_URL\_SCHEME](../Topic/ATL_URL_SCHEME.md)|Los miembros de esta enumeración proporcionan las constantes para esquemas entendidos por [rizo](../atl/reference/curl-class.md).|  
  
### Funciones  
  
|||  
|-|-|  
|[AtlCanonicalizeUrl](../Topic/AtlCanonicalizeUrl.md)|Llame a esta función para canonicalize una dirección URL, que incluye convertir caracteres y espacios no seguros en secuencias de escape.|  
|[AtlCombineUrl](../Topic/AtlCombineUrl.md)|Llame a esta función para combinar una dirección URL base y una dirección URL relativa en una dirección URL única, canónica.|  
|[AtlEscapeUrl](../Topic/AtlEscapeUrl.md)|Llame a esta función para convertir todos los caracteres inseguros en secuencias de escape.|  
|[AtlGetDefaultUrlPort](../Topic/AtlGetDefaultUrlPort.md)|Llame a esta función para obtener el número de puerto predeterminado asociado con un Internet Protocol o un esquema determinado.|  
|[AtlHexValue](../Topic/AtlHexValue.md)|Llame a esta función para obtener el valor numérico de un dígito hexadecimal.|  
|[AtlIsUnsafeUrlChar](../Topic/AtlIsUnsafeUrlChar.md)|Llame a esta función para comprobar si un carácter es seguro para el uso en una dirección URL.|  
|[AtlUnescapeUrl](../Topic/AtlUnescapeUrl.md)|Llame a esta función para convertir los caracteres ASCII de nuevo a sus valores originales.|  
|[SystemTimeToHttpDate](../Topic/SystemTimeToHttpDate.md)|Llame a esta función para convertir una hora del sistema en una cadena en un formato adecuado para utilizar en encabezados HTTP.|  
|[ATLPath:: AddBackslash](../Topic/ATLPath::AddBackslash.md)|esta función es un contenedor sobrecargado para [PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561).|  
|[ATLPath:: AddExtension](../Topic/ATLPath::AddExtension.md)|esta función es un contenedor sobrecargado para [PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563).|  
|[ATLPath:: Anexar](../Topic/ATLPath::Append.md)|esta función es un contenedor sobrecargado para [PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565).|  
|[ATLPath:: BuildRoot](../Topic/ATLPath::BuildRoot.md)|esta función es un contenedor sobrecargado para [PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567).|  
|[ATLPath:: Canonicalize](../Topic/ATLPath::Canonicalize.md)|esta función es un contenedor sobrecargado para [PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569).|  
|[ATLPath:: Combine](../Topic/ATLPath::Combine.md)|esta función es un contenedor sobrecargado para [PathCombine](http://msdn.microsoft.com/library/windows/desktop/bb773571).|  
|[ATLPath:: CommonPrefix](../Topic/ATLPath::CommonPrefix.md)|esta función es un contenedor sobrecargado para [PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574).|  
|[ATLPath:: CompactPath](../Topic/ATLPath::CompactPath.md)|esta función es un contenedor sobrecargado para [PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575).|  
|[ATLPath:: CompactPathEx](../Topic/ATLPath::CompactPathEx.md)|esta función es un contenedor sobrecargado para [PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578).|  
|[ATLPath:: FileExists](../Topic/ATLPath::FileExists.md)|esta función es un contenedor sobrecargado para [PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584).|  
|[ATLPath:: FindExtension](../Topic/ATLPath::FindExtension.md)|esta función es un contenedor sobrecargado para [PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587).|  
|[ATLPath:: FindFileName](../Topic/ATLPath::FindFileName.md)|esta función es un contenedor sobrecargado para [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589).|  
|[ATLPath:: GetDriveNumber](../Topic/ATLPath::GetDriveNumber.md)|esta función es un contenedor sobrecargado para [PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612).|  
|[ATLPath:: IsDirectory](../Topic/ATLPath::IsDirectory.md)|esta función es un contenedor sobrecargado para [PathIsDirectory](http://msdn.microsoft.com/library/windows/desktop/bb773621).|  
|[ATLPath:: IsFileSpec](../Topic/ATLPath::IsFileSpec.md)|esta función es un contenedor sobrecargado para [PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627).|  
|[ATLPath:: IsPrefix](../Topic/ATLPath::IsPrefix.md)|esta función es un contenedor sobrecargado para [PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650).|  
|[ATLPath:: IsRelative](../Topic/ATLPath::IsRelative.md)|esta función es un contenedor sobrecargado para [PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660).|  
|[ATLPath:: IsRoot](../Topic/ATLPath::IsRoot.md)|esta función es un contenedor sobrecargado para [PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674).|  
|[ATLPath:: IsSameRoot](../Topic/ATLPath::IsSameRoot.md)|esta función es un contenedor sobrecargado para [PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687).|  
|[ATLPath:: IsUNC](../Topic/ATLPath::IsUNC.md)|esta función es un contenedor sobrecargado para [PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712).|  
|[ATLPath:: IsUNCServer](../Topic/ATLPath::IsUNCServer.md)|esta función es un contenedor sobrecargado para [PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722).|  
|[ATLPath:: IsUNCServerShare](../Topic/ATLPath::IsUNCServerShare.md)|esta función es un contenedor sobrecargado para [PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723).|  
|[ATLPath:: MakePretty](../Topic/ATLPath::MakePretty.md)|esta función es un contenedor sobrecargado para [PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725).|  
|[ATLPath:: MatchSpec](../Topic/ATLPath::MatchSpec.md)|esta función es un contenedor sobrecargado para [PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727).|  
|[ATLPath:: QuoteSpaces](../Topic/ATLPath::QuoteSpaces.md)|esta función es un contenedor sobrecargado para [PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739).|  
|[ATLPath:: RelativePathTo](../Topic/ATLPath::RelativePathTo.md)|esta función es un contenedor sobrecargado para [PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740).|  
|[ATLPath:: RemoveArgs](../Topic/ATLPath::RemoveArgs.md)|esta función es un contenedor sobrecargado para [PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742).|  
|[ATLPath:: RemoveBackslash](../Topic/ATLPath::RemoveBackslash.md)|esta función es un contenedor sobrecargado para [PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743).|  
|[ATLPath:: RemoveBlanks](../Topic/ATLPath::RemoveBlanks.md)|esta función es un contenedor sobrecargado para [PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745).|  
|[ATLPath:: RemoveExtension](../Topic/ATLPath::RemoveExtension.md)|esta función es un contenedor sobrecargado para [PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746).|  
|[ATLPath:: RemoveFileSpec](../Topic/ATLPath::RemoveFileSpec.md)|esta función es un contenedor sobrecargado para [PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748).|  
|[ATLPath:: RenameExtension](../Topic/ATLPath::RenameExtension.md)|esta función es un contenedor sobrecargado para [PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749).|  
|[ATLPath:: SkipRoot](../Topic/ATLPath::SkipRoot.md)|esta función es un contenedor sobrecargado para [PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754).|  
|[ATLPath:: StripPath](../Topic/ATLPath::StripPath.md)|esta función es un contenedor sobrecargado para [PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756).|  
|[ATLPath:: StripToRoot](../Topic/ATLPath::StripToRoot.md)|esta función es un contenedor sobrecargado para [PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757).|  
|[ATLPath:: UnquoteSpaces](../Topic/ATLPath::UnquoteSpaces.md)|esta función es un contenedor sobrecargado para [PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763).|  
  
### Macros  
  
|||  
|-|-|  
|[Marcadores de ATL\_URL](../Topic/ATL_URL%20Flags.md)|Estas marcas modifican el comportamiento de [AtlEscapeUrl](../Topic/AtlEscapeUrl.md) y de [AtlCanonicalizeUrl](../Topic/AtlCanonicalizeUrl.md) .|  
|[ATL\_WORKER\_THREAD\_WAIT](../Topic/ATL_WORKER_THREAD_WAIT.md)|Esta macro define el valor predeterminado en milisegundos que [CWorkerThread:: Apagado](../Topic/CWorkerThread::Shutdown.md) esperará el subproceso de trabajo para cerrar.|  
|[ATLS\_DEFAULT\_THREADPOOLSHUTDOWNTIMEOUT](../Topic/ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT.md)|esta macro define la hora predeterminada en milisegundos que [CThreadPool](../atl/reference/cthreadpool-class.md) esperará un subproceso para cerrar.|  
|[ATLS\_DEFAULT\_THREADSPERPROC](../Topic/ATLS_DEFAULT_THREADSPERPROC.md)|esta macro define el número predeterminado de subprocesos por el procesador utilizado por [CThreadPool](../atl/reference/cthreadpool-class.md).|  
  
## Vea también  
 [Conceptos](../atl/active-template-library-atl-concepts.md)   
 [ATL COM Desktop Components](../atl/atl-com-desktop-components.md)