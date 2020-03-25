---
title: Error irrecuperable C1091
ms.date: 11/04/2016
f1_keywords:
- C1091
helpviewer_keywords:
- C1091
ms.assetid: 812d4201-9154-48b0-b9af-5959c082ca33
ms.openlocfilehash: 76492be7abab6deb740f1670b85274b8c296c783
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203898"
---
# <a name="fatal-error-c1091"></a>Error irrecuperable C1091

límite del compilador: la longitud de la cadena supera los bytes de 'length'.

Una constante de cadena supera el límite actual de la longitud de las cadenas.

Puede dividir la cadena estática en dos (o más) variables y usar [strcpy_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) para unir el resultado como parte de la declaración o durante el tiempo de ejecución.
