---
title: VCPROFILE_PATH | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VCPROFILE_PATH
dev_langs: C++
helpviewer_keywords: VCPROFILE_PATH environment variable
ms.assetid: 25217aa4-7e86-4eba-854d-10b3c457e4df
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d5b4a2bbb46e906883f3f0c99c84d3b12cc0f104
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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