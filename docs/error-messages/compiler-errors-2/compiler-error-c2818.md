---
title: Error del compilador C2818 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2818
dev_langs:
- C++
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 10d7f419d528fcd2445b82e29d92442002624909
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2818"></a>Error del compilador C2818
aplicación de sobrecargado 'operator ->' es recursiva mediante el tipo 'tipo'  
  
 Una nueva definición del operador de acceso de miembro de clase contiene una recursiva `return` instrucción. Para volver a definir la `->` operador con la recursividad, se debe mover la rutina recursiva a una función independiente que se llamará desde el operador de reemplazo de función.