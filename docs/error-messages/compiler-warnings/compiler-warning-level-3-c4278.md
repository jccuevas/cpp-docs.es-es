---
title: Compilador advertencia (nivel 3) C4278 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4278
dev_langs:
- C++
helpviewer_keywords:
- C4278
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 249b13b70f3f10942852d7a9aa13dcf4f08e1f7f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4278"></a>Advertencia del compilador (nivel 3) C4278
'identificador': identificador de la biblioteca de tipos 'tlb' ya es una macro; Utilice el calificador 'rename'  
  
 Cuando se usa [#import](../../preprocessor/hash-import-directive-cpp.md), un identificador de la biblioteca de tipos que está importando intenta declarar un identificador ***identificador***. Sin embargo, esto ya es un símbolo válido.  
  
 Use la `#import` **cambiar el nombre de** atributo para asignar un alias al símbolo de la biblioteca de tipos.