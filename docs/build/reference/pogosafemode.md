---
title: PogoSafeMode | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: PogoSafeMode
ms.assetid: 2daeeff7-44cb-417f-90eb-6b9edf658533
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1ce0f4fe011c730a3264cea65b7ab5d10dbcd7ad
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="pogosafemode"></a>PogoSafeMode
Especifique si desea usar el modo rápido o modo seguro para la generación de perfiles de aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
PogoSafeMode  
```  
  
## <a name="remarks"></a>Comentarios  
 Optimización guiada por perfiles (PGO) tiene dos modos posibles durante la fase de generación de perfiles: modo rápido y modo seguro. Cuando la generación de perfiles está en modo rápido, utiliza el **INC** instrucción para aumentar los contadores de datos. El **INC** instrucción es más rápida pero no es seguro para subprocesos. Cuando la generación de perfiles está en modo seguro, usa el **LOCK INC** instrucción para aumentar los contadores de datos. El **LOCK INC** instrucción tiene la misma funcionalidad que la **INC** instrucción tiene y es segura para subprocesos, pero es más lenta que la **INC** instrucción.  
  
 De forma predeterminada, la generación de perfiles PGO funciona en modo rápido. `PogoSafeMode`es necesario sólo si desea usar el modo seguro.  
  
 Para ejecutar la generación de perfiles PGO en modo seguro, se debe usar la variable de entorno `PogoSafeMode` o el modificador de vinculador **- PogoSafeMode**, según el sistema. Si va a realizar la generación de perfiles en un x64 equipo, debe usar el modificador del vinculador. Si va a realizar la generación de perfiles en un x86 equipo, debe definir la variable de entorno para cualquier valor antes de empezar el proceso de optimización.  
  
## <a name="example"></a>Ejemplo  
  
```  
set PogoSafeMode=1  
```  
  
## <a name="see-also"></a>Vea también  
 [Variables de entorno para las optimizaciones guiadas por perfil](../../build/reference/environment-variables-for-profile-guided-optimizations.md)   
 [Optimizaciones guiadas por perfiles](../../build/reference/profile-guided-optimizations.md)