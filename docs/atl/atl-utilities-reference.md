---
title: Referencia de utilidades ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: dd8a2888-34f4-461e-9bf4-834218f9b95b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d11e06b7a8b8bc636de906a210cfffb62c6eeff4
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220325"
---
# <a name="atl-utilities-reference"></a>Referencia de utilidades de ATL
ATL proporciona código para manipular las rutas de acceso y direcciones URL en forma de [CPathT](../atl/reference/cpatht-class.md) y [CUrl](../atl/reference/curl-class.md). Un grupo de subprocesos, [CThreadPool](../atl/reference/cthreadpool-class.md), se puede usar en sus aplicaciones. Este código puede encontrarse en atlutil.h y atlpath.h en.  
  
### <a name="classes"></a>Clases  
  
|||  
|-|-|  
|[CPathT (clase)](../atl/reference/cpatht-class.md)|Esta clase representa una ruta de acceso.|  
|[CDebugReportHook (clase)](../atl/reference/cdebugreporthook-class.md)|Utilice esta clase para enviar informes de depuración a una canalización con nombre.|  
|[CNonStatelessWorker (clase)](../atl/reference/cnonstatelessworker-class.md)|Recibe solicitudes de un grupo de subprocesos y los pasa a un objeto de trabajo que se crea y destruye en cada solicitud.|  
|[CNoWorkerThread (clase)](../atl/reference/cnoworkerthread-class.md)|Utilice esta clase como argumento para el `MonitorClass` parámetro de plantilla a las clases de caché si desea deshabilitar el mantenimiento de la caché dinámica.|  
|[CThreadPool (clase)](../atl/reference/cthreadpool-class.md)|Esta clase proporciona un grupo de subprocesos de trabajo que procesan una cola de elementos de trabajo.|  
|[CUrl (clase)](../atl/reference/curl-class.md)|Esta clase representa una dirección URL. Permite manipular cada elemento de la dirección URL independientemente de los demás si una dirección URL existente de análisis de cadena o creación de una cadena desde el principio.|  
|[CWorkerThread (clase)](../atl/reference/cworkerthread-class.md)|Esta clase crea un subproceso de trabajo o usa uno existente, espera en uno o varios identificadores de objeto de kernel y ejecuta una función de cliente especificada cuando se señala a uno de los controladores.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[CPath](../atl/reference/atl-typedefs.md#cpath)|Una especialización de [CPathT](../atl/reference/cpatht-class.md) mediante `CString`.|  
|[CPathA](../atl/reference/atl-typedefs.md#cpatha)|Una especialización de [CPathT](../atl/reference/cpatht-class.md) mediante `CStringA`.|  
|[CPathW](../atl/reference/atl-typedefs.md#cpathw)|Una especialización de [CPathT](../atl/reference/cpatht-class.md) mediante `CStringW`.|  
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
|[AtlGetDefaultUrlPort](../atl/reference/atl-http-utility-functions.md#atlgetdefaulturlport)|Llame a esta función para obtener el número de puerto predeterminado asociado con un determinado protocolo de internet o un esquema.|  
|[AtlHexValue](../atl/reference/atl-text-encoding-functions.md#atlhexvalue)|Llame a esta función para obtener el valor numérico de un dígito hexadecimal.|  
|[AtlIsUnsafeUrlChar](../atl/reference/atl-http-utility-functions.md#atlisunsafeurlchar)|Llame a esta función para comprobar si un carácter es seguro para usarlo en una dirección URL.|  
|[AtlUnescapeUrl](../atl/reference/atl-http-utility-functions.md#atlunescapeurl)|Llame a esta función para convertir de nuevo los caracteres de escape en sus valores originales.|  
|[SystemTimeToHttpDate](../atl/reference/atl-http-utility-functions.md#systemtimetohttpdate)|Llame a esta función para convertir una hora del sistema en una cadena con un formato adecuado para usarla en encabezados HTTP.|  

|[ATLPath::AddBackslash](../atl/reference/atl-path-functions.md#addbackslash)| Esta función es un contenedor sobrecargado de [PathAddBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha
). |  
|[ATLPath::AddExtension](../atl/reference/atl-path-functions.md#addextension)| Esta función es un contenedor sobrecargado de [PathAddExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddextensiona). |  
|[ATLPath::Append](../atl/reference/atl-path-functions.md#append)| Esta función es un contenedor sobrecargado de [PathAppend](/windows/desktop/api/shlwapi/nf-shlwapi-pathappenda). |  
|[ATLPath::BuildRoot](../atl/reference/atl-path-functions.md#buildroot)| Esta función es un contenedor sobrecargado de [PathBuildRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathbuildroota). |  
|[ATLPath::Canonicalize](../atl/reference/atl-path-functions.md#canonicalize)| Esta función es un contenedor sobrecargado de [PathCanonicalize](/windows/desktop/api/shlwapi/nf-shlwapi-pathcanonicalizea). |  
|[ATLPath::Combine](../atl/reference/atl-path-functions.md#combine)| Esta función es un contenedor sobrecargado de [PathCombine](/windows/desktop/api/shlwapi/nf-shlwapi-pathcombinea). |  
|[ATLPath::CommonPrefix](../atl/reference/atl-path-functions.md#commonprefix)| Esta función es un contenedor sobrecargado de [PathCommonPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathcommonprefixa). |  
|[ATLPath::CompactPath](../atl/reference/atl-path-functions.md#compactpath)| Esta función es un contenedor sobrecargado de [PathCompactPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpatha). |  
|[ATLPath::CompactPathEx](../atl/reference/atl-path-functions.md#compactpathex)| Esta función es un contenedor sobrecargado de [PathCompactPathEx](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpathexa). |  
|[ATLPath::FileExists](../atl/reference/atl-path-functions.md#fileexists)| Esta función es un contenedor sobrecargado de [PathFileExists](/windows/desktop/api/shlwapi/nf-shlwapi-pathfileexistsa). |  
|[ATLPath::FindExtension](../atl/reference/atl-path-functions.md#findextension)| Esta función es un contenedor sobrecargado de [PathFindExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindextensiona). |  
|[ATLPath::FindFileName](../atl/reference/atl-path-functions.md#findfilename)| Esta función es un contenedor sobrecargado de [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea). |  
|[ATLPath::GetDriveNumber](../atl/reference/atl-path-functions.md#getdrivenumber)| Esta función es un contenedor sobrecargado de [PathGetDriveNumber](/windows/desktop/api/shlwapi/nf-shlwapi-pathgetdrivenumbera). |  
|[ATLPath::IsDirectory](../atl/reference/atl-path-functions.md#isdirectory)| Esta función es un contenedor sobrecargado de [PathIsDirectory](/windows/desktop/api/shlwapi/nf-shlwapi-pathisdirectorya). |  
|[ATLPath::IsFileSpec](../atl/reference/atl-path-functions.md#isfilespec)| Esta función es un contenedor sobrecargado de [PathIsFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathisfilespeca). |  
|[ATLPath::IsPrefix](../atl/reference/atl-path-functions.md#isprefix)| Esta función es un contenedor sobrecargado de [PathIsPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathisprefixa). |  
|[ATLPath::IsRelative](../atl/reference/atl-path-functions.md#isrelative)| Esta función es un contenedor sobrecargado de [PathIsRelative](/windows/desktop/api/shlwapi/nf-shlwapi-pathisrelativea). |  
|[ATLPath::IsRoot](../atl/reference/atl-path-functions.md#isroot)| Esta función es un contenedor sobrecargado de [PathIsRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathisroota). |  
|[ATLPath::IsSameRoot](../atl/reference/atl-path-functions.md#issameroot)| Esta función es un contenedor sobrecargado de [PathIsSameRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathissameroota). |  
|[ATLPath::IsUNC](../atl/reference/atl-path-functions.md#isunc)| Esta función es un contenedor sobrecargado de [PathIsUNC](/windows/desktop/api/shlwapi/nf-shlwapi-pathisunca). |  
|[ATLPath::IsUNCServer](../atl/reference/atl-path-functions.md#isuncserver)| Esta función es un contenedor sobrecargado de [PathIsUNCServer](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncservera). |  
|[ATLPath::IsUNCServerShare](../atl/reference/atl-path-functions.md#isuncservershare)| Esta función es un contenedor sobrecargado de [PathIsUNCServerShare](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncserversharea). |  
|[ATLPath::MakePretty](../atl/reference/atl-path-functions.md#makepretty)| Esta función es un contenedor sobrecargado de [PathMakePretty](/windows/desktop/api/shlwapi/nf-shlwapi-pathmakeprettya). |  
|[ATLPath::MatchSpec](../atl/reference/atl-path-functions.md#matchspec)| Esta función es un contenedor sobrecargado de [PathMatchSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathmatchspeca). |  
|[ATLPath::QuoteSpaces](../atl/reference/atl-path-functions.md#quotespaces)| Esta función es un contenedor sobrecargado de [PathQuoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathquotespacesa). |  
|[ATLPath::RelativePathTo](../atl/reference/atl-path-functions.md#relativepathto)| Esta función es un contenedor sobrecargado de [PathRelativePathTo](/windows/desktop/api/shlwapi/nf-shlwapi-pathrelativepathtoa). |  
|[ATLPath::RemoveArgs](../atl/reference/atl-path-functions.md#removeargs)| Esta función es un contenedor sobrecargado de [PathRemoveArgs](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveargsa). |  
|[ATLPath::RemoveBackslash](../atl/reference/atl-path-functions.md#removebackslash)| Esta función es un contenedor sobrecargado de [PathRemoveBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovebackslasha). |  
|[ATLPath::RemoveBlanks](../atl/reference/atl-path-functions.md#removeblanks)| Esta función es un contenedor sobrecargado de [PathRemoveBlanks](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveblanksa). |  
|[ATLPath::RemoveExtension](../atl/reference/atl-path-functions.md#removeextension)| Esta función es un contenedor sobrecargado de [PathRemoveExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveextensiona). |  
|[ATLPath::RemoveFileSpec](../atl/reference/atl-path-functions.md#removefilespec)| Esta función es un contenedor sobrecargado de [PathRemoveFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovefilespeca). |  
|[ATLPath::RenameExtension](../atl/reference/atl-path-functions.md#renameextension)| Esta función es un contenedor sobrecargado de [PathRenameExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathrenameextensiona). |  
|[ATLPath::SkipRoot](../atl/reference/atl-path-functions.md#skiproot)| Esta función es un contenedor sobrecargado de [PathSkipRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathskiproota). |  
|[ATLPath::StripPath](../atl/reference/atl-path-functions.md#strippath)| Esta función es un contenedor sobrecargado de [PathStripPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathstrippatha). |  
|[ATLPath::StripToRoot](../atl/reference/atl-path-functions.md#striptoroot)| Esta función es un contenedor sobrecargado de [PathStripToRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathstriptoroota). |  
|[ATLPath::UnquoteSpaces](../atl/reference/atl-path-functions.md#unquotespaces)| Esta función es un contenedor sobrecargado de [PathUnquoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathunquotespacesa). |  
  

## <a name="see-also"></a>Vea también  
 [Conceptos](../atl/active-template-library-atl-concepts.md)   
 [Componentes de escritorio COM de ATL](../atl/atl-com-desktop-components.md)
