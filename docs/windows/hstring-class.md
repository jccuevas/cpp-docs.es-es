---
title: HString (clase) | Microsoft Docs
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
ms.openlocfilehash: 868d0a4e2d84add447c95bfcd9690c8a17850718
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39571456"
---
# <a name="hstring-class"></a>HString (Clase)
Una clase auxiliar para administrar la duración de una cadena HSTRING mediante el modelo RAII.
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
class HString;  
```  
  
## <a name="remarks"></a>Comentarios  
 El tiempo de ejecución de Windows proporciona acceso a las cadenas a través de identificadores HSTRING. El **HString** clase proporciona funciones de comodidad y operadores para simplificar el uso de identificadores de HSTRING. Esta clase puede controlar la duración de HSTRING posee a través de un modelo RAII. 
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[HString::HString (constructor)](../windows/hstring-hstring-constructor.md)|Inicializa una nueva instancia de la **HString** clase.|  
|[HString::~HString (destructor)](../windows/hstring-tilde-hstring-destructor.md)|Destruye la instancia actual de la **HString** clase.|  
  
### <a name="members"></a>Miembros  
  
|Name|Descripción|  
|----------|-----------------|  
|[HString::Set (método)](../windows/hstring-set-method.md)|Establece el valor del elemento actual **HString** objeto en la cadena especificada de caracteres anchos o **HString** parámetro.|  
|[HString::Attach (método)](../windows/hstring-attach-method.md)|Asocia especificado **HString** objeto con el actual **HString** objeto.|  
|[HString::CopyTo (método)](../windows/hstring-copyto-method.md)|Copia actual **HString** objeto a un objeto HSTRING.|  
|[HString::Detach (método)](../windows/hstring-detach-method.md)|Anula la asociación entre **HString** objeto desde su valor subyacente.|  
|[HString::GetAddressOf (método)](../windows/hstring-getaddressof-method.md)|Recupera un puntero al identificador HSTRING subyacente.|  
|[HString::Get (método)](../windows/hstring-get-method.md)|Recupera el valor del identificador HSTRING subyacente.|  
|[HString::Release (método)](../windows/hstring-release-method.md)|Elimina el valor de cadena subyacente e inicializa actual **HString** objeto en un valor vacío.|  
|[HString::MakeReference (método)](../windows/hstring-makereference-method.md)|Crea un `HStringReference` objeto a partir de un parámetro de cadena especificado.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[HString::Operator= (operador)](../windows/hstring-operator-assign-operator.md)|Mueve el valor de otro **HString** el objeto actual **HString** objeto.|  
|[HString::Operator== (operador)](../windows/hstring-operator-equality-operator.md)|Indica si los dos parámetros son iguales.|  
|[HString::Operator!= (operador)](../windows/hstring-operator-inequality-operator.md)|Indica si los dos parámetros no son iguales.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `HString`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Wrappers (espacio de nombres)](../windows/microsoft-wrl-wrappers-namespace.md)