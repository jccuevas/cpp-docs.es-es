---
title: Error irrecuperable de CVTRES CVT1100 | Documentos de Microsoft
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
ms.openlocfilehash: 32085c4c37c82567eb78f46b52bcc4a6c41daae5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cvtres-fatal-error-cvt1100"></a>Error irrecuperable de CVTRES CVT1100
recurso duplicado:: tipo, nombre: nombre,: de idioma, marcas: marcas, tamaño: tamaño  
  
 El recurso dado se especificó más de una vez.  
  
 Este error puede aparecer si el vinculador crea una biblioteca de tipos y no se especificó [/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md) y un recurso en el proyecto ya usa 1. En este caso, especifique /TLBID y otro número hasta 65535.