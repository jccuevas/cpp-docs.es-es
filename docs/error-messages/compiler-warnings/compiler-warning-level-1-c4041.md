---
title: Advertencia del compilador (nivel 1) C4041
ms.date: 11/04/2016
f1_keywords:
- C4041
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
ms.openlocfilehash: 14ea6d9cae3b490107b656153bb68815026971e1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164240"
---
# <a name="compiler-warning-level-1-c4041"></a>Advertencia del compilador (nivel 1) C4041

límite del compilador : se va a finalizar el resultado del explorador

La información del explorador supera el límite del compilador.

Esta advertencia puede deberse a la compilación con [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) (información del explorador con variables locales).

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Para corregir mediante las siguientes posibles soluciones

1. Compile con /Fr (información del explorador sin variables locales).

1. Deshabilite el resultado del explorador (compile sin /FR o /Fr).
