---
title: Error del compilador C2865 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2865
dev_langs:
- C++
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70b2c6c831fde18f9054e139a120d834a75b6950
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246221"
---
# <a name="compiler-error-c2865"></a>Error del compilador C2865
'función': comparación no válida de handle_or_pointer  
  
 Puede comparar las referencias a [clases y Structs](../../windows/classes-and-structs-cpp-component-extensions.md) o administrar los tipos de referencia de igualdad para comprobar si hacen referencia al mismo objeto (==) o a objetos diferentes (! =).  
  
 No puede comparar ellos para la ordenación debido a que el tiempo de ejecución de .NET puede pasarse objetos administrados en cualquier momento, cambiar el resultado de la prueba.