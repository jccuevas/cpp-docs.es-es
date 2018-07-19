---
title: C2708 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2708
dev_langs:
- C++
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d30b2e5c1856a604ae314316cd71d6acc00a7c74
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234765"
---
# <a name="compiler-error-c2708"></a>C2708 de Error del compilador
'identificador': longitud de parámetros reales en bytes es distinta respecto llamada anterior o referencia  
  
 A [__stdcall](../../cpp/stdcall.md) función debe ir precedida de un prototipo. En caso contrario, el compilador interpreta la primera llamada a la función como un prototipo y este error se produce cuando el compilador encuentra una llamada que no coincide.  
  
 Para corregir este error, agregue un prototipo de función.