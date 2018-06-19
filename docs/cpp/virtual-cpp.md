---
title: virtual (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- virtual_cpp
- virtual
dev_langs:
- C++
helpviewer_keywords:
- virtual base classes [C++], declaring
- base classes [C++], virtual
- virtual functions [C++], declaring
- virtual keyword [C++]
ms.assetid: c2eb987d-6cf3-43b6-aa0c-29a6f561b1ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 909fd3fde92479b2e5407608026cb01ec17fced2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32421801"
---
# <a name="virtual-c"></a>virtual (C++)
La palabra clave `virtual` declara una función virtual o una clase base virtual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
virtual [type-specifiers] member-function-declarator  
virtual [access-specifier] base-class-name  
```  
  
#### <a name="parameters"></a>Parámetros  
 `type-specifiers`  
 Especifica el tipo de valor devuelto de la función miembro virtual.  
  
 `member-function-declarator`  
 Declara una función miembro.  
  
 `access-specifier`  
 Define el nivel de acceso a la clase base: `public`, `protected` o `private`. Puede aparecer antes o después de la palabra clave `virtual`.  
  
 `base-class-name`  
 Identifica un tipo de clase declarado previamente.  
  
## <a name="remarks"></a>Comentarios  
 Vea [funciones virtuales](../cpp/virtual-functions.md) para obtener más información.  
  
 Consulte también las siguientes palabras clave: [clase](../cpp/class-cpp.md), [privada](../cpp/private-cpp.md), [público](../cpp/public-cpp.md), y [protegido](../cpp/protected-cpp.md).  
  
## <a name="see-also"></a>Vea también  
 [Palabras clave](../cpp/keywords-cpp.md)