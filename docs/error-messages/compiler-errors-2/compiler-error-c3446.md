---
title: C3446 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 07/21/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3446
dev_langs:
- C++
helpviewer_keywords:
- C3445
ms.assetid: 33064548-24e4-46f1-beb1-476e3c3b3fbf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a7715ebbc094c2c3c91aa3a0bb42f7df97bef08
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3446"></a>C3446 de Error del compilador  
  
>'*clase*': no se permite un inicializador de miembro predeterminado para un miembro de una clase de valor  
  
En Visual Studio 2015 y versiones anteriores, el compilador permitía (aunque omitía) un inicializador de miembro predeterminado para un miembro de una clase de valor. La inicialización predeterminada de una clase de valor siempre inicializa a cero a los miembros; no se permite un constructor predeterminado. En Visual Studio 2017, los inicializadores de miembro predeterminados generan un error del compilador, tal como se muestra en este ejemplo:

## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C3446 en Visual Studio de 2017 y versiones posteriores:  
  
```cpp  
// C3446.cpp  
value struct V
{
       int i = 0; // error C3446: 'V::i': a default member initializer  
                  // is not allowed for a member of a value class
       int j {0}; // C3446           
};
```  
  
Para corregir el error, quite al inicializador:  
  
```cpp  
// C3446b.cpp  
value struct V
{
       int i;  
       int j;
};
```  
  
