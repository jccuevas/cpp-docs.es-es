---
title: Error del compilador C2212
ms.date: 11/04/2016
f1_keywords:
- C2212
helpviewer_keywords:
- C2212
ms.assetid: 3fdab304-272c-4d07-bfd4-fad75170e536
ms.openlocfilehash: bf478c96e76a4fe139caee79f497a0abe7f70824
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206690"
---
# <a name="compiler-error-c2212"></a>Error del compilador C2212

' Identifier ': __based no está disponible para punteros a funciones

Los punteros a funciones no se pueden declarar `__based`. Si necesita datos basados en código, use la palabra clave `__declspec` o el pragma `data_seg`.
