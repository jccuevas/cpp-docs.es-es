---
title: WeakReference Class1 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference
dev_langs:
- C++
helpviewer_keywords:
- WeakReference class
ms.assetid: 3f4c956b-dbbd-49b1-8cfa-9509a9956c97
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a44b992138371ff33a9059990a5ec3e93689c679
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891651"
---
# <a name="weakreference-class1"></a>WeakReference Class1
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class WeakReference;  
```  
  
## <a name="remarks"></a>Comentarios  
 Representa un *referencia débil* que se puede utilizar con el tiempo de ejecución de Windows o COM clásico. Una referencia débil representa un objeto que puede ser o no accesible.  
  
 A `WeakReference` objeto mantiene un *referencia segura*, que es un puntero a un objeto y un *recuento de referencia segura*, que es el número de copias de la referencia segura que se han distribuido por el método Resolve(). Mientras el recuento de referencia segura es distinto de cero, la referencia segura no es válida y el objeto es accesible. Cuando el recuento de referencia segura se convierte en cero, la referencia segura no es válida y el objeto es accesible.  
  
 Un objeto WeakReference normalmente se usa para representar un objeto cuya existencia se controla mediante una aplicación o un subproceso externo. Por ejemplo, crear un objeto WeakReference desde una referencia a un objeto de archivo. Mientras el archivo esté abierto, la referencia segura será válida. Sin embargo, si el archivo está abierto, la referencia segura no será válida.  
  
 Los métodos de WeakReference son seguros para subprocesos.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[WeakReference::WeakReference (constructor)](../windows/weakreference-weakreference-constructor.md)|Inicializa una nueva instancia de la clase WeakReference.|  
|[WeakReference::~WeakReference (destructor)](../windows/weakreference-tilde-weakreference-destructor.md)|Desinicializa (destruye) la instancia actual de la clase WeakReference.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[WeakReference::DecrementStrongReference (método)](../windows/weakreference-decrementstrongreference-method.md)|Disminuye el seguro recuento de referencias del objeto WeakReference actual.|  
|[WeakReference::IncrementStrongReference (método)](../windows/weakreference-incrementstrongreference-method.md)|Incrementa el recuento de referencia segura del objeto WeakReference actual.|  
|[WeakReference::Resolve (método)](../windows/weakreference-resolve-method.md)|Establece el puntero especificado en el valor de referencia segura actual si el recuento de referencia segura es distinto de cero.|  
|[WeakReference::SetUnknown (método)](../windows/weakreference-setunknown-method.md)|Establece la referencia segura del objeto WeakReference actual en el puntero de interfaz especificado.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `WeakReference`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)