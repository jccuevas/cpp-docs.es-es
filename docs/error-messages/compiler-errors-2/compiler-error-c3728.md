---
title: Error del compilador C3728 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3728
dev_langs:
- C++
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 100ef8275f938406a4f6a7d3909e04f40ce1d16b
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3728"></a>Error del compilador C3728
'evento': evento no tiene un método raise  
  
 Metadatos creados con un lenguaje, como C#, que no permite que se genere desde fuera de la clase en la que se define un evento, se incluyó con el [#using](../../preprocessor/hash-using-directive-cpp.md) directiva y un programa de Visual C++ mediante programación con CLR intentó se genera el evento.  
  
 Para generar un evento en un programa desarrollado en un lenguaje como C#, la clase que contiene el evento debe definir también un método público que genera el evento.
