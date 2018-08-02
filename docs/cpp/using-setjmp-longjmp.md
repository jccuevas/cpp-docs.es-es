---
title: Usar setjmp-longjmp | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- longjmp_cpp
- setjmp_cpp
dev_langs:
- C++
helpviewer_keywords:
- C++ exception handling, setjmp/longjmp functions
- setjmpex.h
- longjmp function in C++ programs
- setjmp.h
- setjmp function
- setjmp function, C++ programs
ms.assetid: 96be8816-f6f4-4567-9a9c-0c3c720e37c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2073729fc5445fc36e3d8a6f52c4f69b079c8b47
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462136"
---
# <a name="using-setjmplongjmp"></a>Usar setjmp/longjmp
Cuando [setjmp](../c-runtime-library/reference/setjmp.md) y [longjmp](../c-runtime-library/reference/longjmp.md) son usan juntos, proporcionan una forma de ejecutar un no locales **goto**. Se utilizan normalmente para pasar el control de la ejecución al control de errores o al código de recuperación en una rutina invocada anteriormente sin utilizar convenciones estándar de llamada o devolución.  
  
> [!CAUTION]
>  Sin embargo, dado que **setjmp** y **longjmp** no admiten la semántica de objeto de C++, y porque además pueden degradar el rendimiento evitando la optimización en variables locales, se recomienda no usar los programas en C++. Se recomienda que use **intente**/**catch** construcciones en su lugar.  
  
 Si decide usar **setjmp**/**longjmp** en un programa de C++, incluya también \<setjmp.h > o \<setjmpex.h > para garantizar la interacción correcta entre el las funciones y control de excepciones de C++. Si usas [/EH](../build/reference/eh-exception-handling-model.md) para compilar, se llama a destructores para objetos locales durante el desenredo de pila. Si usas **/EHs** para compilar y uno de su funciones llama a una función que utiliza [nothrow](../cpp/nothrow-cpp.md) y la función que usa **nothrow** llamadas **longjmp**, a continuación, el desenredo del destructor podría no producirse, dependiendo del optimizador.  
  
 En el código portable, cuando un usuario no local **goto** que llama a **longjmp** se ejecuta, destrucción correcta de los objetos basados en marcos podría no ser confiable.  
  
## <a name="see-also"></a>Vea también  
 [Mezclar excepciones de C (estructuradas) y de C++](../cpp/mixing-c-structured-and-cpp-exceptions.md)