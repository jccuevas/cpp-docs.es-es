---
title: Compilador advertencia (nivel 3) C4278 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4278
dev_langs:
- C++
helpviewer_keywords:
- C4278
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b556166f61c5d77ac34fb7243ac25d5baeaa2b1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4278"></a>Advertencia del compilador (nivel 3) C4278
'identificador': identificador de la biblioteca de tipos 'tlb' ya es una macro; Utilice el calificador 'rename'  
  
 Cuando se usa [#import](../../preprocessor/hash-import-directive-cpp.md), un identificador de la biblioteca de tipos que está importando intenta declarar un identificador ***identificador***. Sin embargo, esto ya es un símbolo válido.  
  
 Use la `#import` **cambiar el nombre de** atributo para asignar un alias al símbolo de la biblioteca de tipos.