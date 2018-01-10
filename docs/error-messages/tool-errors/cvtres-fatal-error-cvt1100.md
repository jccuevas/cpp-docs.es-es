---
title: Error irrecuperable de CVTRES CVT1100 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CVT1100
dev_langs: C++
helpviewer_keywords: CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 906e03b778276196d36a04e6b9e2f02a2d5944bc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cvtres-fatal-error-cvt1100"></a>Error irrecuperable de CVTRES CVT1100
recurso duplicado:: tipo, nombre: nombre,: de idioma, marcas: marcas, tamaño: tamaño  
  
 El recurso dado se especificó más de una vez.  
  
 Este error puede aparecer si el vinculador crea una biblioteca de tipos y no se especificó [/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md) y un recurso en el proyecto ya usa 1. En este caso, especifique /TLBID y otro número hasta 65535.