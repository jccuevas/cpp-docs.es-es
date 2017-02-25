---
title: "CSacl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CSacl"
  - "ATL::CSacl"
  - "CSacl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSacl class"
ms.assetid: 8624889b-aebc-4183-9d29-a20f07837f05
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CSacl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase es un contenedor para una estructura SACL \(lista de control de acceso del sistema\).  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CSacl : public CAcl  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSacl::CSacl](../Topic/CSacl::CSacl.md)|el constructor.|  
|[CSacl::~CSacl](../Topic/CSacl::~CSacl.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSacl::AddAuditAce](../Topic/CSacl::AddAuditAce.md)|Agrega una entrada de control de acceso de \(ACE\) la auditoría al objeto de `CSacl` .|  
|[CSacl::GetAceCount](../Topic/CSacl::GetAceCount.md)|devuelve el número de entradas de control de acceso \(ACEs\) en el objeto de `CSacl` .|  
|[CSacl::RemoveAce](../Topic/CSacl::RemoveAce.md)|Quita un ACE específico \(entrada de control de acceso\) del objeto de **CSacl** .|  
|[CSacl::RemoveAllAces](../Topic/CSacl::RemoveAllAces.md)|Quita todos los ACE contenido en el objeto de `CSacl` .|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSacl::operator \=](../Topic/CSacl::operator%20=.md)|Operador de asignación.|  
  
## Comentarios  
 SACL contiene las entradas de \(ACEs\) control de acceso que especifican los tipos de intentos de acceso que generan los registros de auditoría en el registro de eventos de seguridad de un controlador de dominio.  Observe que SACL genera las entradas de registro sólo en el controlador de dominio en que el intento de acceso aparece, no en cada controlador de dominio que contiene una réplica del objeto.  
  
 Para establecer o recuperar SACL en el descriptor de seguridad de un objeto, el privilegio de SE\_SECURITY\_NAME debe habilitarse en el token de acceso del subproceso solicitante.  El grupo de administradores hace este privilegio conceder de forma predeterminada, y puede conceder a otros usuarios o grupos.  Hacer el privilegio conceder no es todo lo que se necesita: antes de que la operación definido por el privilegio puede realizar, el privilegio se debe habilitar en el token de acceso de seguridad surta efecto.  El modelo permite a continuación que deshabilitans privilegios están habilitados solo para las operaciones del sistema específicas y, cuando ya no se necesiten.  Vea [AtlGetSacl](../Topic/AtlGetSacl.md) y [AtlSetSacl](../Topic/AtlSetSacl.md) por ejemplos de habilitar SE\_SECURITY\_NAME.  
  
 Utilice los métodos de la clase proporcionados para agregar, quitar, para crear, eliminar ACE del objeto de **SACL** .  Vea también [AtlGetSacl](../Topic/AtlGetSacl.md) y [AtlSetSacl](../Topic/AtlSetSacl.md).  
  
 Para obtener una introducción al modelo de control de acceso de Windows, vea [control de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374860) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## Jerarquía de herencia  
 [CAcl](../../atl/reference/cacl-class.md)  
  
 `CSacl`  
  
## Requisitos  
 **encabezado:** atlsecurity.h  
  
## Vea también  
 [CAcl Class](../../atl/reference/cacl-class.md)   
 [ACLs](http://msdn.microsoft.com/library/windows/desktop/aa374872)   
 [ACEs](http://msdn.microsoft.com/library/windows/desktop/aa374868)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Security Global Functions](../../atl/reference/security-global-functions.md)