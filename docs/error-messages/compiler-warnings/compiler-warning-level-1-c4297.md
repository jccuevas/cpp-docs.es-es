---
title: Compilador (nivel 1) de la advertencia C4297 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4297
dev_langs:
- C++
helpviewer_keywords:
- C4297
ms.assetid: ba92fcdc-9f70-4f60-abe6-281f9582ca59
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: c21453d185fed2c33e7cb054e77e1698fadf491b
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4297"></a>Advertencia del compilador (nivel 1) C4297
'función': se suponía que la función no iniciaba una excepción, pero lo hace  
  
 Una declaración de función contiene un (posiblemente implícito) `noexcept` especificador, vacía `throw` especificador de excepción o un [__declspec (nothrow)](../../cpp/nothrow-cpp.md) atributo y la definición contiene uno o más [throw](../../cpp/try-throw-and-catch-statements-cpp.md) instrucciones. Para resolver la advertencia C4297, no intente iniciar excepciones en funciones declaradas `__declspec(nothrow)`, `noexcept(true)` o `throw()`. O bien, quite la especificación `noexcept`, `throw()` o `__declspec(nothrow)`.  
  
 De manera predeterminada, el compilador genera especificadores `noexcept(true)` implícitos para destructores definidos por el usuario, funciones de desasignador y funciones miembro especiales generadas por el compilador. Esto cumple la norma ISO C ++&11;. Para impedir la generación de especificadores de noexcept implícita y revertir al compilador que el comportamiento no estándar de Visual Studio 2013, utilice la **/Zc:implicitNoexcept-** opción del compilador. Para obtener más información, consulte [/Zc:implicitNoexcept (especificadores de excepción implícita)](../../build/reference/zc-implicitnoexcept-implicit-exception-specifiers.md).  
  
 Para obtener más información sobre las especificaciones de excepciones, vea [especificaciones de excepciones (throw)](../../cpp/exception-specifications-throw-cpp.md). Consulte también [/EH (Exception Handling Model)](../../build/reference/eh-exception-handling-model.md) para obtener información sobre cómo modificar el comportamiento del control en tiempo de compilación de excepción.  
  
 Esta advertencia también se genera para las funciones __declspec ([dllexport](../../cpp/dllexport-dllimport.md)) las funciones marcadas extern "C", incluso si son funciones de C++.  
  
 El siguiente ejemplo genera la advertencia C4297.  
  
```  
// C4297.cpp  
// compile with: /W1 /LD  
void __declspec(nothrow) f1()   // declared nothrow  
// try the following line instead  
// void f1()  
{  
   throw 1;   // C4297  
}  
```
