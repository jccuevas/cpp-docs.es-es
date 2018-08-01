---
title: _bstr_t::GetBSTR | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::GetBSTR
dev_langs:
- C++
helpviewer_keywords:
- GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8863f3a6c37693ec28f931c2af4cb0d299788daa
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402668"
---
# <a name="bstrtgetbstr"></a>_bstr_t::GetBSTR
**Específicos de Microsoft**  
  
 Señala al principio del objeto `BSTR` incluido en `_bstr_t`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
BSTR& GetBSTR( );  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Principio del objeto `BSTR` incluido en `_bstr_t`.  
  
## <a name="remarks"></a>Comentarios  
 **GetBSTR** afecta a todos los `_bstr_t` objetos que comparten un `BSTR`. Más de un `_bstr_t` puede compartir un `BSTR` mediante el uso del constructor de copias y y **operador =**.  
  
## <a name="example"></a>Ejemplo  
 Consulte [_bstr_t:: Assign](../cpp/bstr-t-assign.md) para obtener un ejemplo con **GetBSTR**.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_bstr_t (Clase)](../cpp/bstr-t-class.md)