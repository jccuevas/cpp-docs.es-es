---
title: Clase CPathT | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPathT
- ATLPATH/ATL::CPathT
- ATLPATH/ATL::CPathT::PCXSTR
- ATLPATH/ATL::CPathT::PXSTR
- ATLPATH/ATL::CPathT::XCHAR
- ATLPATH/ATL::CPathT::CPathT
- ATLPATH/ATL::CPathT::AddBackslash
- ATLPATH/ATL::CPathT::AddExtension
- ATLPATH/ATL::CPathT::Append
- ATLPATH/ATL::CPathT::BuildRoot
- ATLPATH/ATL::CPathT::Canonicalize
- ATLPATH/ATL::CPathT::Combine
- ATLPATH/ATL::CPathT::CommonPrefix
- ATLPATH/ATL::CPathT::CompactPath
- ATLPATH/ATL::CPathT::CompactPathEx
- ATLPATH/ATL::CPathT::FileExists
- ATLPATH/ATL::CPathT::FindExtension
- ATLPATH/ATL::CPathT::FindFileName
- ATLPATH/ATL::CPathT::GetDriveNumber
- ATLPATH/ATL::CPathT::GetExtension
- ATLPATH/ATL::CPathT::IsDirectory
- ATLPATH/ATL::CPathT::IsFileSpec
- ATLPATH/ATL::CPathT::IsPrefix
- ATLPATH/ATL::CPathT::IsRelative
- ATLPATH/ATL::CPathT::IsRoot
- ATLPATH/ATL::CPathT::IsSameRoot
- ATLPATH/ATL::CPathT::IsUNC
- ATLPATH/ATL::CPathT::IsUNCServer
- ATLPATH/ATL::CPathT::IsUNCServerShare
- ATLPATH/ATL::CPathT::MakePretty
- ATLPATH/ATL::CPathT::MatchSpec
- ATLPATH/ATL::CPathT::QuoteSpaces
- ATLPATH/ATL::CPathT::RelativePathTo
- ATLPATH/ATL::CPathT::RemoveArgs
- ATLPATH/ATL::CPathT::RemoveBackslash
- ATLPATH/ATL::CPathT::RemoveBlanks
- ATLPATH/ATL::CPathT::RemoveExtension
- ATLPATH/ATL::CPathT::RemoveFileSpec
- ATLPATH/ATL::CPathT::RenameExtension
- ATLPATH/ATL::CPathT::SkipRoot
- ATLPATH/ATL::CPathT::StripPath
- ATLPATH/ATL::CPathT::StripToRoot
- ATLPATH/ATL::CPathT::UnquoteSpaces
- ATLPATH/ATL::CPathT::m_strPath
dev_langs:
- C++
helpviewer_keywords:
- CPathT class
ms.assetid: eba4137d-1fd2-4b44-a2e1-0944db64df3c
caps.latest.revision: 20
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 98b00e3f888d5f6bfb33f6ee24c4af2860bb470f
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="cpatht-class"></a>Clase CPathT
Esta clase representa una ruta de acceso.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <typename StringType>
class CPathT
```  
  
#### <a name="parameters"></a>Parámetros  
 `StringType`  
 La clase de cadena ATL y MFC que se usará para la ruta de acceso (vea [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)).  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPathT::PCXSTR](#pcxstr)|Un tipo de cadena constante.|  
|[CPathT::PXSTR](#pxstr)|Un tipo de cadena.|  
|[CPathT::XCHAR](#xchar)|Tipo de carácter.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPathT::CPathT](#cpatht)|El constructor para la ruta de acceso.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPathT::AddBackslash](#addbackslash)|Llamar a este método para agregar una barra diagonal inversa al final de una cadena para crear la sintaxis correcta para una ruta de acceso.|  
|[CPathT::AddExtension](#addextension)|Llamar a este método para agregar una extensión de archivo a una ruta de acceso.|  
|[CPathT::Append](#append)|Llame a este método para anexar una cadena a la ruta de acceso actual.|  
|[CPathT::BuildRoot](#buildroot)|Llame a este método para crear una ruta de acceso raíz de un número de unidad determinada.|  
|[CPathT::Canonicalize](#canonicalize)|Llamar a este método para convertir la ruta de acceso en forma canónica.|  
|[CPathT::Combine](#combine)|Llame a este método para concatenar una cadena que representa un nombre de directorio y una cadena que representa un nombre de ruta de acceso de archivo en una ruta de acceso.|  
|[CPathT::CommonPrefix](#commonprefix)|Llamar a este método para determinar si la ruta de acceso especificada comparte un prefijo común con la ruta de acceso actual.|  
|[CPathT::CompactPath](#compactpath)|Llamar a este método para truncar una ruta de acceso de archivo para ajustarse a un ancho de píxel determinado mediante la sustitución de componentes de ruta de acceso con puntos suspensivos.|  
|[CPathT::CompactPathEx](#compactpathex)|Llamar a este método para truncar una ruta de acceso de archivo para que se ajusten dentro de un número determinado de caracteres mediante la sustitución de componentes de ruta de acceso con puntos suspensivos.|  
|[CPathT::FileExists](#fileexists)|Llame a este método para comprobar si existe el archivo en este nombre de ruta de acceso.|  
|[CPathT::FindExtension](#findextension)|Llame a este método para buscar la posición de la extensión de archivo en la ruta de acceso.|  
|[CPathT::FindFileName](#findfilename)|Llame a este método para buscar la posición del nombre de archivo en la ruta de acceso.|  
|[CPathT::GetDriveNumber](#getdrivenumber)|Llamar a este método para buscar la ruta de acceso de una letra de unidad en el intervalo de 'A' a la 'Z' y devolver el número de unidad correspondiente.|  
|[CPathT::GetExtension](#getextension)|Llamar a este método para obtener la extensión de archivo de la ruta de acceso.|  
|[CPathT::IsDirectory](#isdirectory)|Llamar a este método para comprobar si la ruta de acceso es un directorio válido.|  
|[CPathT::IsFileSpec](#isfilespec)|Llamar a este método para buscar una ruta de acceso para cualquier carácter delimitadoras de ruta de acceso (por ejemplo, ':' o '\\'). Si no hay ningún carácter delimitadoras de ruta de acceso está presente, se considera que la ruta de acceso es una ruta de acceso de la especificación de archivo.|  
|[CPathT::IsPrefix](#isprefix)|Llamar a este método para determinar si una ruta de acceso contiene un prefijo válido del tipo pasado por `pszPrefix`.|  
|[CPathT::IsRelative](#isrelative)|Llamar a este método para determinar si la ruta de acceso es relativa.|  
|[CPathT::IsRoot](#isroot)|Llamar a este método para determinar si la ruta de acceso es una directorio raíz.|  
|[CPathT::IsSameRoot](#issameroot)|Llamar a este método para determinar si otra ruta de acceso tiene un componente de raíz común con la ruta de acceso actual.|  
|[CPathT::IsUNC](#isunc)|Llamar a este método para determinar si la ruta de acceso es una ruta de acceso UNC (convención de nomenclatura universal) válida para un servidor y compartir.|  
|[CPathT::IsUNCServer](#isuncserver)|Llamar a este método para determinar si la ruta de acceso es una ruta de acceso UNC (convención de nomenclatura universal) válida para un solo servidor.|  
|[CPathT::IsUNCServerShare](#isuncservershare)|Llamar a este método para determinar si la ruta de acceso es una ruta válida de recurso compartido UNC (convención de nomenclatura universal), \\ \  *server*\ *compartir*.|  
|[CPathT::MakePretty](#makepretty)|Llamar a este método para convertir una ruta de acceso a todos los caracteres en minúsculas para dar una apariencia coherente de la ruta de acceso.|  
|[CPathT::MatchSpec](#matchspec)|Llamar a este método para buscar la ruta de acceso para una cadena que contiene un tipo de coincidencia de caracteres comodín.|  
|[CPathT::QuoteSpaces](#quotespaces)|Llame a este método para incluir la ruta de acceso entre comillas si contiene espacios en blanco.|  
|[CPathT::RelativePathTo](#relativepathto)|Llame a este método para crear una ruta de acceso relativa de un archivo o carpeta a otra.|  
|[CPathT::RemoveArgs](#removeargs)|Llamar a este método para quitar los argumentos de línea de comandos de la ruta de acceso.|  
|[CPathT::RemoveBackslash](#removebackslash)|Llamar a este método para quitar la barra diagonal inversa al final de la ruta de acceso.|  
|[CPathT::RemoveBlanks](#removeblanks)|Llamar a este método para quitar todos los espacios iniciales y finales de la ruta de acceso.|  
|[CPathT::RemoveExtension](#removeextension)|Llamar a este método para quitar la extensión de archivo de la ruta de acceso, si hay alguno.|  
|[CPathT::RemoveFileSpec](#removefilespec)|Llamar a este método para quitar el nombre de archivo al final y la barra diagonal inversa de la ruta de acceso, si lo tiene.|  
|[CPathT::RenameExtension](#renameextension)|Llamar a este método para reemplazar la extensión de nombre de archivo en la ruta de acceso con una nueva extensión. Si el nombre de archivo no contiene una extensión, la extensión se adjuntarán al final de la cadena.|  
|[CPathT::SkipRoot](#skiproot)|Llame a este método para analizar una ruta de acceso, se omitirá la letra de unidad o partes de ruta de acceso de servidor o recurso compartido UNC.|  
|[CPathT::StripPath](#strippath)|Llamar a este método para quitar la parte de la ruta de acceso de una ruta de acceso completa y nombre de archivo.|  
|[CPathT::StripToRoot](#striptoroot)|Llamar a este método para quitar todas las partes de la ruta de acceso, salvo la información de raíz.|  
|[CPathT::UnquoteSpaces](#unquotespaces)|Llamar a este método para quitar las comillas de principio y al final de una ruta de acceso.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPathT::operator const StringType siguiente](#operator_const_stringtype_amp)|Este operador permite que el objeto se traten como una cadena.|  
|[CPathT::operator CPathT::PCXSTR](#operator_cpatht__pcxstr)|Este operador permite que el objeto se traten como una cadena.|  
|[CPathT::operator StringType siguiente](#operator_stringtype)|Este operador permite que el objeto se traten como una cadena.|  
|[CPathT::operator +=](#operator_add_eq)|Este operador anexa una cadena a la ruta de acceso.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPathT::m_strPath](#m_strpath)|La ruta de acceso.|  
  
## <a name="remarks"></a>Comentarios  
 `CPath`, `CPathA`, y `CPathW` son creaciones de instancias de `CPathT` define del siguiente modo:  
  
 `typedef CPathT< CString > CPath;`  
  
 `typedef CPathT< CStringA > CPathA;`  
  
 `typedef CPathT< CStringW > CPathW;`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlpath.h  
  
##  <a name="addbackslash"></a>CPathT::AddBackslash  
 Llamar a este método para agregar una barra diagonal inversa al final de una cadena para crear la sintaxis correcta para una ruta de acceso. Si la ruta de acceso ya tiene una barra diagonal inversa, no se agregará ninguna barra diagonal inversa.  
  
```
void AddBackslash();
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathAddBackSlash](http://msdn.microsoft.com/library/windows/desktop/bb773561).  
  
##  <a name="addextension"></a>CPathT::AddExtension  
 Llamar a este método para agregar una extensión de archivo a una ruta de acceso.  
  
```
BOOL AddExtension(PCXSTR pszExtension);
```  
  
### <a name="parameters"></a>Parámetros  
 `pszExtension`  
 Para agregar la extensión de archivo.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563).  
  
