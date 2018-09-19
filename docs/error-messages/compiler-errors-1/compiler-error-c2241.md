---
title: Error del compilador C2241 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2241
dev_langs:
- C++
helpviewer_keywords:
- C2241
ms.assetid: 2f4e2c2c-b95c-4afe-bbe0-4214cd39d140
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd97551e0feaecce776cc552353716c67822f273
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055902"
---
# <a name="compiler-error-c2241"></a>Error del compilador C2241

'identificador': el acceso a miembros está restringido

El código intenta acceder a un miembro privado o protegido.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo

1. Cambie el nivel de acceso del miembro.

1. Declare el miembro como `friend` de la función de acceso.