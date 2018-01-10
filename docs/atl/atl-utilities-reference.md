---
title: Referencia de utilidades ATL | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: dd8a2888-34f4-461e-9bf4-834218f9b95b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 69f085df8b5dadbd0ba9d20596d37cb6313bb3f0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="atl-utilities-reference"></a>Referencia de utilidades de ATL
ATL proporciona código para manipular las rutas de acceso y las direcciones URL en forma de [CPathT](../atl/reference/cpatht-class.md) y [CUrl](../atl/reference/curl-class.md). Un grupo de subprocesos, [CThreadPool](../atl/reference/cthreadpool-class.md), puede utilizar en las aplicaciones. Este código se puede encontrar en atlpath.h y atlutil.h.  
  
### <a name="classes"></a>Clases  
  
|||  
|-|-|  
|[CPathT (clase)](../atl/reference/cpatht-class.md)|Esta clase representa una ruta de acceso.|  
|[CDebugReportHook (clase)](../atl/reference/cdebugreporthook-class.md)|Utilice esta clase para enviar informes de depuración a una canalización con nombre.|  
|[CNonStatelessWorker (clase)](../atl/reference/cnonstatelessworker-class.md)|Recibe solicitudes de un grupo de subprocesos y los pasa a un objeto de trabajo que se crea y se destruye en cada solicitud.|  
|[CNoWorkerThread (clase)](../atl/reference/cnoworkerthread-class.md)|Utilice esta clase como argumento para el `MonitorClass` parámetro de plantilla a las clases de caché si desea deshabilitar el mantenimiento de la memoria caché dinámica.|  
|[CThreadPool (clase)](../atl/reference/cthreadpool-class.md)|Esta clase proporciona un grupo de subprocesos de trabajo que procesan una cola de elementos de trabajo.|  
|[CUrl (clase)](../atl/reference/curl-class.md)|Esta clase representa una dirección URL. Permite manipular cada elemento de la dirección URL independientemente de las otras si analizar una dirección URL existente cadena o generar una cadena desde el principio.|  
|[CWorkerThread (clase)](../atl/reference/cworkerthread-class.md)|Esta clase crea un subproceso de trabajo o usa uno existente, espera a que en uno o varios identificadores de objeto de kernel y ejecuta una función de cliente especificado cuando se señala a uno de los controladores.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[CPath](../atl/reference/atl-typedefs.md#cpath)|Una especialización de [CPathT](../atl/reference/cpatht-class.md) con `CString`.|  
|[CPathA](../atl/reference/atl-typedefs.md#cpatha)|Una especialización de [CPathT](../atl/reference/cpatht-class.md) con `CStringA`.|  
|[CPathW](../atl/reference/atl-typedefs.md#cpathw)|Una especialización de [CPathT](../atl/reference/cpatht-class.md) con `CStringW`.|  
|[ATL_URL_PORT](../atl/reference/atl-typedefs.md#atl_url_port)|El tipo utilizado por [CUrl](../atl/reference/curl-class.md) para especificar un número de puerto.|  
  
### <a name="enums"></a>Enumeraciones  
  
|||  
|-|-|  
|[ATL_URL_SCHEME](../atl/reference/atl-url-scheme-enum.md)|Los miembros de esta enumeración proporcionan constantes para los esquemas entendidos [CUrl](../atl/reference/curl-class.md).|  
  
### <a name="functions"></a>Funciones  
  
|||  
|-|-|  
|[AtlCanonicalizeUrl](../atl/reference/atl-http-utility-functions.md#atlcanonicalizeurl)|Llame a esta función para canonizar una dirección URL, que incluye la conversión de espacios y caracteres no seguros en secuencias de escape.|  
|[AtlCombineUrl](../atl/reference/atl-http-utility-functions.md#atlcombineurl)|Llame a esta función para combinar una dirección URL base y una dirección URL relativa en una única dirección URL canónica.|  
|[AtlEscapeUrl](../atl/reference/atl-http-utility-functions.md#atlescapeurl)|Llame a esta función para convertir todos los caracteres no seguros en secuencias de escape.|  
|[AtlGetDefaultUrlPort](../atl/reference/atl-http-utility-functions.md#atlgetdefaulturlport)|Llame a esta función para obtener el número de puerto predeterminado asociado a un determinado protocolo de internet o un esquema.|  
|[AtlHexValue](../atl/reference/atl-text-encoding-functions.md#atlhexvalue)|Llame a esta función para obtener el valor numérico de un dígito hexadecimal.|  
|[AtlIsUnsafeUrlChar](../atl/reference/atl-http-utility-functions.md#atlisunsafeurlchar)|Llame a esta función para comprobar si un carácter es seguro para usarlo en una dirección URL.|  
|[AtlUnescapeUrl](../atl/reference/atl-http-utility-functions.md#atlunescapeurl)|Llame a esta función para convertir de nuevo los caracteres de escape en sus valores originales.|  
|[SystemTimeToHttpDate](../atl/reference/atl-http-utility-functions.md#systemtimetohttpdate)|Llame a esta función para convertir una hora del sistema en una cadena con un formato adecuado para usarla en encabezados HTTP.|  

|[ATLPath::AddBackslash](../atl/reference/atl-path-functions.md#addbackslash)| Esta función es un contenedor sobrecargado de [PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561). |  
|[ATLPath::AddExtension](../atl/reference/atl-path-functions.md#addextension)| Esta función es un contenedor sobrecargado de [PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563). |  
|[ATLPath::Append](../atl/reference/atl-path-functions.md#append)| Esta función es un contenedor sobrecargado de [PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565). |  
|[ATLPath::BuildRoot](../atl/reference/atl-path-functions.md#buildroot)| Esta función es un contenedor sobrecargado de [PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567). |  
|[ATLPath::Canonicalize](../atl/reference/atl-path-functions.md#canonicalize)| Esta función es un contenedor sobrecargado de [PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569). |  
|[ATLPath::Combine](../atl/reference/atl-path-functions.md#combine)| Esta función es un contenedor sobrecargado de [PathCombine](http://msdn.microsoft.com/library/windows/desktop/bb773571). |  
|[ATLPath::CommonPrefix](../atl/reference/atl-path-functions.md#commonprefix)| Esta función es un contenedor sobrecargado de [PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574). |  
|[ATLPath::CompactPath](../atl/reference/atl-path-functions.md#compactpath)| Esta función es un contenedor sobrecargado de [PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575). |  
|[ATLPath::CompactPathEx](../atl/reference/atl-path-functions.md#compactpathex)| Esta función es un contenedor sobrecargado de [PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578). |  
|[ATLPath::FileExists](../atl/reference/atl-path-functions.md#fileexists)| Esta función es un contenedor sobrecargado de [PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584). |  
|[ATLPath::FindExtension](../atl/reference/atl-path-functions.md#findextension)| Esta función es un contenedor sobrecargado de [PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587). |  
|[ATLPath::FindFileName](../atl/reference/atl-path-functions.md#findfilename)| Esta función es un contenedor sobrecargado de [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589). |  
|[ATLPath::GetDriveNumber](../atl/reference/atl-path-functions.md#getdrivenumber)| Esta función es un contenedor sobrecargado de [PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612). |  
|[ATLPath::IsDirectory](../atl/reference/atl-path-functions.md#isdirectory)| Esta función es un contenedor sobrecargado de [PathIsDirectory](http://msdn.microsoft.com/library/windows/desktop/bb773621). |  
|[ATLPath::IsFileSpec](../atl/reference/atl-path-functions.md#isfilespec)| Esta función es un contenedor sobrecargado de [PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627). |  
|[ATLPath::IsPrefix](../atl/reference/atl-path-functions.md#isprefix)| Esta función es un contenedor sobrecargado de [PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650). |  
|[ATLPath::IsRelative](../atl/reference/atl-path-functions.md#isrelative)| Esta función es un contenedor sobrecargado de [PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660). |  
|[ATLPath::IsRoot](../atl/reference/atl-path-functions.md#isroot)| Esta función es un contenedor sobrecargado de [PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674). |  
|[ATLPath::IsSameRoot](../atl/reference/atl-path-functions.md#issameroot)| Esta función es un contenedor sobrecargado de [PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687). |  
|[ATLPath::IsUNC](../atl/reference/atl-path-functions.md#isunc)| Esta función es un contenedor sobrecargado de [PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712). |  
|[ATLPath::IsUNCServer](../atl/reference/atl-path-functions.md#isuncserver)| Esta función es un contenedor sobrecargado de [PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722). |  
|[ATLPath::IsUNCServerShare](../atl/reference/atl-path-functions.md#isuncservershare)| Esta función es un contenedor sobrecargado de [PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723). |  
|[ATLPath::MakePretty](../atl/reference/atl-path-functions.md#makepretty)| Esta función es un contenedor sobrecargado de [PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725). |  
|[ATLPath::MatchSpec](../atl/reference/atl-path-functions.md#matchspec)| Esta función es un contenedor sobrecargado de [PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727). |  
|[ATLPath::QuoteSpaces](../atl/reference/atl-path-functions.md#quotespaces)| Esta función es un contenedor sobrecargado de [PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739). |  
|[ATLPath::RelativePathTo](../atl/reference/atl-path-functions.md#relativepathto)| Esta función es un contenedor sobrecargado de [PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740). |  
|[ATLPath::RemoveArgs](../atl/reference/atl-path-functions.md#removeargs)| Esta función es un contenedor sobrecargado de [PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742). |  
|[ATLPath::RemoveBackslash](../atl/reference/atl-path-functions.md#removebackslash)| Esta función es un contenedor sobrecargado de [PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743). |  
|[ATLPath::RemoveBlanks](../atl/reference/atl-path-functions.md#removeblanks)| Esta función es un contenedor sobrecargado de [PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745). |  
|[ATLPath::RemoveExtension](../atl/reference/atl-path-functions.md#removeextension)| Esta función es un contenedor sobrecargado de [PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746). |  
|[ATLPath::RemoveFileSpec](../atl/reference/atl-path-functions.md#removefilespec)| Esta función es un contenedor sobrecargado de [PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748). |  
|[ATLPath::RenameExtension](../atl/reference/atl-path-functions.md#renameextension)| Esta función es un contenedor sobrecargado de [PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749). |  
|[ATLPath::SkipRoot](../atl/reference/atl-path-functions.md#skiproot)| Esta función es un contenedor sobrecargado de [PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754). |  
|[ATLPath::StripPath](../atl/reference/atl-path-functions.md#strippath)| Esta función es un contenedor sobrecargado de [PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756). |  
|[ATLPath::StripToRoot](../atl/reference/atl-path-functions.md#striptoroot)| Esta función es un contenedor sobrecargado de [PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757). |  
|[ATLPath::UnquoteSpaces](../atl/reference/atl-path-functions.md#unquotespaces)| Esta función es un contenedor sobrecargado de [PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763). |  
  

## <a name="see-also"></a>Vea también  
 [Conceptos](../atl/active-template-library-atl-concepts.md)   
 [Componentes de escritorio COM de ATL](../atl/atl-com-desktop-components.md)
