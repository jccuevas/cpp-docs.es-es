---
title: Error irrecuperable C1305 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1305
dev_langs:
- C++
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: cf4a9025b8d441ae42b7de7605594fda60dc5603
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="fatal-error-c1305"></a>Error irrecuperable C1305
la base de datos del perfil 'archivo_pgd' es para una arquitectura diferente  
  
 Un archivo .pgd generado a partir de la operación/LTCG: PGINSTRUMENT de otra plataforma se pasó a [/LTCG: PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md) . [Las optimizaciones guiadas por perfil](../../build/reference/profile-guided-optimizations.md) están disponibles para x86 y [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] plataformas. Sin embargo, un archivo .pgd generado con una operación /LTCG:PGINSTRUMENT de una plataforma no es válido como entrada para una operación /LTCG:PGOPTIMIZE de otra plataforma.  
  
 Para resolver este error, pase únicamente un archivo .pgd creado mediante las operaciones /LTCG:PGINSTRUMENT a /LTCG:PGOPTIMIZE de la misma plataforma.
