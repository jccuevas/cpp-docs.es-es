---
title: no_auto_exclude | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_auto_exclude
dev_langs:
- C++
helpviewer_keywords:
- no_auto_exclude attribute
ms.assetid: 3241ef9c-758a-4e86-bdc5-37da6072430f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 67d077ca620661ffda2e8664b2a4fb9ef5ea7168
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408263"
---
# <a name="noautoexclude"></a>no_auto_exclude
**Específicos de C++**  
  
Deshabilita la exclusión automática.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
no_auto_exclude  
```  
  
## <a name="remarks"></a>Comentarios  
 
Las bibliotecas de tipos pueden incluir definiciones de elementos definidos en encabezados de sistema u otras bibliotecas de tipos. `#import` intenta evitar varios errores de definición mediante la exclusión automática de dichos elementos. Cuando esto sucede, [advertencia del compilador (nivel 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md) se emitirá para que cada elemento que desea excluir. Se puede deshabilitar esta exclusión automática con este atributo.  
  
**FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 
[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)