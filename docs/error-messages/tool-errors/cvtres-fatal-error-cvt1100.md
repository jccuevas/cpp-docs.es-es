---
title: Error irrecuperable de CVTRES CVT1100 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CVT1100
dev_langs:
- C++
helpviewer_keywords:
- CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18a5508301c54637fb34a751c8f1c4e307e47d50
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068967"
---
# <a name="cvtres-fatal-error-cvt1100"></a>Error irrecuperable de CVTRES CVT1100

recurso duplicado: tipo: tipo, nombre: nombre, lenguaje: language, marcas: marcas, tamaño: tamaño

Se especificó más de una vez el recurso especificado.

Este error puede aparecer si el vinculador crea una biblioteca de tipos y no especificó [/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md) y un recurso en el proyecto ya usa 1. En este caso, especifique /TLBID y otro número hasta 65535.