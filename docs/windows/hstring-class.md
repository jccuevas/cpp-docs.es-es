---
title: Hstring (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
dev_langs:
- C++
ms.assetid: 6709dd2e-8d72-4675-8ec7-1baa7d71854d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8544a78fdbdab19f44081853f5f5878f980cec01
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="hstring-class"></a>HString (Clase)
Una clase auxiliar para administrar la duración de HSTRING utilizando el modelo RAII.
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
class HString;  
```  
  
## <a name="remarks"></a>Comentarios  
 El tiempo de ejecución de Windows proporciona acceso a las cadenas a través de identificadores HSTRING. La clase HString proporciona funciones de comodidad y operadores para simplificar el uso de identificadores HSTRING. Esta clase puede controlar la duración de la HSTRING posee a través de un modelo RAII. 
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[HString::HString (constructor)](../windows/hstring-hstring-constructor.md)|Inicializa una nueva instancia de la clase HString.|  
|[HString::~HString (destructor)](../windows/hstring-tilde-hstring-destructor.md)|Destruye la instancia actual de la clase HString.|  
  
### <a name="members"></a>Miembros  
  
|Name|Descripción|  
|----------|-----------------|  
|[HString::Set (método)](../windows/hstring-set-method.md)|Establece el valor del objeto HString actual en la cadena de caracteres anchos especificada o el parámetro de HString.|  
|[HString::Attach (método)](../windows/hstring-attach-method.md)|Asocia el objeto HString especificado con el objeto de HString actual.|  
|[HString::CopyTo (método)](../windows/hstring-copyto-method.md)|Copia el HString actual objeto a un objeto HSTRING.|  
|[HString::Detach (método)](../windows/hstring-detach-method.md)|Desasocia el objeto especificado de HString de su valor subyacente.|  
|[HString::GetAddressOf (método)](../windows/hstring-getaddressof-method.md)|Recupera un puntero al identificador de HSTRING subyacente.|  
|[HString::Get (método)](../windows/hstring-get-method.md)|Recupera el valor del identificador HSTRING subyacente.|  
|[HString::Release (método)](../windows/hstring-release-method.md)|Elimina el valor de cadena subyacente e inicializa el objeto de HString actual en un valor vacío.|  
|[HString::MakeReference (método)](../windows/hstring-makereference-method.md)|Crea un objeto HStringReference de un parámetro de cadena especificada.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[HString::Operator= (operador)](../windows/hstring-operator-assign-operator.md)|Mueve el valor de otro objeto de HString al objeto HString actual.|  
|[HString::Operator== (operador)](../windows/hstring-operator-equality-operator.md)|Indica si los dos parámetros son iguales.|  
|[HString::Operator!= (operador)](../windows/hstring-operator-inequality-operator.md)|Indica si los dos parámetros no son iguales.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `HString`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Wrappers (espacio de nombres)](../windows/microsoft-wrl-wrappers-namespace.md)