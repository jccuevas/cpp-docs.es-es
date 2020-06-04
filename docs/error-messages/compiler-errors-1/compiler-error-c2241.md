---
title: Error del compilador C2241
ms.date: 11/04/2016
f1_keywords:
- C2241
helpviewer_keywords:
- C2241
ms.assetid: 2f4e2c2c-b95c-4afe-bbe0-4214cd39d140
ms.openlocfilehash: 4d09af5b29318e1481c666fcfe56b3f80434d4a0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206526"
---
# <a name="compiler-error-c2241"></a>Error del compilador C2241

'identificador': el acceso a miembros está restringido

El código intenta acceder a un miembro privado o protegido.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Para corregir mediante las siguientes posibles soluciones

1. Cambie el nivel de acceso del miembro.

1. Declare el miembro como `friend` de la función de acceso.
