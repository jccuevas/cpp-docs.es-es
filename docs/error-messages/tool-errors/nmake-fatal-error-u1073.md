---
title: Error grave de NMAKE U1073
ms.date: 11/04/2016
f1_keywords:
- U1073
helpviewer_keywords:
- U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
ms.openlocfilehash: 97d44594540d18bf008757506a9e36e6d16d2cd7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182700"
---
# <a name="nmake-fatal-error-u1073"></a>Error grave de NMAKE U1073

no se sabe cómo hacer ' TargetName '

El destino especificado no existe y no hay ningún comando que ejecutar o regla de inferencia para aplicar.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Para corregir mediante las siguientes posibles soluciones

1. Compruebe la ortografía del nombre de destino.

1. Si *targetName* es un pseudodestino, especifíquelo como destino en otro bloque de descripción.

1. Si *targetName* es una invocación de macro, asegúrese de que no se expande a una cadena nula.
