---
title: Error irrecuperable C1211 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1211
dev_langs:
- C++
helpviewer_keywords:
- C1211
ms.assetid: df0ca70d-ec6e-4400-926a-b877e2599978
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 444d2bc25c2eddd5ea9a0170272bd3e71b61f94f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018535"
---
# <a name="fatal-error-c1211"></a>Error irrecuperable C1211

La versión del runtime instalada no admite el atributo personalizado TypeForwardedTo

El error C1211 se produce cuando tiene un compilador para la versión actual, pero un Common Language Runtime de una versión anterior.

Parte de la funcionalidad del compilador podría no funcionar en una versión anterior de runtime.

Para resolver el error C1211, instale el Common Language Runtime que se incluye con el compilador que está usando.

Para obtener más información, consulte [reenvío de tipos (C++ / c++ / CLI)](../../windows/type-forwarding-cpp-cli.md).