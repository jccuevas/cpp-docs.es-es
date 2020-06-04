---
title: Advertencia del compilador (nivel 1) C4952
ms.date: 08/27/2018
f1_keywords:
- C4952
helpviewer_keywords:
- C4952
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
ms.openlocfilehash: 560705edeb0bbdd6be760736a8d4a19d914133d2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174575"
---
# <a name="compiler-warning-level-1-c4952"></a>Advertencia del compilador (nivel 1) C4952

> '*función*': no se encontraron datos de perfil en la base de datos de programa '*pgd_file*'

Al usar [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), el compilador detectó un módulo de entrada que se ha vuelto a compilar después `/LTCG:PGINSTRUMENT` y que tiene presente una nueva función (*function*).

Esta advertencia es informativa. Para resolver esta advertencia, ejecute `/LTCG:PGINSTRUMENT`, rehaga todas las pruebas y ejecute `/LTCG:PGOPTIMIZE`.

Esta advertencia se reemplazaría por un error si se hubiera usado `/LTCG:PGOPTIMIZE` .
