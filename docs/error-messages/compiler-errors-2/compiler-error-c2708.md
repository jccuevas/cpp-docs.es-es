---
title: C2708 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2708
dev_langs: C++
helpviewer_keywords: C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 495fd9aeaad785edd8653e46ae666f60c337b12d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2708"></a>C2708 de Error del compilador
'identificador': longitud de parámetros reales en bytes es distinta respecto llamada anterior o referencia  
  
 A [__stdcall](../../cpp/stdcall.md) función debe ir precedida de un prototipo. En caso contrario, el compilador interpreta la primera llamada a la función como un prototipo y este error se produce cuando el compilador encuentra una llamada que no coincide.  
  
 Para corregir este error, agregue un prototipo de función.