##  <a name="append"></a>CPathT::Append  
 Llame a este método para anexar una cadena a la ruta de acceso actual.  
  
```
BOOL Append(PCXSTR pszMore);
```  
  
### <a name="parameters"></a>Parámetros  
 `pszMore`  
 Cadena que se va a anexar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565).  
  
##  <a name="buildroot"></a>CPathT::BuildRoot  
 Llame a este método para crear una ruta de acceso raíz de un número de unidad determinada.  
  
```
void BuildRoot(int iDrive);
```  
  
### <a name="parameters"></a>Parámetros  
 *iDrive*  
 El número de unidad (0 es r:, 1 es B: y así sucesivamente).  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567).  
  
##  <a name="canonicalize"></a>CPathT::Canonicalize  
 Llamar a este método para convertir la ruta de acceso en forma canónica.  
  
```
void Canonicalize();
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569).  
  
##  <a name="combine"></a>CPathT::Combine  
 Llame a este método para concatenar una cadena que representa un nombre de directorio y una cadena que representa un nombre de ruta de acceso de archivo en una ruta de acceso.  
  
```
void Combine(PCXSTR pszDir, PCXSTR  pszFile);
```  
  
### <a name="parameters"></a>Parámetros  
 `pszDir`  
 La ruta de acceso de directorio.  
  
 *pszFile*  
 La ruta de acceso de archivo.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathCombine](http://msdn.microsoft.com/library/windows/desktop/bb773571).  
  
##  <a name="commonprefix"></a>CPathT::CommonPrefix  
 Llamar a este método para determinar si la ruta de acceso especificada comparte un prefijo común con la ruta de acceso actual.  
  
```
CPathT<StringType> CommonPrefix(PCXSTR pszOther);
```  
  
### <a name="parameters"></a>Parámetros  
 `pszOther`  
 La ruta de acceso que se compara con la actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el prefijo común.  
  
### <a name="remarks"></a>Comentarios  
 Un prefijo es uno de estos tipos: "C:\\\\",".","..",".. \\\\". Para obtener más información, consulte [PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574).  
  
##  <a name="compactpath"></a>CPathT::CompactPath  
 Llamar a este método para truncar una ruta de acceso de archivo para ajustarse a un ancho de píxel determinado mediante la sustitución de componentes de ruta de acceso con puntos suspensivos.  
  
```
BOOL CompactPath(HDC hDC, UINT nWidth);
```  
  
### <a name="parameters"></a>Parámetros  
 `hDC`  
 El contexto de dispositivo utilizado para las métricas de fuente.  
  
 `nWidth`  
 El ancho, en píxeles, que la cadena se verán obligada a ajustarse.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575).  
  
##  <a name="compactpathex"></a>CPathT::CompactPathEx  
 Llamar a este método para truncar una ruta de acceso de archivo para que se ajusten dentro de un número determinado de caracteres mediante la sustitución de componentes de ruta de acceso con puntos suspensivos.  
  
```
BOOL CompactPathEx(UINT nMaxChars, DWORD dwFlags = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `nMaxChars`  
 El número máximo de caracteres que se van a incluirse en la nueva cadena, incluido el carácter nulo final.  
  
 `dwFlags`  
 Reservado.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578).  
  
