---
title: Compilador advertencia (nivel 3) C4278 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4278
dev_langs: C++
helpviewer_keywords: C4278
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: eb1666d873d8b284c4739431e258bedc6586ff66
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4278"></a>Advertencia del compilador (nivel 3) C4278
'identificador': identificador de la biblioteca de tipos 'tlb' ya es una macro; Utilice el calificador 'rename'  
  
 Cuando se usa [#import](../../preprocessor/hash-import-directive-cpp.md), un identificador de la biblioteca de tipos que está importando intenta declarar un identificador ***identificador***. Sin embargo, esto ya es un símbolo válido.  
  
 Use la `#import` **cambiar el nombre de** atributo para asignar un alias al símbolo de la biblioteca de tipos.