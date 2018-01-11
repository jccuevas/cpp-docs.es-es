---
title: Error del compilador C2865 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2865
dev_langs: C++
helpviewer_keywords: C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 149ca019ef30d66dba63bc927d79064a269d8c70
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2865"></a>Error del compilador C2865
'función': comparación no válida de handle_or_pointer  
  
 Puede comparar las referencias a [clases y Structs](../../windows/classes-and-structs-cpp-component-extensions.md) o administrar los tipos de referencia de igualdad para comprobar si hacen referencia al mismo objeto (==) o a objetos diferentes (! =).  
  
 No puede comparar ellos para la ordenación debido a que el tiempo de ejecución de .NET puede pasarse objetos administrados en cualquier momento, cambiar el resultado de la prueba.