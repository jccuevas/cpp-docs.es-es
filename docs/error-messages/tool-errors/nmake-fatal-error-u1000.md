---
title: Error grave de NMAKE U1000 | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1000
dev_langs:
- C++
helpviewer_keywords:
- U1000
ms.assetid: 49b9bd9e-f1bc-4b55-a171-c748e40b195e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 69909c542a02baf8aa261c8ef78413a877a223a7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194893"
---
# <a name="nmake-fatal-error-u1000"></a>Error grave de NMAKE U1000

> error de sintaxis: ')' no se encuentra en la llamada de macro

Un paréntesis de apertura, **(**, sin un paréntesis coincidente, se sentía **)**, en una llamada de macro. El formato correcto es **$(**<em>nombre</em>**)**; **$** <em>n</em> está permitida para nombres de un carácter.