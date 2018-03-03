---
title: VCPROFILE_ALLOC_SCALE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VCPROFILE_ALLOC_SCALE
dev_langs:
- C++
helpviewer_keywords:
- VCPROFILE_ALLOC_SCALE environment variable
ms.assetid: 5cb5ce27-f9b8-489b-b46c-d6e9bcab2d34
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b7b441f41106544633bd691c409fa04c989146f0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="vcprofileallocscale"></a>VCPROFILE_ALLOC_SCALE
Modificar la cantidad de memoria asignada para almacenar los datos de perfil.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
VCPROFILE_ALLOC_SCALE=scale_value  
```  
  
#### <a name="parameters"></a>Parámetros  
 `scale_value`  
 El valor de escala para la cantidad de memoria deseada para ejecutar los escenarios de prueba.  El valor predeterminado es 1.  
  
## <a name="remarks"></a>Comentarios  
 En raras ocasiones, no habrá suficiente memoria disponible para admitir la recopilación de datos de perfil al ejecutar escenarios de prueba.  En esos casos, puede aumentar la cantidad de memoria con `VCPROFILE_ALLOC_SCALE`.  
  
 Si recibe un mensaje de error durante una ejecución de pruebas que indica que dispone de suficiente memoria, asignar un valor mayor para `VCPROFILE_ALLOC_SCALE`, hasta que la prueba se ejecuta completa sin errores de memoria insuficiente.  
  
## <a name="example"></a>Ejemplo  
  
```  
set VCPROFILE_ALLOC_SCALE=2  
```  
  
## <a name="see-also"></a>Vea también  
 [Variables de entorno para las optimizaciones guiadas por perfiles](../../build/reference/environment-variables-for-profile-guided-optimizations.md)