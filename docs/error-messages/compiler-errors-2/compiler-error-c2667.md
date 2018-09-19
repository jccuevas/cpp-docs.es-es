---
title: Error del compilador C2667 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2667
dev_langs:
- C++
helpviewer_keywords:
- C2667
ms.assetid: 3c91d9d1-18fa-4e0d-a9ba-984d38980ca3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5d6d14cf04ae399b10cbaa393d9e9fcc7133f274
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46095253"
---
# <a name="compiler-error-c2667"></a>Error del compilador C2667

'function': ninguna de las sobrecargas número tiene una conversión mejor

Una llamada de función sobrecargada es ambigua y no se puede resolver.

La conversión necesaria para coincidir con los parámetros reales de la llamada de función a una de las funciones sobrecargadas debe ser estrictamente mejor que las conversiones necesarias todas las funciones sobrecargadas.

Consulte el artículo de Knowledge Base Q240869 para obtener más información sobre la ordenación parcial de plantillas de función.