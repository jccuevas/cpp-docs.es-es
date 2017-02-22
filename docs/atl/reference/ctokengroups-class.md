---
title: "CTokenGroups Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CTokenGroups"
  - "ATL.CTokenGroups"
  - "CTokenGroups"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTokenGroups class"
ms.assetid: 2ab08076-4b08-4487-bc70-ec6dee304190
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CTokenGroups Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase es un contenedor para la estructura de **TOKEN\_GROUPS** .  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CTokenGroups  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTokenGroups::CTokenGroups](../Topic/CTokenGroups::CTokenGroups.md)|el constructor.|  
|[CTokenGroups::~CTokenGroups](../Topic/CTokenGroups::~CTokenGroups.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTokenGroups::Add](../Topic/CTokenGroups::Add.md)|Agrega `CSid` o una estructura existente de **TOKEN\_GROUPS** al objeto de `CTokenGroups` .|  
|[CTokenGroups::Delete](../Topic/CTokenGroups::Delete.md)|Elimina `CSid` y sus atributos asociados del objeto de `CTokenGroups` .|  
|[CTokenGroups::DeleteAll](../Topic/CTokenGroups::DeleteAll.md)|Elimina todos los objetos de `CSid` y sus atributos asociados del objeto de `CTokenGroups` .|  
|[CTokenGroups::GetCount](../Topic/CTokenGroups::GetCount.md)|Devuelve el número de objetos de `CSid` y atributos asociados contenido en el objeto de **CTokenGroups** .|  
|[CTokenGroups::GetLength](../Topic/CTokenGroups::GetLength.md)|Devuelve el tamaño del objeto de `CTokenGroups` .|  
|[CTokenGroups::GetPTOKEN\_GROUPS](../Topic/CTokenGroups::GetPTOKEN_GROUPS.md)|recupera un puntero a la estructura de **TOKEN\_GROUPS** .|  
|[CTokenGroups::GetSidsAndAttributes](../Topic/CTokenGroups::GetSidsAndAttributes.md)|Recupera los objetos y los atributos de `CSid` que pertenecen al objeto de `CTokenGroups` .|  
|[CTokenGroups::LookupSid](../Topic/CTokenGroups::LookupSid.md)|Recupera los atributos asociados con un objeto de `CSid` .|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTokenGroups::operator const TOKEN\_GROUPS \*](../Topic/CTokenGroups::operator%20const%20TOKEN_GROUPS%20*.md)|Convierte el objeto de `CTokenGroups` a un puntero a la estructura de **TOKEN\_GROUPS** .|  
|[CTokenGroups::operator \=](../Topic/CTokenGroups::operator%20=.md)|Operador de asignación.|  
  
## Comentarios  
 [token de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374909) es un objeto que describe el contexto de seguridad de un proceso o de un subproceso y se asigna a cada usuario registrado en un sistema de Windows NT o Windows 2000.  
  
 La clase de **CTokenGroups** es un contenedor para la estructura de [TOKEN\_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) , que contiene información sobre los identificadores de seguridad \(SIDs\) de grupo en un token de acceso.  
  
 Para obtener una introducción al modelo de control de acceso de Windows, vea [control de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374860) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## Requisitos  
 **encabezado:** atlsecurity.h  
  
## Vea también  
 [Ejemplo de seguridad](../../top/visual-cpp-samples.md)   
 [CSid Class](../../atl/reference/csid-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Security Global Functions](../../atl/reference/security-global-functions.md)