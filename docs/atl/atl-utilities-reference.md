---
title: Referencia de utilidades de ATL
ms.date: 11/04/2016
ms.assetid: dd8a2888-34f4-461e-9bf4-834218f9b95b
ms.openlocfilehash: 6c1481929f832e6f810ce46773f328f278b503fa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491700"
---
# <a name="atl-utilities-reference"></a>Referencia de utilidades de ATL

ATL proporciona código para manipular las rutas de acceso y las direcciones URL en forma de [CPathT](../atl/reference/cpatht-class.md) y [rizo](../atl/reference/curl-class.md). Se puede usar un grupo de subprocesos, [CThreadPool](../atl/reference/cthreadpool-class.md), en las aplicaciones. Este código puede encontrarse en atlutil.h y atlutil.h.

### <a name="classes"></a>Clases

|||
|-|-|
|[CPathT (clase)](../atl/reference/cpatht-class.md)|Esta clase representa una ruta de acceso.|
|[CDebugReportHook (clase)](../atl/reference/cdebugreporthook-class.md)|Utilice esta clase para enviar informes de depuración a una canalización con nombre.|
|[CNonStatelessWorker (clase)](../atl/reference/cnonstatelessworker-class.md)|Recibe solicitudes de un grupo de subprocesos y las pasa a un objeto de trabajo que se crea y se destruye en cada solicitud.|
|[CNoWorkerThread (clase)](../atl/reference/cnoworkerthread-class.md)|Use esta clase como el argumento del parámetro `MonitorClass` de plantilla para almacenar en caché las clases si desea deshabilitar el mantenimiento de la caché dinámica.|
|[CThreadPool (clase)](../atl/reference/cthreadpool-class.md)|Esta clase proporciona un grupo de subprocesos de trabajo que procesan una cola de elementos de trabajo.|
|[CUrl (clase)](../atl/reference/curl-class.md)|Esta clase representa una dirección URL. Permite manipular cada elemento de la dirección URL independientemente de si se analiza una cadena de dirección URL existente o se crea una cadena desde cero.|
|[CWorkerThread (clase)](../atl/reference/cworkerthread-class.md)|Esta clase crea un subproceso de trabajo o utiliza uno existente, espera en uno o varios identificadores de objeto de kernel y ejecuta una función de cliente especificada cuando se señala uno de los identificadores.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[CPath](../atl/reference/atl-typedefs.md#cpath)|Una especialización de [CPathT](../atl/reference/cpatht-class.md) mediante `CString`.|
|[CPathA](../atl/reference/atl-typedefs.md#cpatha)|Una especialización de [CPathT](../atl/reference/cpatht-class.md) mediante `CStringA`.|
|[CPathW](../atl/reference/atl-typedefs.md#cpathw)|Una especialización de [CPathT](../atl/reference/cpatht-class.md) mediante `CStringW`.|
|[ATL_URL_PORT](../atl/reference/atl-typedefs.md#atl_url_port)|Tipo utilizado por [rizo](../atl/reference/curl-class.md) para especificar un número de puerto.|

### <a name="enums"></a>Enumeraciones

|||
|-|-|
|[ATL_URL_SCHEME](../atl/reference/atl-url-scheme-enum.md)|Los miembros de esta enumeración proporcionan constantes para los esquemas que comprende el [rizo](../atl/reference/curl-class.md).|

### <a name="functions"></a>Funciones

|||
|-|-|
|[AtlCanonicalizeUrl](../atl/reference/atl-http-utility-functions.md#atlcanonicalizeurl)|Llame a esta función para canonizar una dirección URL, que incluye la conversión de espacios y caracteres no seguros en secuencias de escape.|
|[AtlCombineUrl](../atl/reference/atl-http-utility-functions.md#atlcombineurl)|Llame a esta función para combinar una dirección URL base y una dirección URL relativa en una única dirección URL canónica.|
|[AtlEscapeUrl](../atl/reference/atl-http-utility-functions.md#atlescapeurl)|Llame a esta función para convertir todos los caracteres no seguros en secuencias de escape.|
|[AtlGetDefaultUrlPort](../atl/reference/atl-http-utility-functions.md#atlgetdefaulturlport)|Llame a esta función para obtener el número de puerto predeterminado asociado a un esquema o un protocolo de Internet determinado.|
|[AtlHexValue](../atl/reference/atl-text-encoding-functions.md#atlhexvalue)|Llame a esta función para obtener el valor numérico de un dígito hexadecimal.|
|[AtlIsUnsafeUrlChar](../atl/reference/atl-http-utility-functions.md#atlisunsafeurlchar)|Llame a esta función para comprobar si un carácter es seguro para usarlo en una dirección URL.|
|[AtlUnescapeUrl](../atl/reference/atl-http-utility-functions.md#atlunescapeurl)|Llame a esta función para convertir de nuevo los caracteres de escape en sus valores originales.|
|[SystemTimeToHttpDate](../atl/reference/atl-http-utility-functions.md#systemtimetohttpdate)|Llame a esta función para convertir una hora del sistema en una cadena con un formato adecuado para usarla en encabezados HTTP.|

|[ATLPath::AddBackslash](../atl/reference/atl-path-functions.md#addbackslash)| Esta función es un contenedor sobrecargado de [PathAddBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha
). | |[ ATLPath::AddExtension](../atl/reference/atl-path-functions.md#addextension)| Esta función es un contenedor sobrecargado de [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw). | |[ ATLPath::Append](../atl/reference/atl-path-functions.md#append)| Esta función es un contenedor sobrecargado de [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw). | |[ ATLPath::BuildRoot](../atl/reference/atl-path-functions.md#buildroot)| Esta función es un contenedor sobrecargado de [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw). | |[ ATLPath::Canonicalize](../atl/reference/atl-path-functions.md#canonicalize)| Esta función es un contenedor sobrecargado de [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew). | |[ ATLPath::Combine](../atl/reference/atl-path-functions.md#combine)| Esta función es un contenedor sobrecargado de [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew). | |[ ATLPath::CommonPrefix](../atl/reference/atl-path-functions.md#commonprefix)| Esta función es un contenedor sobrecargado de [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw). | |[ ATLPath::CompactPath](../atl/reference/atl-path-functions.md#compactpath)| Esta función es un contenedor sobrecargado de [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw). | |[ ATLPath::CompactPathEx](../atl/reference/atl-path-functions.md#compactpathex)| Esta función es un contenedor sobrecargado de [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw). | |[ ATLPath::FileExists](../atl/reference/atl-path-functions.md#fileexists)| Esta función es un contenedor sobrecargado de [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw). | |[ ATLPath::FindExtension](../atl/reference/atl-path-functions.md#findextension)| Esta función es un contenedor sobrecargado de [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw). | |[ ATLPath::FindFileName](../atl/reference/atl-path-functions.md#findfilename)| Esta función es un contenedor sobrecargado de [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew). | |[ ATLPath::GetDriveNumber](../atl/reference/atl-path-functions.md#getdrivenumber)| Esta función es un contenedor sobrecargado de [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw). | |[ ATLPath::IsDirectory](../atl/reference/atl-path-functions.md#isdirectory)| Esta función es un contenedor sobrecargado de [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw). | |[ ATLPath::IsFileSpec](../atl/reference/atl-path-functions.md#isfilespec)| Esta función es un contenedor sobrecargado de [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw). | |[ ATLPath::IsPrefix](../atl/reference/atl-path-functions.md#isprefix)| Esta función es un contenedor sobrecargado de [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw). | |[ ATLPath::IsRelative](../atl/reference/atl-path-functions.md#isrelative)| Esta función es un contenedor sobrecargado de [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew). | |[ ATLPath::IsRoot](../atl/reference/atl-path-functions.md#isroot)| Esta función es un contenedor sobrecargado de [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw). | |[ ATLPath::IsSameRoot](../atl/reference/atl-path-functions.md#issameroot)| Esta función es un contenedor sobrecargado de [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw). | |[ ATLPath::IsUNC](../atl/reference/atl-path-functions.md#isunc)| Esta función es un contenedor sobrecargado de [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw). | |[ ATLPath::IsUNCServer](../atl/reference/atl-path-functions.md#isuncserver)| Esta función es un contenedor sobrecargado de [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw). | |[ ATLPath::IsUNCServerShare](../atl/reference/atl-path-functions.md#isuncservershare)| Esta función es un contenedor sobrecargado de [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).| |[ATLPath::MakePretty](../atl/reference/atl-path-functions.md#makepretty)|This function is an overloaded wrapper for [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).| |[ATLPath::MatchSpec](../atl/reference/atl-path-functions.md#matchspec)|This function is an overloaded wrapper for [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).| |[ATLPath::QuoteSpaces](../atl/reference/atl-path-functions.md#quotespaces)|This function is an overloaded wrapper for [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).| |[ATLPath::RelativePathTo](../atl/reference/atl-path-functions.md#relativepathto)|This function is an overloaded wrapper for [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).| |[ATLPath::RemoveArgs](../atl/reference/atl-path-functions.md#removeargs)|This function is an overloaded wrapper for [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).| |[ATLPath::RemoveBackslash](../atl/reference/atl-path-functions.md#removebackslash)|This function is an overloaded wrapper for [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).| |[ATLPath::RemoveBlanks](../atl/reference/atl-path-functions.md#removeblanks)|This function is an overloaded wrapper for [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).| |[ATLPath::RemoveExtension](../atl/reference/atl-path-functions.md#removeextension)|This function is an overloaded wrapper for [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).| |[ATLPath::RemoveFileSpec](../atl/reference/atl-path-functions.md#removefilespec)|This function is an overloaded wrapper for [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).| |[ATLPath::RenameExtension](../atl/reference/atl-path-functions.md#renameextension)|This function is an overloaded wrapper for [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).| |[ATLPath::SkipRoot](../atl/reference/atl-path-functions.md#skiproot)|This function is an overloaded wrapper for [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).| |[ATLPath::StripPath](../atl/reference/atl-path-functions.md#strippath)|This function is an overloaded wrapper for [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).| |[ATLPath::StripToRoot](../atl/reference/atl-path-functions.md#striptoroot)|This function is an overloaded wrapper for [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).| |[ATLPath::UnquoteSpaces](../atl/reference/atl-path-functions.md#unquotespaces)|This function is an overloaded wrapper for [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).|

## <a name="see-also"></a>Vea también

[Conceptos](../atl/active-template-library-atl-concepts.md)<br/>
[Componentes de escritorio COM de ATL](../atl/atl-com-desktop-components.md)
