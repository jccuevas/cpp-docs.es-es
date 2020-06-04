---
title: Error irrecuperable C1126
ms.date: 11/04/2016
f1_keywords:
- C1126
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
ms.openlocfilehash: a6c9d06cd087eb4462ae475cc1f6d64ba451887f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203666"
---
# <a name="fatal-error-c1126"></a>Error irrecuperable C1126

' Identifier ': la asignación automática supera el tamaño

El espacio asignado para las variables locales de una función (más una cantidad limitada de espacio que usa el compilador, como un 20 bytes adicionales para las funciones intercambiables) supera el límite.

Para corregir este error, use `malloc` o `new` para asignar grandes cantidades de datos.
