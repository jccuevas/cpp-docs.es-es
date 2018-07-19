---
title: _bstr_t::GetAddress | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::GetAddress
dev_langs:
- C++
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4895153abe248265e0aacfbe636b9a4bd46ed205
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941202"
---
# <a name="bstrtgetaddress"></a>_bstr_t::GetAddress
**Específicos de Microsoft**  
  
 Libera cualquier cadena existente y devuelve la dirección de una cadena recién asignada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
BSTR* GetAddress( );  
  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Puntero a `BSTR` contenido en `_bstr_t`.  
  
## <a name="remarks"></a>Comentarios  
 `GetAddress` afecta a todos los objetos de `_bstr_t` que comparten `BSTR`. Más de un `_bstr_t` puede compartir un `BSTR` mediante el uso del constructor de copias y y **operador =**.  
  
## <a name="example"></a>Ejemplo  
 Consulte [_bstr_t:: Assign](../cpp/bstr-t-assign.md) para obtener un ejemplo con `GetAddress`.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_bstr_t (Clase)](../cpp/bstr-t-class.md)