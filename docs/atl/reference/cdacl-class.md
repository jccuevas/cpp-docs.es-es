---
title: "CDacl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CDacl"
  - "CDacl"
  - "ATL.CDacl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDacl class"
ms.assetid: 2dc76616-6362-4967-b6cf-e2d39ca37ddd
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDacl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase es un contenedor para una estructura DACL \(lista de control de acceso discrecional \(DACL\)\).  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CDacl : public CAcl  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDacl::CDacl](../Topic/CDacl::CDacl.md)|el constructor.|  
|[CDacl::~CDacl](../Topic/CDacl::~CDacl.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDacl::AddAllowedAce](../Topic/CDacl::AddAllowedAce.md)|Agrega un ACE permitido \(entrada de control de acceso\) al objeto de `CDacl` .|  
|[CDacl::AddDeniedAce](../Topic/CDacl::AddDeniedAce.md)|Agrega un ACE denegado al objeto de `CDacl` .|  
|[CDacl::GetAceCount](../Topic/CDacl::GetAceCount.md)|Devuelve el número de ACE \(entradas de control de acceso\) en el objeto de `CDacl` .|  
|[CDacl::RemoveAce](../Topic/CDacl::RemoveAce.md)|Quita un ACE específico \(entrada de control de acceso\) del objeto de `CDacl` .|  
|[CDacl::RemoveAllAces](../Topic/CDacl::RemoveAllAces.md)|Quita todos los ACE contenido en el objeto de `CDacl` .|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDacl::operator \=](../Topic/CDacl::operator%20=.md)|Operador de asignación.|  
  
## Comentarios  
 El descriptor de seguridad de un objeto puede contener una DACL.  Una DACL contiene cero o más ACE \(entradas de control de acceso\) que identifica los usuarios y grupos que pueden tener acceso al objeto.  Si una DACL está vacía \(es decir, contiene ACE cero\), no se concede ningún acceso explícitamente, por lo que el acceso se deniega implícitamente.  Sin embargo, si el descriptor de seguridad de un objeto no tiene una DACL, se anula el objeto y todo el mundo ha completado el acceso.  
  
 Para recuperar una DACL de un objeto, debe ser el propietario del objeto o tener acceso de READ\_CONTROL al objeto.  Para cambiar una DACL de un objeto, debe tener acceso de WRITE\_DAC al objeto.  
  
 Utilice los métodos de la clase proporcionados para crear, agregar, quitar, eliminar ACE del objeto de `CDacl` .  Vea también [AtlGetDacl](../Topic/AtlGetDacl.md) y [AtlSetDacl](../Topic/AtlSetDacl.md).  
  
 Para obtener una introducción al modelo de control de acceso de Windows, vea [control de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374860) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## Jerarquía de herencia  
 [CAcl](../../atl/reference/cacl-class.md)  
  
 `CDacl`  
  
## Requisitos  
 **encabezado:** atlsecurity.h  
  
## Vea también  
 [Ejemplo de seguridad](../../top/visual-cpp-samples.md)   
 [CAcl Class](../../atl/reference/cacl-class.md)   
 [ACLs](http://msdn.microsoft.com/library/windows/desktop/aa374872)   
 [ACEs](http://msdn.microsoft.com/library/windows/desktop/aa374868)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Security Global Functions](../../atl/reference/security-global-functions.md)