##  <a name="cpatht"></a>CPathT::CPathT  
 El constructor.  
  
```
CPathT(PCXSTR pszPath);
CPathT(const CPathT<StringType>& path);
CPathT() throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *pszPath*  
 Puntero a una cadena de ruta de acceso.  
  
 *path*  
 La cadena de ruta de acceso.  
  
##  <a name="fileexists"></a>CPathT::FileExists  
 Llame a este método para comprobar si existe el archivo en este nombre de ruta de acceso.  
  
```
BOOL FileExists() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si el archivo existe, FALSE en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584).  
  
##  <a name="findextension"></a>CPathT::FindExtension  
 Llame a este método para buscar la posición de la extensión de archivo en la ruta de acceso.  
  
```
int FindExtension() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la posición de la "." delante de la extensión. Si no se encuentra ninguna extensión, devuelve -1.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587).  
  
##  <a name="findfilename"></a>CPathT::FindFileName  
 Llame a este método para buscar la posición del nombre de archivo en la ruta de acceso.  
  
```
int FindFileName() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la posición del nombre de archivo. Si no se encuentra ningún nombre de archivo, devuelve -1.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589).  
  
##  <a name="getdrivenumber"></a>CPathT::GetDriveNumber  
 Llamar a este método para buscar la ruta de acceso de una letra de unidad en el intervalo de 'A' a la 'Z' y devolver el número de unidad correspondiente.  
  
