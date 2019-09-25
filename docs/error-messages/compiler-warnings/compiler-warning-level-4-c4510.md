---
title: Advertencia del compilador (nivel 4) C4510
description: ADVERTENCIA del compilador C4510 Descripción y solución.
ms.date: 09/22/2019
f1_keywords:
- C4510
helpviewer_keywords:
- C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
ms.openlocfilehash: 05a6d0fe42d8247d3328506d8772b2fa77b5703c
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230383"
---
# <a name="compiler-warning-level-4-c4510"></a>Advertencia del compilador (nivel 4) C4510

> '*Class*': no se pudo generar el constructor predeterminado

El compilador no puede generar un constructor predeterminado para la clase especificada, que no tiene ningún constructor definido por el usuario. No se pueden crear objetos de este tipo.

Hay varias situaciones que impiden que el compilador genere un constructor predeterminado, entre los que se incluyen:

- Un miembro de datos **const** .

- Un miembro de datos que es una referencia.

Para corregir este problema, cree un constructor predeterminado definido por el usuario para la clase que inicializa estos miembros.
