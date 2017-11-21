---
title: -MANIFESTINPUT (especificar entrada de manifiestos) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a32eb8c65e14684b818341121714ce0359f6521a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT (Especificar entrada de manifiestos)
Especifica un archivo de entrada de manifiesto debe incluir en el manifiesto que se incrusta en la imagen.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/MANIFESTINPUT:filename  
```  
  
#### <a name="parameters"></a>Parámetros  
 `filename`  
 El archivo de manifiesto debe incluir en el manifiesto incrustado.  
  
## <a name="remarks"></a>Comentarios  
 El **/MANIFESTINPUT** opción especifica la ruta de acceso de un archivo de entrada se usa para crear el manifiesto incrustado en una imagen ejecutable. Si tiene un manifiesto varios archivos de entrada, utilice el modificador varias veces: una vez para cada archivo de entrada. Los archivos de entrada de manifiesto se combinan para crear el manifiesto incrustado. Esta opción requiere el **/MANIFEST: EMBED** opción.  
  
 Esta opción no se puede establecer directamente en [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)]. En su lugar, use la **archivos de manifiesto adicionales** propiedad del proyecto para especificar los archivos de manifiesto adicionales que se incluirán. Para obtener más información, consulte [entrada y salida, herramienta manifiesto, propiedades de configuración, \<NombreDeProyecto > cuadro de diálogo páginas de propiedades](../../ide/input-and-output-manifest-tool.md).  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)