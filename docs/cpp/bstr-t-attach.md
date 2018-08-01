---
title: _bstr_t::Attach | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::Attach
dev_langs:
- C++
helpviewer_keywords:
- Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9f69811b7b25a793d11ef6d53aaf0638c752a11
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39409110"
---
# <a name="bstrtattach"></a>_bstr_t::Attach
**Específicos de Microsoft**  
  
 Vincula un contenedor `_bstr_t` a un `BSTR`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void Attach(  
   BSTR s  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *s*  
 `BSTR` que se va a asociar con, o asignar a, la variable `_bstr_t`.  
  
## <a name="remarks"></a>Comentarios  
 Si `_bstr_t` se ha asociado previamente a otro `BSTR`, `_bstr_t` limpiará el recurso de `BSTR`, si ninguna otra variable `_bstr_t` está utilizando `BSTR`.  
  
## <a name="example"></a>Ejemplo  
 Consulte [_bstr_t:: Assign](../cpp/bstr-t-assign.md) para obtener un ejemplo con **adjuntar**.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_bstr_t (Clase)](../cpp/bstr-t-class.md)