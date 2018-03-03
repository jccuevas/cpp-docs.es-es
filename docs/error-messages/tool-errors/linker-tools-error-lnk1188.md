---
title: Las herramientas del vinculador LNK1188 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1188
dev_langs:
- C++
helpviewer_keywords:
- LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 81d2988742eb9e8cd6aef134510ac8272d3dd27c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1188"></a>Error de las herramientas del vinculador LNK1188
BADFIXUPSECTION:: destino de la corrección no válido 'símbolo'; posible sección de longitud cero  
  
 Durante una vinculación de VxD, el destino de una reubicación no tenía una sección. Con LINK386 (una versión anterior), un registro OMF GROUP (generado por una directiva de grupo de MASM) puede haberse usado para combinar la sección de longitud cero con otra sección de longitud distinta de cero. El formato COFF no es compatible con la directiva de grupo y secciones de longitud cero. Cuando LINK convierte automáticamente este tipo de objetos OMF a COFF, puede producirse este error.