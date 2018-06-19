---
title: Error del compilador C2930 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2930
dev_langs:
- C++
helpviewer_keywords:
- C2930
ms.assetid: f07eecd1-e5d1-4518-bd89-b1fd2a003a17
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1d2d1890b86292cec062d64e1fe56c5769178444
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33247877"
---
# <a name="compiler-error-c2930"></a>Error del compilador C2930
'class': el identificador de clase de tipo se volvió a definir como un enumerador de 'enum identifier'  
  
 No puede usar una clase genérica o de plantilla como una enumeración.  
  
 Este error puede producirse si las llaves no coinciden como es debido.  
  
 El ejemplo siguiente genera la advertencia C2930:  
  
```  
// C2930.cpp  
// compile with: /c  
template<class T>   
class x{};  
enum SomeEnum { x };   // C2930  
  
class y{};  
enum SomeEnum { y };  
```  
  
 También se puede producir C2930 al utilizar genéricos:  
  
```  
// C2930c.cpp  
// compile with: /clr /c  
generic<class T>   
ref struct GC {};  
enum SomeEnum { GC };   // C2930  
  
ref struct GC2 {};  
enum SomeEnum2 { GC2 };  
```