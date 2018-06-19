---
title: Compilador advertencia (nivel 4) C4092 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4092
dev_langs:
- C++
helpviewer_keywords:
- C4092
ms.assetid: 396ae826-a892-4327-bd66-f4762376d72b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ca145addc16306d613817643e363ecd9c95069a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292193"
---
# <a name="compiler-warning-level-4-c4092"></a>Compilador advertencia (nivel 4) C4092
sizeof devuelve 'unsigned long'  
  
 El operando de la `sizeof` operador era muy grande, por lo que `sizeof` devuelto unsigned **largo**. Esta advertencia se produce en las extensiones de Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)). Cuando está habilitada la compatibilidad con ANSI (/Za), el resultado se trunca en su lugar.