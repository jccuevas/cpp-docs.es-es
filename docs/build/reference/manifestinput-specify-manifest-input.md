---
title: -MANIFESTINPUT (especificar entrada de manifiestos) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d1b5ed266f1b8929deee3ffb60a10b18b7604afc
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572295"
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
 El **/MANIFESTINPUT** opción especifica la ruta de acceso de archivo de entrada se usa para crear el manifiesto incrustado en una imagen ejecutable. Si tiene un manifiesto varios archivos de entrada, utilice el modificador varias veces: una vez para cada archivo de entrada. Los archivos de entrada de manifiesto se combinan para crear el manifiesto incrustado. Esta opción requiere el **/MANIFEST: EMBED** opción.  
  
 Esta opción no se puede establecer directamente en Visual Studio. En su lugar, use el **archivos de manifiesto adicionales** propiedad del proyecto para especificar los archivos de manifiesto adicionales para incluir. Para obtener más información, consulte [entrada y salida, herramienta manifiesto, propiedades de configuración, \<NombreDelProyecto > cuadro de diálogo páginas de propiedades](../../ide/input-and-output-manifest-tool.md).  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)