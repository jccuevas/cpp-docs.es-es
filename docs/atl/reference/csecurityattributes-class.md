---
title: Clase CSecurityAttributes | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::Set
dev_langs: C++
helpviewer_keywords: CSecurityAttributes class
ms.assetid: a094880c-52e1-4a28-97ff-752d5869908e
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8ed8a9336a60b3577f856f0bc2bd6baa358aec6d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="csecurityattributes-class"></a>Clase de CSecurityAttributes
Esta clase es un contenedor fino para la estructura de atributos de seguridad.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CSecurityAttributes : public SECURITY_ATTRIBUTES
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSecurityAttributes::CSecurityAttributes](#csecurityattributes)|El constructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSecurityAttributes:: Set](#set)|Llamar a este método para establecer los atributos de la `CSecurityAttributes` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 El **SECURITY_ATTRIBUTES** estructura contiene una [descriptor de seguridad](http://msdn.microsoft.com/library/windows/desktop/aa379561) utilizado para la creación de un objeto y especifica si el identificador que se recuperan mediante la especificación de esta estructura es heredable.  
  
 Para obtener una introducción al modelo de control de acceso en Windows, consulte [el Control de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374860) en el SDK de Windows.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `SECURITY_ATTRIBUTES`  
  
 `CSecurityAttributes`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsecurity.h  
  
##  <a name="csecurityattributes"></a>CSecurityAttributes::CSecurityAttributes  
 El constructor.  
  
```
CSecurityAttributes() throw();
explicit CSecurityAttributes(const CSecurityDesc& rSecurityDescriptor, bool bInheritsHandle = false) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `rSecurityDescriptor`  
 Referencia a un descriptor de seguridad.  
  
 `bInheritsHandle`  
 Especifica si se hereda el identificador devuelto cuando se crea un nuevo proceso. Si este miembro es true, el nuevo proceso hereda el identificador.  
  
##  <a name="set"></a>CSecurityAttributes:: Set  
 Llamar a este método para establecer los atributos de la `CSecurityAttributes` objeto.  
  
```
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `rSecurityDescriptor`  
 Referencia a un descriptor de seguridad.  
  
 `bInheritHandle`  
 Especifica si se hereda el identificador devuelto cuando se crea un nuevo proceso. Si este miembro es true, el nuevo proceso hereda el identificador.  
  
### <a name="remarks"></a>Comentarios  
 Este método se utiliza el constructor para inicializar el `CSecurityAttributes` objeto.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de seguridad](../../visual-cpp-samples.md)   
 [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)   
 [descriptor de seguridad](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [Información general de clases](../../atl/atl-class-overview.md)   
 [Funciones globales de seguridad](../../atl/reference/security-global-functions.md)
