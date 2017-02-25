---
title: "CSid Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSid"
  - "ATL::CSid"
  - "ATL.CSid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSid class"
ms.assetid: be58b7ca-5958-49c3-a833-ca341aaaf753
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CSid Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase es un contenedor para una estructura de `SID` \(identificador de seguridad\).  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CSid  
  
```  
  
## Members  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSid::CSidArray](../Topic/CSid::CSidArray.md)|Matriz de objetos `CSid`.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSid::CSid](../Topic/CSid::CSid.md)|el constructor.|  
|[CSid::~CSid](../Topic/CSid::~CSid.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSid::AccountName](../Topic/CSid::AccountName.md)|Devuelve el nombre de la cuenta asociada al objeto de `CSid` .|  
|[CSid::Domain](../Topic/CSid::Domain.md)|Devuelve el nombre de dominio asociado con el objeto de `CSid` .|  
|[CSid::EqualPrefix](../Topic/CSid::EqualPrefix.md)|Prueba los prefijos de `SID` \(identificador de seguridad\) para comprobar la igualdad.|  
|[CSid::GetLength](../Topic/CSid::GetLength.md)|Devuelve la longitud del objeto de `CSid` .|  
|[CSid::GetPSID](../Topic/CSid::GetPSID.md)|devuelve un puntero a una estructura de `SID` .|  
|[CSid::GetPSID\_IDENTIFIER\_AUTHORITY](../Topic/CSid::GetPSID_IDENTIFIER_AUTHORITY.md)|devuelve un puntero a la estructura de **SID\_IDENTIFIER\_AUTHORITY** .|  
|[CSid::GetSubAuthority](../Topic/CSid::GetSubAuthority.md)|devuelve un subauthority especificado en una estructura de **SID** .|  
|[CSid::GetSubAuthorityCount](../Topic/CSid::GetSubAuthorityCount.md)|Devuelve el número de subauthority.|  
|[CSid::IsValid](../Topic/CSid::IsValid.md)|prueba el objeto de `CSid` para la validez.|  
|[CSid::LoadAccount](../Topic/CSid::LoadAccount.md)|actualiza el objeto de `CSid` dado el nombre de cuenta y el dominio, o una estructura existente de `SID` .|  
|[CSid::Sid](../Topic/CSid::Sid.md)|Devuelve la cadena de identificador.|  
|[CSid::SidNameUse](../Topic/CSid::SidNameUse.md)|Devuelve una descripción del estado del objeto de `CSid` .|  
  
### Operadores  
  
|||  
|-|-|  
|[operador \=](../Topic/CSid::operator%20=.md)|Operador de asignación.|  
|[const SID de operador \*](../Topic/CSid::operator%20const%20SID%20*.md)|Convierte un objeto de `CSid` a un puntero a una estructura de `SID` .|  
  
### operadores globales  
  
|||  
|-|-|  
|[operator \=\=](../Topic/CSid::operator%20==.md)|pruebas dos objetos de descriptor de seguridad para la igualdad|  
|[el operador\! \=](../Topic/CSid::operator%20!=.md)|pruebas dos objetos de descriptor de seguridad para la desigualdad|  
|[operador \<](../Topic/CSid::operator%20%3C.md)|compara el valor relativo de dos objetos de descriptor de seguridad.|  
|[operador \>](../Topic/CSid::operator%20%3E.md)|compara el valor relativo de dos objetos de descriptor de seguridad.|  
|[operador \<\=](../Topic/CSid::operator%20%3C=.md)|compara el valor relativo de dos objetos de descriptor de seguridad.|  
|[operador \>\=](../Topic/CSid::operator%20%3E=.md)|compara el valor relativo de dos objetos de descriptor de seguridad.|  
  
## Comentarios  
 La estructura de `SID` es una estructura de longitud variable utilizada para identificar usuarios o grupos.  
  
 Las aplicaciones no deben modificar la estructura de `SID` directamente, sino utilizan métodos proporcionados en esta clase contenedora.  Vea también [AtlGetOwnerSid](../Topic/AtlGetOwnerSid.md), [AtlSetGroupSid](../Topic/AtlSetGroupSid.md), [AtlGetGroupSid](../Topic/AtlGetGroupSid.md), y [AtlSetOwnerSid](../Topic/AtlSetOwnerSid.md).  
  
 Para obtener una introducción al modelo de control de acceso de Windows, vea [control de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374860) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## Requisitos  
 **encabezado:** atlsecurity.h  
  
## Vea también  
 [Ejemplo de seguridad](../../top/visual-cpp-samples.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Security Global Functions](../../atl/reference/security-global-functions.md)   
 [Operators Alphabetical Reference](../../atl/reference/atl-operators.md)