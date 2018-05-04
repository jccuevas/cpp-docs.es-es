---
title: nullptr | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- nullptr_cpp
dev_langs:
- C++
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f1bcfee3f408f6815e51740f9fc02d842afaa4d5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="nullptr"></a>nullptr
Designa una constante de puntero null de tipo `std::nullptr_t`, que se puede convertir a cualquier tipo de puntero sin formato.  Aunque puede utilizar la palabra clave `nullptr` sin incluir ningún encabezado, si el código usa el tipo `std::nullptr_t`, debe definirlo incluyendo el encabezado `<cstddef>`.  
  
> [!NOTE]
>  La palabra clave `nullptr` también se define en C++/CLI para aplicaciones de código administrado y no es intercambiable con la palabra clave de C++ del estándar ISO. Si el código podría compilarse con la [/CLR](../build/reference/clr-common-language-runtime-compilation.md) opción del compilador, destinada a código administrado, a continuación, utilice `__nullptr` en cualquier línea de código donde debe garantizar que el compilador usa la interpretación de C++ nativo. Para obtener más información, consulte [nullptr](../windows/nullptr-cpp-component-extensions.md).  
  
## <a name="remarks"></a>Comentarios  
 Evite usar `NULL` o cero (`0`) como constante de puntero null; `nullptr` es menos vulnerable en caso de mal uso y funciona mejor en la mayoría de las situaciones.  Por ejemplo, dado `func(std::pair<const char *, double>)`, la llamada a `func(std::make_pair(NULL, 3.14))` produce un error del compilador.  La macro NULL se expande a `0`, de modo que la llamada `std::make_pair(0, 3.14)` devuelve `std::pair<int, double>`, que no se puede convertir al tipo de parámetro `std::pair<const char *, double>` de func().  La llamada a `func(std::make_pair(nullptr, 3.14))` se compila correctamente porque `std::make_pair(nullptr, 3.14)` devuelve `std::pair<std::nullptr_t, double>`, que se puede convertir en `std::pair<const char *, double>`.  
  
## <a name="see-also"></a>Vea también  
 [Palabras clave](../cpp/keywords-cpp.md)   
 [nullptr](../windows/nullptr-cpp-component-extensions.md)