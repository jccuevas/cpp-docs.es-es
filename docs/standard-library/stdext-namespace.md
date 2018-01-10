---
title: stdext (Espacio de nombres) | Microsoft Docs
ms.custom: 
ms.date: 09/06/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: stdext
dev_langs: C++
helpviewer_keywords:
- _DEFINE_DEPRECATED_HASH_CLASSES symbol
- stdext namespace
ms.assetid: 3e94fc89-0584-424f-bc09-081b73379545
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 59da07c0cea58e9fc4b544b9f3bad937b2951f9e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="stdext-namespace"></a>stdext (espacio de nombres)

Los miembros de la [ \<hash_map >](../standard-library/hash-map.md) y [ \<hash_set >](../standard-library/hash-set.md) archivos de encabezado no son parte del estándar ISO C++. Por lo tanto, estos tipos y miembros se movieron del espacio de nombres `std` al espacio de nombres `stdext`, para seguir siendo compatibles con el estándar de C++.

Cuando se compila con [/Ze](../build/reference/za-ze-disable-language-extensions.md), que es el valor predeterminado, el compilador advierte sobre el uso de `std` para los miembros de la \<hash_map > y \<hash_set > archivos de encabezado. Para deshabilitar la advertencia, use el pragma [warning](../preprocessor/warning.md) .

Para que el compilador genere un error para el uso de `std` para los miembros de la \<hash_map > y \<hash_set > archivos de encabezado con **/Ze**, agregue la siguiente directiva antes de `#include` los archivos de encabezado Biblioteca estándar de C++.

```cpp  
#define _DEFINE_DEPRECATED_HASH_CLASSES 0  
```  

Cuando se compila con **/Za**, el compilador genera un error.  

## <a name="see-also"></a>Vea también

[Información general sobre la biblioteca estándar de C++](../standard-library/cpp-standard-library-overview.md)

