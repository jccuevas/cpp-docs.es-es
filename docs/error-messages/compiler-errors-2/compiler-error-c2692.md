---
title: C2692 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2692
dev_langs:
- C++
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 6e65c0310dfd82f86b49193fb173bb483fbd4333
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2692"></a>C2692 de Error del compilador
'nombre_de_función': las funciones prototipos totalmente necesarias en el compilador de C con el ' / clr' opción  
  
 Al compilar para .NET código administrado, el compilador de C requiere declaraciones de función ANSI. Además, si una función no toma ningún parámetro, debe declarar explícitamente `void` como el tipo de parámetro.
