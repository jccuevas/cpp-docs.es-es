---
title: Usar setjmp longjmp | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- longjmp_cpp
- setjmp_cpp
dev_langs:
- C++
helpviewer_keywords:
- C++ exception handling, setjmp/longjmp functions
- SETJMPEX.H
- longjmp function in C++ programs
- SETJMP.H
- setjmp function
- setjmp function, C++ programs
ms.assetid: 96be8816-f6f4-4567-9a9c-0c3c720e37c5
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 356924c0a93f6d9d21bb417f84836385491b2144
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="using-setjmplongjmp"></a>Usar setjmp/longjmp
Cuando [setjmp](../c-runtime-library/reference/setjmp.md) y [longjmp](../c-runtime-library/reference/longjmp.md) son usan juntos, proporcionan una manera de ejecutar un no locales `goto`. Se utilizan normalmente para pasar el control de la ejecución al control de errores o al código de recuperación en una rutina invocada anteriormente sin utilizar convenciones estándar de llamada o devolución.  
  
> [!CAUTION]
>  Sin embargo, como `setjmp` y `longjmp` no admiten la semántica de objeto de C++, y como además pueden degradar el rendimiento evitando la optimización en variables locales, se recomienda que no se utilicen en los programas de C++. Se recomienda que use `try` / `catch` construye en su lugar.  
  
 Si decide usar `setjmp` / `longjmp` en un programa de C++, también puede incluir SETJMP. H o SETJMPEX. H para garantizar la interacción correcta entre las funciones y el control de excepciones de C++. Si usa [/EH](../build/reference/eh-exception-handling-model.md) para compilar, se llaman a destructores para los objetos locales durante el desenredo de la pila. Si usa **/EHs** para compilar y uno de sus funciones llama a una función que utiliza [nothrow](../cpp/nothrow-cpp.md) y la función que usa `nothrow` llamadas `longjmp`, a continuación, no puede producir el desenredo del destructor, Dependiendo del optimizador.  
  
 En código portable, cuando se ejecuta una instrucción `goto` no local que llama a `longjmp`, la destrucción correcta de objetos basados en marcos podría no ser confiable.  
  
## <a name="see-also"></a>Vea también  
 [Mezclar excepciones de C (estructuradas) y de C++](../cpp/mixing-c-structured-and-cpp-exceptions.md)
