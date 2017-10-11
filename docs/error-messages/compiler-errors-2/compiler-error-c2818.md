---
title: Error del compilador C2818 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2818
dev_langs:
- C++
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 02c1b8e67679e7b8ce69b202c3ddef899439095d
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2818"></a>Error del compilador C2818
aplicación de sobrecargado 'operator ->' es recursiva mediante el tipo 'tipo'  
  
 Una nueva definición del operador de acceso de miembro de clase contiene una recursiva `return` instrucción. Para volver a definir la `->` operador con la recursividad, se debe mover la rutina recursiva a una función independiente que se llamará desde el operador de reemplazo de función.
