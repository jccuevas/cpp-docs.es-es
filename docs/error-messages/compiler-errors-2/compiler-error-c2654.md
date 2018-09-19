---
title: Error del compilador C2654 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2654
dev_langs:
- C++
helpviewer_keywords:
- C2654
ms.assetid: ca7de1bd-576b-40bf-96fc-a91984827d20
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1181cbab40739617343f8d2a2e5e26540f01e82f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080849"
---
# <a name="compiler-error-c2654"></a>Error del compilador C2654

'identifier': intento de acceso a un miembro fuera de una función miembro

Se tiene acceso a un miembro en una declaración. Los datos de miembros pueden tener acceso solo en las funciones miembro.

Este error puede deberse al intentar inicializar las variables en una declaración. Utilice un constructor para este propósito.