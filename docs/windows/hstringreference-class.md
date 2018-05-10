---
title: HStringReference (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference
dev_langs:
- C++
ms.assetid: 9bf823b1-17eb-4ac4-8c5d-27d27c7a4150
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 90e94471fe114eafec91a19ddad5d47ce39a8de7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="hstringreference-class"></a>HStringReference (Clase)
Representa un HSTRING que se crea a partir de una cadena existente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
class HStringReference;  
```  
  
## <a name="remarks"></a>Comentarios  
 La duración del búfer de copia de seguridad en el nuevo HSTRING no está administrada por el tiempo de ejecución de Windows. El llamador asigna una cadena de origen en el marco de pila para evitar una asignación del montón y eliminar el riesgo de pérdida de memoria. Además, el llamador debe asegurarse de que la cadena original permanece intacta durante la duración de la HSTRING adjunto. Para obtener más información, consulte [WindowsCreateStringReference función](http://msdn.microsoft.com/en-us/0361bb7e-da49-4289-a93e-de7aab8712ac).  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[HStringReference::HStringReference (constructor)](../windows/hstringreference-hstringreference-constructor.md)|Inicializa una nueva instancia de la clase HStringReference.|  
  
### <a name="members"></a>Miembros  
  
|Miembro|Descripción|  
|------------|-----------------|  
|[HStringReference::CopyTo (método)](../windows/hstringreference-copyto-method.md)|Copia el HStringReference actual objeto a un objeto HSTRING.|  
|[HStringReference::Get (método)](../windows/hstringreference-get-method.md)|Recupera el valor del identificador HSTRING subyacente.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[HStringReference::Operator= (operador)](../windows/hstringreference-operator-assign-operator.md)|Mueve el valor de otro objeto de HStringReference al objeto HStringReference actual.|  
|[HStringReference::Operator== (operador)](../windows/hstringreference-operator-equality-operator.md)|Indica si los dos parámetros son iguales.|  
|[HStringReference::Operator!= (operador)](../windows/hstringreference-operator-inequality-operator.md)|Indica si los dos parámetros no son iguales.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `HStringReference`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Wrappers (espacio de nombres)](../windows/microsoft-wrl-wrappers-namespace.md)