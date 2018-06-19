---
title: Constructor hstring | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::HString
dev_langs:
- C++
ms.assetid: 6da12785-ed01-4720-a004-667db60298f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a3188e137d3a39fb26ca4151f72073306038e46f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876883"
---
# <a name="hstringhstring-constructor"></a>HString::HString (Constructor)
Inicializa una nueva instancia de la clase HString.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HString(HSTRING hstr = nullptr) throw();  
HString(HString&& other) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `hstr`  
 Un controlador HSTRING.  
  
 `other`  
 Un objeto HString existente.  
  
## <a name="remarks"></a>Comentarios  
 El primer constructor inicializa un nuevo objeto HString que está vacío.  
  
 El segundo constructor inicializa un nuevo objeto de HString para el valor de la existente `other` parámetro y, a continuación, destruye el `other` parámetro.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [HString (clase)](../windows/hstring-class.md)