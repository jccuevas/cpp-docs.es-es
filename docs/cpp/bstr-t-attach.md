---
title: _bstr_t::Attach | Documentos de Microsoft
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
ms.openlocfilehash: eeb114a33d3ac356bff16aeab47b8d894b7513e6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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
 Vea [_bstr_t:: Assign](../cpp/bstr-t-assign.md) para obtener un ejemplo de uso **adjuntar**.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_bstr_t (Clase)](../cpp/bstr-t-class.md)