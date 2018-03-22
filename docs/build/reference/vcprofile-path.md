---
title: VCPROFILE_PATH | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VCPROFILE_PATH
dev_langs:
- C++
helpviewer_keywords:
- VCPROFILE_PATH environment variable
ms.assetid: 25217aa4-7e86-4eba-854d-10b3c457e4df
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ea682b70f4417ef49bfca530af5f12f21699a389
ms.sourcegitcommit: 5cd2e3e51ecc8d9fc0d889555b4bfa193ba1d6a5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2018
---
# <a name="vcprofilepath"></a>VCPROFILE_PATH
Especifique el directorio para crear archivos .pgc.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
VCPROFILE_PATH=path  
```  
  
#### <a name="parameters"></a>Parámetros  
 `path`  
 La ruta de acceso de directorio en qué .pgc se agregarán los archivos.  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, los archivos .pgc se crean en el mismo directorio que el archivo binario que se va a perfilar.  Sin embargo, si no existe la ruta de acceso absoluta del archivo binario, como puede ser el caso cuando se ejecutan escenarios de perfiles en un equipo diferente de donde se creó el archivo binario, puede establecer `VCPROFILE_PATH` a una ruta de acceso existe.  
  
## <a name="example"></a>Ejemplo  
  
```  
set VCPROFILE_PATH=c:\  
```  
  
## <a name="see-also"></a>Vea también  
 [Variables de entorno para las optimizaciones guiadas por perfiles](../../build/reference/environment-variables-for-profile-guided-optimizations.md)