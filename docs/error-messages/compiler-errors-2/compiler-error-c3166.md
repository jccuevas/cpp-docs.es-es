---
title: C3166 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3166
dev_langs:
- C++
helpviewer_keywords:
- C3166
ms.assetid: ec3e330d-c15d-4158-8268-09101486c566
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f1996da7bb937fd00a4283ad94a4885432a9d47a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33247711"
---
# <a name="compiler-error-c3166"></a>C3166 de Error del compilador
'puntero': no se puede declarar un puntero a un puntero __gc interior como miembro de 'tipo'  
  
El compilador encontró una declaración de puntero no válido (un `__nogc` puntero a un `__gc` puntero.). 
  
Solo es accesible mediante la opción del compilador obsoleta C3166 **/CLR: oldSyntax**.  
