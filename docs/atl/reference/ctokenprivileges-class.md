---
title: "CTokenPrivileges Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CTokenPrivileges"
  - "CTokenPrivileges"
  - "ATL.CTokenPrivileges"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTokenPrivileges class"
ms.assetid: 89590105-f001-4014-870d-142926091231
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CTokenPrivileges Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase es un contenedor para la estructura de **TOKEN\_PRIVILEGES** .  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CTokenPrivileges  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTokenPrivileges::CTokenPrivileges](../Topic/CTokenPrivileges::CTokenPrivileges.md)|el constructor.|  
|[CTokenPrivileges::~CTokenPrivileges](../Topic/CTokenPrivileges::~CTokenPrivileges.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTokenPrivileges::Add](../Topic/CTokenPrivileges::Add.md)|Agregue uno o más privilegios al objeto de `CTokenPrivileges` .|  
|[CTokenPrivileges::Delete](../Topic/CTokenPrivileges::Delete.md)|Elimina un privilegio del objeto de `CTokenPrivileges` .|  
|[CTokenPrivileges::DeleteAll](../Topic/CTokenPrivileges::DeleteAll.md)|Elimina todos los privilegios del objeto de `CTokenPrivileges` .|  
|[CTokenPrivileges::GetCount](../Topic/CTokenPrivileges::GetCount.md)|Devuelve el número de entradas de privilegios en el objeto de `CTokenPrivileges` .|  
|[CTokenPrivileges::GetDisplayNames](../Topic/CTokenPrivileges::GetDisplayNames.md)|Recupera los nombres para mostrar de privilegios contenido en el objeto de `CTokenPrivileges` .|  
|[CTokenPrivileges::GetLength](../Topic/CTokenPrivileges::GetLength.md)|Devuelve el tamaño de búfer en los bytes necesarios conserve la estructura de **TOKEN\_PRIVILEGES** representada por el objeto de `CTokenPrivileges` .|  
|[CTokenPrivileges::GetLuidsAndAttributes](../Topic/CTokenPrivileges::GetLuidsAndAttributes.md)|Recupera localmente identificadores únicos \(LUIDs\) y el atributo marca del objeto de `CTokenPrivileges` .|  
|[CTokenPrivileges::GetNamesAndAttributes](../Topic/CTokenPrivileges::GetNamesAndAttributes.md)|Recupera los nombres de privilegios y el atributo marca del objeto de `CTokenPrivileges` .|  
|[CTokenPrivileges::GetPTOKEN\_PRIVILEGES](../Topic/CTokenPrivileges::GetPTOKEN_PRIVILEGES.md)|devuelve un puntero a la estructura de **TOKEN\_PRIVILEGES** .|  
|[CTokenPrivileges::LookupPrivilege](../Topic/CTokenPrivileges::LookupPrivilege.md)|Recupera el atributo asociado con un nombre concreto de privilegios.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTokenPrivileges::operator const TOKEN\_PRIVILEGES \*](../Topic/CTokenPrivileges::operator%20const%20TOKEN_PRIVILEGES%20*.md)|Convierte un valor en un puntero a la estructura de **TOKEN\_PRIVILEGES** .|  
|[CTokenPrivileges::operator \=](../Topic/CTokenPrivileges::operator%20=.md)|Operador de asignación.|  
  
## Comentarios  
 [token de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374909) es un objeto que describe el contexto de seguridad de un proceso o de un subproceso y se asigna a cada usuario registrado en un sistema de Windows NT o Windows 2000.  
  
 El token de acceso se utiliza para describir los distintos privilegios de seguridad concedidos a cada usuario.  Un privilegio está compuesta de un número 64 bits denominado localmente un identificador único \([LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)\) y un por cadena.  
  
 la clase de `CTokenPrivileges` es un contenedor para la estructura de [TOKEN\_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) y contiene 0 o más privilegios.  Los privilegios se pueden agregar, eliminar, o ver utilizando los métodos proporcionados de la clase.  
  
 Para obtener una introducción al modelo de control de acceso de Windows, vea [control de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374860) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## Requisitos  
 **encabezado:** atlsecurity.h  
  
## Vea también  
 [Ejemplo de seguridad](../../top/visual-cpp-samples.md)   
 [TOKEN\_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)   
 [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)   
 [LUID\_AND\_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379263)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Security Global Functions](../../atl/reference/security-global-functions.md)