```
int GetDriveNumber() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de unidad como un número entero comprendido entre 0 y 25 (correspondiente a 'A' a la 'Z') si la ruta de acceso tiene una letra de unidad, o -1 en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612).  
  
##  <a name="getextension"></a>CPathT::GetExtension  
 Llamar a este método para obtener la extensión de archivo de la ruta de acceso.  
  
```
StringType GetExtension() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la extensión de archivo.  
  
##  <a name="isdirectory"></a>CPathT::IsDirectory  
 Llamar a este método para comprobar si la ruta de acceso es un directorio válido.  
  
```
BOOL IsDirectory() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor distinto de cero (16) si la ruta de acceso es un directorio, `FALSE` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathIsDirectory](http://msdn.microsoft.com/library/windows/desktop/bb773621).  
  
##  <a name="isfilespec"></a>CPathT::IsFileSpec  
 Llamar a este método para buscar una ruta de acceso para cualquier carácter delimitadoras de ruta de acceso (por ejemplo, ':' o '\\'). Si no hay ningún carácter delimitadoras de ruta de acceso está presente, se considera que la ruta de acceso es una ruta de acceso de la especificación de archivo.  
  
```
BOOL IsFileSpec() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si no hay ningún carácter delimitadoras de ruta de acceso dentro de la ruta de acceso, o FALSE si no hay caracteres delimitadoras de ruta de acceso.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627).  
  
