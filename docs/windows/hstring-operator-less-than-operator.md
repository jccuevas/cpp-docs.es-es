---
title: 'Hstring:: operator&lt; operador | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator<
dev_langs:
- C++
ms.assetid: 48a051cb-4609-42be-b48c-d35fc99d1eab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1bdc6d54a6c9b60036d7434edec960715db304e2
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017687"
---
# <a name="hstringoperatorlt-operator"></a>Hstring:: operator&lt; operador
Indica si el primer parámetro es menor que el segundo parámetro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
inline bool operator<(  
    const HString& lhs,   
    const HString& rhs) throw()  
```  
  
### <a name="parameters"></a>Parámetros  
 *LHS*  
 El primer parámetro para comparar. *LHS* puede ser una referencia a un **HString**.  
  
 *RHS*  
 El segundo parámetro para comparar. *RHS* puede ser una referencia a un **HString**.  
  
## <a name="return-value"></a>Valor devuelto  
 **True** si el *lhs* parámetro es menor que el *rhs* parámetro; en caso contrario, **false**.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [HString (clase)](../windows/hstring-class.md)