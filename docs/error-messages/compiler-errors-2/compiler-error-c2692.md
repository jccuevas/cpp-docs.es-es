---
title: C2692 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2692
dev_langs:
- C++
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a02110750a748b5c520df7d202a87957f227a802
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33231001"
---
# <a name="compiler-error-c2692"></a>C2692 de Error del compilador
'nombre_de_función': las funciones prototipos totalmente necesarias en el compilador de C con el ' / clr' opción  
  
 Al compilar para .NET código administrado, el compilador de C requiere declaraciones de función ANSI. Además, si una función no toma ningún parámetro, debe declarar explícitamente `void` como el tipo de parámetro.