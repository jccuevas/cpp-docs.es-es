---
title: Problemas comunes de migración de 64 bits de Visual C++ | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- 64-bit programming [C++], migration
- 64-bit compiler [C++], migration
- porting 32-bit code to 64-bit code
- upgrading Visual C++ applications, 32-bit code
- migration [C++], 64-bit code issues
- 32-bit code porting [C++]
- 64-bit applications [C++]
- 64-bit compiler [C++], porting 32-bit code
- Win64 [C++]
ms.assetid: d17fb838-7513-4e2d-8b27-a1666f17ad76
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ab4b8a8e693a9e1a87ddb3a06fe609416808d3dc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367734"
---
# <a name="common-visual-c-64-bit-migration-issues"></a>Problemas comunes de migración a 64 bits en Visual C++

Al utilizar Visual C++ para crear aplicaciones que se ejecutan en un sistema operativo Windows de 64 bits, debe tener en cuenta lo siguiente:  
  
-   `int` y `long` son valores de 32 bits en sistemas operativos Windows de 64 bits. Debe tener cuidado de no asignar punteros a variables de 32 bits en los programas que piense compilar para plataformas de 64 bits. Los punteros son de 64 bits en las plataformas de 64 bits; si asigna un puntero a una variable de 32 bits, se truncará su valor.  
  
-   `size_t`, `time_t`, y `ptrdiff_t` son valores de 64 bits en sistemas operativos de Windows de 64 bits.  
  
-   `time_t` es un valor de 32 bits en sistemas de operativos Windows de 32 bits en las versiones de Visual C++ anteriores a Visual C++ 2005. `time_t` es ahora un entero de 64 bits de forma predeterminada. Para obtener más información, consulte [administración del tiempo](../c-runtime-library/time-management.md).  
  
     Debe tener en cuenta los lugares en que el código toma un valor `int` y lo procesa como valor `size_t` o `time_t`. Es posible que el número aumente hasta superar un número de 32 bits y que los datos se trunquen al volver a pasarlo al almacenamiento `int`.  
  
El modificador `printf` %x (`int` en formato hexadecimal) no funcionará según lo esperado en un sistema operativo Windows de 64 bits. Sólo operará en los primeros 32 bits del valor que se le pasa.  
  
-   Use % I32x para presentar un tipo entero de 32 bits en formato hexadecimal.  
  
-   Use % I32x para presentar un tipo entero de 64 bits en formato hexadecimal.  
  
-   El modificador %p (un puntero en formato hexadecimal) funcionará según lo esperado en un sistema operativo Windows de 64 bits.  
  
Para obtener más información, consulte:  
  
-   [Opciones del compilador](../build/reference/compiler-options.md)  
  
-   [Sugerencias de migración](http://msdn.microsoft.com/library/windows/desktop/aa384214)  
  
## <a name="see-also"></a>Vea también  

[Configurar Visual C++ de 64 bits, x64 destinos](../build/configuring-programs-for-64-bit-visual-cpp.md)   
[Guía de migración y actualización de Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)