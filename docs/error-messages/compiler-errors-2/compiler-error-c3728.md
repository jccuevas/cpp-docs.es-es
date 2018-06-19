---
title: Error del compilador C3728 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3728
dev_langs:
- C++
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bae204db616db9e7d7e04cfd62d53374b0793aa9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273229"
---
# <a name="compiler-error-c3728"></a>Error del compilador C3728
'evento': evento no tiene un método raise  
  
 Metadatos creados con un lenguaje, como C#, que no permite que se genere desde fuera de la clase en la que se define un evento, se incluyó con el [#using](../../preprocessor/hash-using-directive-cpp.md) directiva y un programa de Visual C++ mediante programación con CLR intentó se genera el evento.  
  
 Para generar un evento en un programa desarrollado en un lenguaje como C#, la clase que contiene el evento debe definir también un método público que genera el evento.