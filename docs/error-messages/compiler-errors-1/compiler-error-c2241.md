---
title: Error del compilador C2241
ms.date: 11/04/2016
f1_keywords:
- C2241
helpviewer_keywords:
- C2241
ms.assetid: 2f4e2c2c-b95c-4afe-bbe0-4214cd39d140
ms.openlocfilehash: 88f25931d84fe3884ebecbc97b9ddd73390bacc2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618897"
---
# <a name="compiler-error-c2241"></a>Error del compilador C2241

'identificador': el acceso a miembros está restringido

El código intenta acceder a un miembro privado o protegido.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo

1. Cambie el nivel de acceso del miembro.

1. Declare el miembro como `friend` de la función de acceso.