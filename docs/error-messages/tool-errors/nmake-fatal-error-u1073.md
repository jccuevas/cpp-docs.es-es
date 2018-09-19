---
title: Error grave de NMAKE U1073 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1073
dev_langs:
- C++
helpviewer_keywords:
- U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c309ed94cd1c984406e0d21f0139e35c6e41d7d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053950"
---
# <a name="nmake-fatal-error-u1073"></a>Error grave de NMAKE U1073

no sabe cómo hacer 'nombrededestino'

El destino especificado no existe y no hay ningún comando para ejecutar o reglas de inferencia se aplican.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo

1. Compruebe la ortografía del nombre de destino.

1. Si *targetname* es un pseudodestino, especifíquelo como un destino en otro bloque de descripción.

1. Si *targetname* es una llamada de macro, asegúrese de que no se expande a una cadena nula.