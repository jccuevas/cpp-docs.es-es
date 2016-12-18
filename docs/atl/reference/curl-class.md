---
title: "CUrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CUrl"
  - "CUrl"
  - "ATL::CUrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CUrl class"
ms.assetid: b3894d34-47b9-4961-9719-4197153793da
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CUrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase representa una dirección URL.  Permite manipular cada elemento de la dirección URL independientemente de los demás si analiza una cadena existente de la dirección URL o compila una cadena desde el principio.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CUrl  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CUrl::CUrl](../Topic/CUrl::CUrl.md)|el constructor.|  
|[CUrl::~CUrl](../Topic/CUrl::~CUrl.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CUrl::Canonicalize](../Topic/CUrl::Canonicalize.md)|Llame a este método para convertir la cadena de dirección URL a la forma canónica.|  
|[CUrl::Clear](../Topic/CUrl::Clear.md)|Llame a este método para borrar todos los campos de dirección URL.|  
|[CUrl::CrackUrl](../Topic/CUrl::CrackUrl.md)|Llame a este método para descodificar y analizar la dirección URL.|  
|[CUrl::CreateUrl](../Topic/CUrl::CreateUrl.md)|Llame a este método para crear la dirección URL.|  
|[CUrl::GetExtraInfo](../Topic/CUrl::GetExtraInfo.md)|¿Llame a este método para obtener información adicional \(por ejemplo?*texto* o \#text\) de la dirección URL.|  
|[CUrl::GetExtraInfoLength](../Topic/CUrl::GetExtraInfoLength.md)|¿Llame a este método para obtener la longitud de información adicional \(por ejemplo?*texto* o \#text\) a la recuperación de la dirección URL.|  
|[CUrl::GetHostName](../Topic/CUrl::GetHostName.md)|Llame a este método para obtener el nombre de host de la dirección URL.|  
|[CUrl::GetHostNameLength](../Topic/CUrl::GetHostNameLength.md)|Llame a este método para obtener la longitud del nombre de host.|  
|[CUrl::GetPassword](../Topic/CUrl::GetPassword.md)|Llame a este método para obtener la contraseña de la dirección URL.|  
|[CUrl::GetPasswordLength](../Topic/CUrl::GetPasswordLength.md)|Llame a este método para obtener la longitud de la contraseña.|  
|[CUrl::GetPortNumber](../Topic/CUrl::GetPortNumber.md)|Llame a este método para obtener el número de puerto en términos de ATL\_URL\_PORT.|  
|[CUrl::GetScheme](../Topic/CUrl::GetScheme.md)|Llame a este método para obtener el esquema de la dirección URL.|  
|[CUrl::GetSchemeName](../Topic/CUrl::GetSchemeName.md)|Llame a este método para obtener el nombre de la combinación de la dirección URL.|  
|[CUrl::GetSchemeNameLength](../Topic/CUrl::GetSchemeNameLength.md)|Llame a este método para obtener la longitud del nombre de combinación de la dirección URL.|  
|[CUrl::GetUrlLength](../Topic/CUrl::GetUrlLength.md)|Llame a este método para obtener la longitud de la dirección URL.|  
|[CUrl::GetUrlPath](../Topic/CUrl::GetUrlPath.md)|Llame a este método para obtener la ruta de la dirección URL.|  
|[CUrl::GetUrlPathLength](../Topic/CUrl::GetUrlPathLength.md)|Llame a este método para obtener la longitud de la ruta de acceso de dirección URL.|  
|[CUrl::GetUserName](../Topic/CUrl::GetUserName.md)|Llame a este método para obtener el nombre de usuario de la dirección URL.|  
|[CUrl::GetUserNameLength](../Topic/CUrl::GetUserNameLength.md)|Llame a este método para obtener la longitud del nombre de usuario.|  
|[CUrl::SetExtraInfo](../Topic/CUrl::SetExtraInfo.md)|¿Llame a este método para establecer información adicional \(por ejemplo?*texto* o \#text\) de la dirección URL.|  
|[CUrl::SetHostName](../Topic/CUrl::SetHostName.md)|Llame a este método para establecer el nombre de host.|  
|[CUrl::SetPassword](../Topic/CUrl::SetPassword.md)|Llame a este método para establecer la contraseña.|  
|[CUrl::SetPortNumber](../Topic/CUrl::SetPortNumber.md)|Llame a este método para establecer el número de puerto en términos de ATL\_URL\_PORT.|  
|[CUrl::SetScheme](../Topic/CUrl::SetScheme.md)|Llame a este método para establecer el esquema de la dirección URL.|  
|[CUrl::SetSchemeName](../Topic/CUrl::SetSchemeName.md)|Llame a este método para establecer el nombre de combinación de la dirección URL.|  
|[CUrl::SetUrlPath](../Topic/CUrl::SetUrlPath.md)|Llame a este método para establecer la ruta de acceso de la dirección URL.|  
|[CUrl::SetUserName](../Topic/CUrl::SetUserName.md)|Llame a este método para establecer el nombre de usuario.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CUrl::operator \=](../Topic/CUrl::operator%20=.md)|Asigna el objeto especificado de `CUrl` al objeto actual de `CUrl` .|  
  
## Comentarios  
 `CUrl` le permiten manipular los campos de una dirección URL, como la ruta o el número de puerto.  `CUrl` entiende direcciones URL con el formato siguiente:  
  
 \<esquema\> : \/ \<nombre de usuario\> : \<contraseña\> @ \<Nombre del host\> : \<número de puerto\> \/ \<UrlPath\>  \<ExtraInfo\>  
  
 \(Algunos campos son opcionales\). Por ejemplo, considere esta dirección URL:  
  
 http:\/\/someone:secret@www.microsoft.com:80\/visualc\/stuff.htm\#contents  
  
 [rizo:: CrackUrl](../Topic/CUrl::CrackUrl.md) lo analiza como sigue:  
  
-   esquema: “http” o [ATL\_URL\_SCHEME\_HTTP](../Topic/ATL_URL_SCHEME.md)  
  
-   nombre de usuario: “alguien”  
  
-   contraseña: “secreto”  
  
-   Nombre de host: “www.microsoft.com”  
  
-   número de puerto: 80  
  
-   UrlPath: “visualc\/stuff.htm”  
  
-   ExtraInfo: “\#contents”  
  
 Para manipular el campo de UrlPath \(por ejemplo\), se debería utilizar [GetUrlPath](../Topic/CUrl::GetUrlPath.md), [GetUrlPathLength](../Topic/CUrl::GetUrlPathLength.md), y [SetUrlPath](../Topic/CUrl::SetUrlPath.md).  Utilice [CreateUrl](../Topic/CUrl::CreateUrl.md) para crear la cadena completa de la dirección URL.  
  
## Requisitos  
 **encabezado:** atlutil.h  
  
## Vea también  
 [Clases](../../atl/reference/atl-classes.md)