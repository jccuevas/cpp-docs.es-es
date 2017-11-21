---
title: _bstr_t::GetAddress | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _bstr_t::GetAddress
dev_langs: C++
helpviewer_keywords: GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5921b3091532c63e3ba92d6e6e74f29a85123ac1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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
 `GetAddress` afecta a todos los objetos de `_bstr_t` que comparten `BSTR`. Varios `_bstr_t` pueden compartir `BSTR` mediante el uso del constructor copy y `operator=`.  
  
## <a name="example"></a>Ejemplo  
 Vea [_bstr_t:: Assign](../cpp/bstr-t-assign.md) para un ejemplo del uso `GetAddress`.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_bstr_t (Clase)](../cpp/bstr-t-class.md)