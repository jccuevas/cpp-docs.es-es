---
title: "CPathT Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CPathT"
  - "CPathT"
  - "ATL::CPathT<StringType>"
  - "ATL::CPathT"
  - "ATL.CPathT<StringType>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPathT class"
ms.assetid: eba4137d-1fd2-4b44-a2e1-0944db64df3c
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CPathT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase representa una ruta.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template< typename   
      StringType  
      >   
class CPathT  
```  
  
#### Parámetros  
 `StringType`  
 La clase de cadena de ATL\/MFC a utilizar para la ruta \(vea [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)\).  
  
## Members  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPathT::PCXSTR](../Topic/CPathT::PCXSTR.md)|Un tipo de cadena constante.|  
|[CPathT::PXSTR](../Topic/CPathT::PXSTR.md)|Un tipo de cadena.|  
|[CPathT::XCHAR](../Topic/CPathT::XCHAR.md)|Un tipo de caracteres.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPathT::CPathT](../Topic/CPathT::CPathT.md)|El constructor de la ruta.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPathT::AddBackslash](../Topic/CPathT::AddBackslash.md)|Llame a este método para agregar una barra diagonal inversa al final de una cadena para crear la sintaxis correcta para una ruta.|  
|[CPathT::AddExtension](../Topic/CPathT::AddExtension.md)|Llame a este método para agregar una extensión de archivo a una ruta.|  
|[CPathT::Append](../Topic/CPathT::Append.md)|Llame a este método para anexar una cadena en la ruta actual.|  
|[CPathT::BuildRoot](../Topic/CPathT::BuildRoot.md)|Llame a este método para crear una ruta de acceso raíz de un número de unidad especificado.|  
|[CPathT::Canonicalize](../Topic/CPathT::Canonicalize.md)|Llame a este método para convertir la ruta a la forma canónica.|  
|[CPathT::Combine](../Topic/CPathT::Combine.md)|Llame a este método para concatenar una cadena que representa un nombre de directorio y una cadena que representa un nombre de ruta de acceso en una ruta.|  
|[CPathT::CommonPrefix](../Topic/CPathT::CommonPrefix.md)|Llame a este método para determinar si la ruta de acceso especificada comparte un prefijo común con la ruta actual.|  
|[CPathT::CompactPath](../Topic/CPathT::CompactPath.md)|Llame a este método para truncar una ruta de acceso para ajustarse a un ancho especificado de píxel reemplazando los componentes de la ruta con las elipses.|  
|[CPathT::CompactPathEx](../Topic/CPathT::CompactPathEx.md)|Llame a este método para truncar una ruta de acceso para ajustarse a un número de caracteres especificado reemplazando los componentes de la ruta con las elipses.|  
|[CPathT::FileExists](../Topic/CPathT::FileExists.md)|Llame a este método para comprobar si existe el archivo en este nombre de ruta.|  
|[CPathT::FindExtension](../Topic/CPathT::FindExtension.md)|Llame a este método para buscar la posición de la extensión de archivo dentro de la ruta.|  
|[CPathT::FindFileName](../Topic/CPathT::FindFileName.md)|Llame a este método para buscar la posición del nombre de archivo en la ruta.|  
|[CPathT::GetDriveNumber](../Topic/CPathT::GetDriveNumber.md)|Llame a este método para buscar la ruta para una letra de unidad dentro del intervalo de “A” a la “z” y devolver el número de unidad correspondiente.|  
|[CPathT::GetExtension](../Topic/CPathT::GetExtension.md)|Llame a este método para obtener la extensión de archivo de la ruta.|  
|[CPathT::IsDirectory](../Topic/CPathT::IsDirectory.md)|Llame a este método para comprobar si la ruta de acceso es un directorio válido.|  
|[CPathT::IsFileSpec](../Topic/CPathT::IsFileSpec.md)|Llame a este método para buscar una ruta por cualquier carácter de ruta\-delimitación \(por ejemplo, “: ” o “\\ "\).  Si no hay caracteres de ruta\-delimitación presentes, la ruta de acceso se considera una ruta de acceso de la especificación del archivo.|  
|[CPathT::IsPrefix](../Topic/CPathT::IsPrefix.md)|Llame a este método para determinar si una ruta de acceso contiene un prefijo válido del tipo pasado por `pszPrefix`.|  
|[CPathT::IsRelative](../Topic/CPathT::IsRelative.md)|Llame a este método para determinar si la ruta de acceso es relativa.|  
|[CPathT::IsRoot](../Topic/CPathT::IsRoot.md)|Llame a este método para determinar si la ruta de acceso es una raíz del directorio.|  
|[CPathT::IsSameRoot](../Topic/CPathT::IsSameRoot.md)|Llame a este método para determinar si otra ruta tiene un componente raíz común con la ruta actual.|  
|[CPathT::IsUNC](../Topic/CPathT::IsUNC.md)|Llame a este método para determinar si la ruta de acceso es una ruta de acceso completa de UNC \(convención de nomenclatura universal\) para un servidor y una acción.|  
|[CPathT::IsUNCServer](../Topic/CPathT::IsUNCServer.md)|Llame a este método para determinar si la ruta de acceso es una ruta de acceso completa de UNC \(convención de nomenclatura universal\) para un servidor sólo.|  
|[CPathT::IsUNCServerShare](../Topic/CPathT::IsUNCServerShare.md)|Llame a este método para determinar si la ruta de acceso es una ruta de acceso completa del recurso compartido UNC \(convención de nomenclatura universal\), \\ \\*servidor*\\*acción*.|  
|[CPathT::MakePretty](../Topic/CPathT::MakePretty.md)|Llame a este método para convertir una ruta de acceso a todos los caracteres en minúscula para dar a la ruta un aspecto coherente.|  
|[CPathT::MatchSpec](../Topic/CPathT::MatchSpec.md)|Llame a este método para buscar la ruta para una cadena que contiene un tipo de carácter comodín.|  
|[CPathT::QuoteSpaces](../Topic/CPathT::QuoteSpaces.md)|Llame a este método para agregar la ruta de acceso entre comillas si contiene cualquier espacio.|  
|[CPathT::RelativePathTo](../Topic/CPathT::RelativePathTo.md)|Llame a este método para crear una ruta de acceso relativa desde un archivo o carpeta a otra.|  
|[CPathT::RemoveArgs](../Topic/CPathT::RemoveArgs.md)|Llame a este método para quitar los argumentos de la línea de comandos de la ruta.|  
|[CPathT::RemoveBackslash](../Topic/CPathT::RemoveBackslash.md)|Llame a este método para quitar la barra diagonal inversa final de la ruta.|  
|[CPathT::RemoveBlanks](../Topic/CPathT::RemoveBlanks.md)|Llame a este método para quitar todos los espacios iniciales y finales de la ruta.|  
|[CPathT::RemoveExtension](../Topic/CPathT::RemoveExtension.md)|Llame a este método para quitar la extensión de archivo de la ruta, si la hay.|  
|[CPathT::RemoveFileSpec](../Topic/CPathT::RemoveFileSpec.md)|Llame a este método para quitar el nombre de archivo y la barra diagonal inversa finales de la ruta, si los hay.|  
|[CPathT::RenameExtension](../Topic/CPathT::RenameExtension.md)|Llame a este método para reemplazar la extensión de nombre de archivo en la ruta de acceso con una nueva extensión.  Si el nombre de archivo no contiene una extensión de, la extensión se adjunta al final de la cadena.|  
|[CPathT::SkipRoot](../Topic/CPathT::SkipRoot.md)|Llame a este método para analizar una ruta, omitiendo la letra de unidad o el servidor UNC o la acción de las partes de la ruta.|  
|[CPathT::StripPath](../Topic/CPathT::StripPath.md)|Llame a este método para quitar la parte de la ruta de una ruta de acceso completa y un nombre de archivo.|  
|[CPathT::StripToRoot](../Topic/CPathT::StripToRoot.md)|Llame a este método para quitar todas las partes de la ruta salvo la información de la raíz.|  
|[CPathT::UnquoteSpaces](../Topic/CPathT::UnquoteSpaces.md)|Llame a este método para quitar comillas desde el principio y el final de una ruta.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPathT::operator const StringType &](../Topic/CPathT::operator%20const%20StringType%20&.md)|Este operador permite que el objeto sea tratada como una cadena.|  
|[CPathT::operator CPathT::PCXSTR](../Topic/CPathT::operator%20CPathT::PCXSTR.md)|Este operador permite que el objeto sea tratada como una cadena.|  
|[CPathT::operator StringType &](../Topic/CPathT::operator%20StringType%20&.md)|Este operador permite que el objeto sea tratada como una cadena.|  
|[CPathT::operator \+\=](../Topic/CPathT::operator%20+=.md)|Este operador anexa una cadena en la ruta.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPathT::m\_strPath](../Topic/CPathT::m_strPath.md)|la ruta.|  
  
## Comentarios  
 `CPath`, `CPathA`, y `CPathW` son instancias de `CPathT` definido como sigue:  
  
 `typedef CPathT< CString > CPath;`  
  
 `typedef CPathT< CStringA > CPathA;`  
  
 `typedef CPathT< CStringW > CPathW;`  
  
## Requisitos  
 **encabezado:** atlpath.h  
  
## Vea también  
 [Clases](../../atl/reference/atl-classes.md)   
 [CStringT Class](../../atl-mfc-shared/reference/cstringt-class.md)