##  <a name="isprefix"></a>CPathT::IsPrefix  
 Llamar a este método para determinar si una ruta de acceso contiene un prefijo válido del tipo pasado por `pszPrefix`.  
  
```
BOOL IsPrefix(PCXSTR pszPrefix) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `pszPrefix`  
 El prefijo para el que se va a buscar. Un prefijo es uno de estos tipos: "C:\\\\",".","..",".. \\\\".  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si la ruta de acceso contiene el prefijo o falso en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650).  
  
##  <a name="isrelative"></a>CPathT::IsRelative  
 Llamar a este método para determinar si la ruta de acceso es relativa.  
  
```
BOOL IsRelative() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si la ruta de acceso es relativa, o FALSE si es absoluto.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660).  
  
##  <a name="isroot"></a>CPathT::IsRoot  
 Llamar a este método para determinar si la ruta de acceso es una directorio raíz.  
  
```
BOOL IsRoot() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si la ruta de acceso es una raíz, o FALSE en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674).  
  
##  <a name="issameroot"></a>CPathT::IsSameRoot  
 Llamar a este método para determinar si otra ruta de acceso tiene un componente de raíz común con la ruta de acceso actual.  
  
```
BOOL IsSameRoot(PCXSTR pszOther) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `pszOther`  
 La otra ruta de acceso.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si dos cadenas tienen el mismo componente de raíz, o falso en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687).  
  
##  <a name="isunc"></a>CPathT::IsUNC  
 Llamar a este método para determinar si la ruta de acceso es una ruta de acceso UNC (convención de nomenclatura universal) válida para un servidor y compartir.  
  
```
BOOL IsUNC() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si la ruta de acceso es una ruta de acceso UNC válida y FALSE en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712).  
  
##  <a name="isuncserver"></a>CPathT::IsUNCServer  
 Llamar a este método para determinar si la ruta de acceso es una ruta de acceso UNC (convención de nomenclatura universal) válida para un solo servidor.  
  
```
BOOL IsUNCServer() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si la cadena es una ruta de acceso UNC de un solo servidor (sin nombre de recurso compartido) válido, o FALSE en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722).  
  
