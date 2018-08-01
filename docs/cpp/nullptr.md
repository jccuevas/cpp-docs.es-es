---
title: nullptr | Microsoft Docs
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
ms.openlocfilehash: 07e05e3a1c1b25e87053e15244f3c5fb9db442d9
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404166"
---
# <a name="nullptr"></a>nullptr
Designa una constante de puntero null de tipo `std::nullptr_t`, que se puede convertir a cualquier tipo de puntero sin formato.  Aunque puede usar la palabra clave **nullptr** sin incluir ningún encabezado, si el código usa el tipo `std::nullptr_t`, a continuación, debe definirlo incluyendo el encabezado `<cstddef>`.  
  
> [!NOTE]
>  El **nullptr** palabra clave también se define en C++ / c++ / CLI para aplicaciones de código administrado y no es intercambiable con la palabra clave de la norma ISO de C++. Si el código podría compilarse con la [/CLR](../build/reference/clr-common-language-runtime-compilation.md) , a continuación, utilice la opción del compilador, destinada a código administrado, `__nullptr` en cualquier línea de código donde debe garantizar que el compilador usa la interpretación de C++ nativa. Para obtener más información, consulte [nullptr](../windows/nullptr-cpp-component-extensions.md).  
  
## <a name="remarks"></a>Comentarios  
 Evite el uso de NULL o cero (`0`) como una constante de puntero nulo; **nullptr** es menos vulnerable a usos indebidos y funciona mejor en la mayoría de las situaciones.  Por ejemplo, dado `func(std::pair<const char *, double>)`, la llamada a `func(std::make_pair(NULL, 3.14))` produce un error del compilador.  La macro NULL se expande a `0`, de modo que la llamada `std::make_pair(0, 3.14)` devuelve `std::pair<int, double>`, que no se puede convertir al tipo de parámetro `std::pair<const char *, double>` de func().  La llamada a `func(std::make_pair(nullptr, 3.14))` se compila correctamente porque `std::make_pair(nullptr, 3.14)` devuelve `std::pair<std::nullptr_t, double>`, que se puede convertir en `std::pair<const char *, double>`.  
  
## <a name="see-also"></a>Vea también  
 [Palabras clave](../cpp/keywords-cpp.md)   
 [nullptr](../windows/nullptr-cpp-component-extensions.md)