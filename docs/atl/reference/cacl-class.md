---
title: "CAcl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAcl"
  - "ATL::CAcl"
  - "ATLSECURITY/CAcl"
  - "ATL.CAcl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAcl class"
ms.assetid: 20bcb9af-dc1c-4737-b923-3864776680d6
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CAcl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase es un contenedor para una estructura de `ACL` \(lista de control de acceso\).  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CAcl  
  
```  
  
## Members  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAcl::CAccessMaskArray](../Topic/CAcl::CAccessMaskArray.md)|Una matriz de s de `ACCESS_MASK`.|  
|[CAcl::CAceFlagArray](../Topic/CAcl::CAceFlagArray.md)|Una matriz de s de `BYTE`.|  
|[CAcl::CAceTypeArray](../Topic/CAcl::CAceTypeArray.md)|Una matriz de s de `BYTE`.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAcl::CAcl](../Topic/CAcl::CAcl.md)|el constructor.|  
|[CAcl::~CAcl](../Topic/CAcl::~CAcl.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAcl::GetAceCount](../Topic/CAcl::GetAceCount.md)|Devuelve el número de objetos de \(ACE\) de entrada de control de acceso.|  
|[CAcl::GetAclEntries](../Topic/CAcl::GetAclEntries.md)|Recupera las entradas \(ACL\) de la lista de control de acceso a objetos de `CAcl` .|  
|[CAcl::GetAclEntry](../Topic/CAcl::GetAclEntry.md)|Recupera toda la información sobre una entrada en un objeto de `CAcl` .|  
|[CAcl::GetLength](../Topic/CAcl::GetLength.md)|Devuelve la longitud de ACL.|  
|[CAcl::GetPACL](../Topic/CAcl::GetPACL.md)|Devuelve un PACL \(puntero a ACL\).|  
|[CAcl::IsEmpty](../Topic/CAcl::IsEmpty.md)|prueba el objeto de `CAcl` para las entradas.|  
|[CAcl::IsNull](../Topic/CAcl::IsNull.md)|Devuelve el estado del objeto de `CAcl` .|  
|[CAcl::RemoveAce](../Topic/CAcl::RemoveAce.md)|Quita un ACE específico \(entrada de control de acceso\) del objeto de `CAcl` .|  
|[CAcl::RemoveAces](../Topic/CAcl::RemoveAces.md)|Quita todos los ACE \(entradas de control de acceso\) de `CAcl` que se aplica a `CSid`especificado.|  
|[CAcl::SetEmpty](../Topic/CAcl::SetEmpty.md)|marca el objeto de `CAcl` como vacío.|  
|[CAcl::SetNull](../Topic/CAcl::SetNull.md)|Marca el objeto de `CAcl` como `NULL`.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAcl::operator const ACL \*](../Topic/CAcl::operator%20const%20ACL%20*.md)|Convierte un objeto de `CAcl` a una estructura de `ACL` .|  
|[CAcl::operator \=](../Topic/CAcl::operator%20=.md)|Operador de asignación.|  
  
## Comentarios  
 La estructura de **ACL** es el encabezado ACL \(lista de control de acceso\).  ACL incluye una lista secuencial de cero o más [as](http://msdn.microsoft.com/library/windows/desktop/aa374868) \(entradas de control de acceso\).  El ACE individual en ACL se numera comprendido entre 0 y *n\-1*, donde *n* es el número de ACE en ACL.  Al editar ACL, una aplicación hace referencia a una entrada de control de acceso \(ACE\) dentro de ACL por su índice.  
  
 Hay dos tipos de ACL:  
  
-   Discrecional  
  
-   Sistema  
  
 ACL discrecional controla el propietario de un objeto o de cualquier persona acceso concedido de **WRITE\_DAC** al objeto.  Especifica los usuarios concretos de acceso y grupos pueden tener que un objeto.  Por ejemplo, el propietario de un archivo puede utilizar ACL discrecional para controlar qué usuarios y grupos pueden y no pueden tener acceso al archivo.  
  
 Un objeto puede obtener información de seguridad de nivel de sistema asociada a él, en forma de sistema ACL controlado por un administrador del sistema.  Un sistema ACL puede permitir que el administrador del sistema audite cualquier intento de obtener acceso a un objeto.  
  
 Para obtener más detalles, vea la descripción de [ACL](http://msdn.microsoft.com/library/windows/desktop/aa374872) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener una introducción al modelo de control de acceso de Windows, vea [control de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374860) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## Requisitos  
 **encabezado:** atlsecurity.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)   
 [Security Global Functions](../../atl/reference/security-global-functions.md)