##  <a name="isuncservershare"></a>CPathT::IsUNCServerShare  
 Llamar a este método para determinar si la ruta de acceso es una ruta válida de recurso compartido UNC (convención de nomenclatura universal), \\ \  *server*\ *compartir*.  
  
```
BOOL IsUNCServerShare() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si la ruta de acceso tiene el formato \\ \  *server*\ *compartir*, o falso en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723).  
  
##  <a name="m_strpath"></a>CPathT::m_strPath  
 La ruta de acceso.  
  
```
StringType m_strPath;
```  
  
### <a name="remarks"></a>Comentarios  
 `StringType`es el parámetro de plantilla `CPathT`.  
  
##  <a name="makepretty"></a>CPathT::MakePretty  
 Llamar a este método para convertir una ruta de acceso a todos los caracteres en minúsculas para dar una apariencia coherente de la ruta de acceso.  
  
```
BOOL MakePretty();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ha convertido la ruta de acceso, o FALSE en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725).  
  
##  <a name="matchspec"></a>CPathT::MatchSpec  
 Llamar a este método para buscar la ruta de acceso para una cadena que contiene un tipo de coincidencia de caracteres comodín.  
  
```
BOOL MatchSpec(PCXSTR pszSpec) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `pszSpec`  
 Puntero a una cadena terminada en null con el tipo de archivo para el que se va a buscar. Por ejemplo, para comprobar si el archivo en la ruta de acceso actual es un archivo de documento, `pszSpec` debe establecerse en "* .doc".  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si la cadena coincide con, o FALSE en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727).  
  
##  <a name="operator_add_eq"></a>CPathT::operator +=  
 Este operador anexa una cadena a la ruta de acceso.  
  
```
CPathT<StringType>& operator+=(PCXSTR pszMore);
```  
  
### <a name="parameters"></a>Parámetros  
 `pszMore`  
 Cadena que se va a anexar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la ruta de acceso actualizada.  
  
##  <a name="operator_const_stringtype_amp"></a>StringType const CPathT::operator&amp;  
 Este operador permite que el objeto se traten como una cadena.  
  
```
 operatorconst StringType&() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una cadena que representa la ruta de acceso actual administrado por este objeto.  
  
##  <a name="operator_cpatht__pcxstr"></a>CPathT::operator CPathT::PCXSTR  
 Este operador permite que el objeto se traten como una cadena.  
  
```
 operatorPCXSTR() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una cadena que representa la ruta de acceso actual administrado por este objeto.  
  
##  <a name="operator_stringtype__amp"></a>CPathT::operator StringType&amp;  
 Este operador permite que el objeto se traten como una cadena.  
  
```
 operatorStringType&() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una cadena que representa la ruta de acceso actual administrado por este objeto.  
  
##  <a name="pcxstr"></a>CPathT::PCXSTR  
 Un tipo de cadena constante.  
  
```
typedef StringType::PCXSTR PCXSTR;
```  
  
### <a name="remarks"></a>Comentarios  
 `StringType`es el parámetro de plantilla `CPathT`.  
  
##  <a name="pxstr"></a>CPathT::PXSTR  
 Un tipo de cadena.  
  
```
typedef StringType::PXSTR PXSTR;
```  
  
### <a name="remarks"></a>Comentarios  
 `StringType`es el parámetro de plantilla `CPathT`.  
  
##  <a name="quotespaces"></a>CPathT::QuoteSpaces  
 Llame a este método para incluir la ruta de acceso entre comillas si contiene espacios en blanco.  
  
```
void QuoteSpaces();
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739).  
  
##  <a name="relativepathto"></a>CPathT::RelativePathTo  
 Llame a este método para crear una ruta de acceso relativa de un archivo o carpeta a otra.  
  
```
BOOL RelativePathTo(
    PCXSTR pszFrom,
    DWORD dwAttrFrom,
    PCXSTR pszTo,
    DWORD dwAttrTo);
