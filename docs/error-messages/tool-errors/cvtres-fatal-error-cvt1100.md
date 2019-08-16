---
title: Error irrecuperable de CVTRES CVT1100
ms.date: 11/04/2016
f1_keywords:
- CVT1100
helpviewer_keywords:
- CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
ms.openlocfilehash: c7e65ccc79852ec99dd2406398fe1b3cdecacde7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406280"
---
# <a name="cvtres-fatal-error-cvt1100"></a>Error irrecuperable de CVTRES CVT1100

recurso duplicado: tipo: tipo, nombre: nombre, lenguaje: language, marcas: marcas, tamaño: tamaño

Se especificó más de una vez el recurso especificado.

Este error puede aparecer si el vinculador crea una biblioteca de tipos y no especificó [/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md) y un recurso en el proyecto ya usa 1. En este caso, especifique /TLBID y otro número hasta 65535.