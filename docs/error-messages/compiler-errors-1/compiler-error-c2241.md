---
title: Error del compilador C2241
ms.date: 11/04/2016
f1_keywords:
- C2241
helpviewer_keywords:
- C2241
ms.assetid: 2f4e2c2c-b95c-4afe-bbe0-4214cd39d140
ms.openlocfilehash: 88f25931d84fe3884ebecbc97b9ddd73390bacc2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388974"
---
# <a name="compiler-error-c2241"></a>Error del compilador C2241

'identificador': el acceso a miembros está restringido

El código intenta acceder a un miembro privado o protegido.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo

1. Cambie el nivel de acceso del miembro.

1. Declare el miembro como `friend` de la función de acceso.