---
title: Error irrecuperable de CVTRES CVT1100
ms.date: 11/04/2016
f1_keywords:
- CVT1100
helpviewer_keywords:
- CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
ms.openlocfilehash: b7e67df24d41b1e8826673146fcc27fd93d143fd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196552"
---
# <a name="cvtres-fatal-error-cvt1100"></a>Error irrecuperable de CVTRES CVT1100

recurso duplicado: tipo: tipo, nombre: nombre, idioma: idioma, marcas: marcas, tamaño: tamaño

El recurso especificado se especificó más de una vez.

Puede obtener este error si el enlazador está creando una biblioteca de tipos y no especificó [/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md) y un recurso del proyecto ya utiliza 1. En este caso, especifique/TLBID y especifique otro número hasta 65535.
