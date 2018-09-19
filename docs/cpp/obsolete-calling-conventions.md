---
title: Convenciones de llamada obsoletas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __fortran
- __pascal
- __syscall
dev_langs:
- C++
helpviewer_keywords:
- WINAPI [C++]
- __syscall keyword [C++]
- __pascal keyword [C++]
- __fortran keyword [C++]
- calling conventions, obsolete
ms.assetid: a91fc665-034a-48ce-b6bd-d27125f308a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eec6f8370103ed0256471c009d6e97cc693a1cd7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071346"
---
# <a name="obsolete-calling-conventions"></a>Convenciones de llamada obsoletas

## <a name="microsoft-specific"></a>Específicos de Microsoft

El **__pascal**, **__fortran**, y **__syscall** ya no se admiten las convenciones de llamada. Puede emular su funcionalidad mediante una de las convenciones de llamada admitidas y las opciones del vinculador adecuadas.

\<Windows.h > ahora es compatible con la macro WINAPI, que se traduce en la convención de llamada adecuada para el destino. Usar WINAPI donde antes utilizaba PASCAL o **__far \__pascal**.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Paso de argumentos y convenciones de nomenclatura](../cpp/argument-passing-and-naming-conventions.md)