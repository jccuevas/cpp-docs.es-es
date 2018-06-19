---
title: Error del compilador C2803 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2803
dev_langs:
- C++
helpviewer_keywords:
- C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 51cf2a8b38a86fcd97ab693b3853fe25527a0bb3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236228"
---
# <a name="compiler-error-c2803"></a>Error del compilador C2803
'operador' debe tener al menos un parámetro formal de tipo de clase  
  
 El operador sobrecargado le falta un parámetro de tipo de clase.  
  
 Es necesario pasar al menos un parámetro por referencia (sin utilizar punteros, pero las referencias) o por valor para que pueda escribir "una < b" (un y b es de una clase de tipo A).  
  
 Si ambos parámetros son punteros será una simple comparación de direcciones de puntero y no utiliza la conversión definida por el usuario.  
  
 El ejemplo siguiente genera C2803:  
  
```  
// C2803.cpp  
// compile with: /c  
class A{};  
bool operator< (const A *left, const A *right);   // C2803  
// try the following line instead  
// bool operator< (const A& left, const A& right);  
```