```  
  
### <a name="parameters"></a>Parámetros  
 `pszFrom`  
 El inicio de la ruta de acceso relativa.  
  
 *dwAttrFrom*  
 Los atributos del archivo de `pszFrom`. Si este valor contiene FILE_ATTRIBUTE_DIRECTORY, `pszFrom` considera que ser un directorio; en caso contrario, `pszFrom` se supone que es un archivo.  
  
 `pszTo`  
 El punto final de la ruta de acceso relativa.  
  
 *dwAttrTo*  
 Los atributos del archivo de `pszTo`. Si este valor contiene FILE_ATTRIBUTE_DIRECTORY, `pszTo` considera que ser un directorio; en caso contrario, `pszTo` se supone que es un archivo.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740).  
  
##  <a name="removeargs"></a>CPathT::RemoveArgs  
 Llamar a este método para quitar los argumentos de línea de comandos de la ruta de acceso.  
  
```
void RemoveArgs();
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742).  
  
##  <a name="removebackslash"></a>CPathT::RemoveBackslash  
 Llamar a este método para quitar la barra diagonal inversa al final de la ruta de acceso.  
  
```
void RemoveBackslash();
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743).  
  
##  <a name="removeblanks"></a>CPathT::RemoveBlanks  
 Llamar a este método para quitar todos los espacios iniciales y finales de la ruta de acceso.  
  
```
void RemoveBlanks();
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745).  
  
##  <a name="removeextension"></a>CPathT::RemoveExtension  
 Llamar a este método para quitar la extensión de archivo de la ruta de acceso, si hay alguno.  
  
```
void RemoveExtension();
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746).  
  
##  <a name="removefilespec"></a>CPathT::RemoveFileSpec  
 Llamar a este método para quitar el nombre de archivo al final y la barra diagonal inversa de la ruta de acceso, si lo tiene.  
  
```
BOOL RemoveFileSpec();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748).  
  
##  <a name="renameextension"></a>CPathT::RenameExtension  
 Llamar a este método para reemplazar la extensión de nombre de archivo en la ruta de acceso con una nueva extensión. Si el nombre de archivo no contiene una extensión, la extensión se adjuntarán al final de la ruta de acceso.  
  
```
BOOL RenameExtension(PCXSTR pszExtension);
```  
  
### <a name="parameters"></a>Parámetros  
 `pszExtension`  
 La nueva extensión de nombre de archivo, precedido por un "." caracteres.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749).  
  
##  <a name="skiproot"></a>CPathT::SkipRoot  
 Llame a este método para analizar una ruta de acceso, se omitirá la letra de unidad o partes de ruta de acceso de servidor o recurso compartido UNC (convención de nomenclatura universal).  
  
```
int SkipRoot() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la posición del principio de la subruta de acceso que sigue a la raíz (letra de unidad o UNC/recurso compartido de servidor).  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754).  
  
##  <a name="strippath"></a>CPathT::StripPath  
 Llamar a este método para quitar la parte de la ruta de acceso de una ruta de acceso completa y nombre de archivo.  
  
```
void StripPath();
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756).  
  
##  <a name="striptoroot"></a>CPathT::StripToRoot  
 Llamar a este método para quitar todas las partes de la ruta de acceso, salvo la información de raíz.  
  
```
BOOL StripToRoot();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si una letra de unidad válido se encontró en la ruta de acceso, o FALSE en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757).  
  
##  <a name="unquotespaces"></a>CPathT::UnquoteSpaces  
 Llamar a este método para quitar las comillas de principio y al final de una ruta de acceso.  
  
```
void UnquoteSpaces();
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763).  
  
##  <a name="xchar"></a>CPathT::XCHAR  
 Tipo de carácter.  
  
```
typedef StringType::XCHAR XCHAR;
```  
  
### <a name="remarks"></a>Comentarios  
 `StringType`es el parámetro de plantilla `CPathT`.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../atl/reference/atl-classes.md)   
 [CStringT (clase)](../../atl-mfc-shared/reference/cstringt-class.md)
