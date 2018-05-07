---
title: PG0165 de Error de optimización guiada por perfiles | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PG0165
dev_langs:
- C++
helpviewer_keywords:
- PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: acad97411480112d06dadd454d1368dcfdf2c87f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="profile-guided-optimization-error-pg0165"></a>Error de la optimización guiada por perfiles PG0165
Leer 'Filename.pgd': ' no se admite la versión PGD (error de coincidencia de versión)'.  
  
 Los archivos PGD son específicos de un conjunto de herramientas del compilador determinado. Este error se genera cuando se usa un compilador diferente a la utilizada para *Filename*pgd. Este error indica que este conjunto de herramientas del compilador no puede usar los datos de *Filename*.pgd para optimizar el programa actual.  
  
 Para resolver este problema, vuelva a generar *Filename*.pgd mediante el conjunto de herramientas de compilador actual.