---
title: Compilador (nivel 1) de la advertencia C4297 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4297
dev_langs:
- C++
helpviewer_keywords:
- C4297
ms.assetid: ba92fcdc-9f70-4f60-abe6-281f9582ca59
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2c37f82b646902d08c8fc2ce633948969d0755f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281981"
---
# <a name="compiler-warning-level-1-c4297"></a>Advertencia del compilador (nivel 1) C4297
'función': se suponía que la función no iniciaba una excepción, pero lo hace  
  
 Una declaración de función contiene un (posiblemente implícito) `noexcept` especificador, vacío `throw` especificador de excepción, o un [__declspec (nothrow)](../../cpp/nothrow-cpp.md) atributo y la definición contiene uno o varios [throw ](../../cpp/try-throw-and-catch-statements-cpp.md) instrucciones. Para resolver la advertencia C4297, no intente iniciar excepciones en funciones declaradas `__declspec(nothrow)`, `noexcept(true)` o `throw()`. O bien, quite la especificación `noexcept`, `throw()` o `__declspec(nothrow)`.  
  
 De manera predeterminada, el compilador genera especificadores `noexcept(true)` implícitos para destructores definidos por el usuario, funciones de desasignador y funciones miembro especiales generadas por el compilador. Esto cumple la norma ISO C ++ 11. Para evitar la generación de especificadores noexcept implícitos y revertir al compilador que el comportamiento no estándar de Visual Studio 2013, use la **Zc** opción del compilador. Para obtener más información, consulte [/Zc: implicitnoexcept (especificadores de excepción implícita)](../../build/reference/zc-implicitnoexcept-implicit-exception-specifiers.md).  
  
 Para obtener más información acerca de las especificaciones de excepción, vea [especificaciones de excepciones (throw)](../../cpp/exception-specifications-throw-cpp.md). Consulte también [/EH (modelo de control de excepciones)](../../build/reference/eh-exception-handling-model.md) para obtener información sobre cómo modificar el comportamiento del control en tiempo de compilación de excepción.  
  
 Esta advertencia también se genera para las funciones __declspec ([dllexport](../../cpp/dllexport-dllimport.md)) las funciones marcadas como extern "C", incluso si son funciones de C++.  
  
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